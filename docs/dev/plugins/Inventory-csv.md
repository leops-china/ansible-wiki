## 需求

使用`csv`文件作为动态主机源，为ansible提供动态主机支持

csv文件内容如下:

```csv
Hostname,IP,Location,Type,OS
i_nginx01,10.1.1.1,IDC,Gateway,Ubuntu
i_web01,10.1.1.2,IDC,Service,Centos
i_web02,10.1.1.3,IDC,Service,Centos
a_nginx01,10.2.1.1,Aliyun,Gateway,Ubuntu
a_web01,10.2.1.2,Aliyun,Service,Centos
a_web02,10.2.1.3,Aliyun,Service,Centos
```

## 编写插件

编写自定义清单插件分为两部分：

- 一个YAML文件，其中描述了使用哪个插件，以及插件的参数
    ```yaml
    # csv_inventory.yaml
    ---
    plugin: my_csv_plugin            # 插件名称
    path_to_inventory: csv_inventory # csv文件目录
    csv_file: myinventory.csv        # csv文件名称
    ```
- Python插件文件，ansible要求插件必须使用python语言编写

    ```python
    #my_csv_plugin.py

    from __future__ import (absolute_import, division, print_function)
    __metaclass__ = type

    DOCUMENTATION = r'''
        name: my_csv_plugin
        plugin_type: inventory
        short_description: Returns Ansible inventory from CSV
        description: Returns Ansible inventory from CSV
        options:
          plugin:
              description: Name of the plugin
              required: true
              choices: ['my_csv_plugin']
          path_to_inventory:
            description: Directory location of the CSV inventory
            required: true
          csv_file:
            description: File name of the CSV inventory file
            required: true
    '''
    
    from ansible.plugins.inventory import BaseInventoryPlugin
    from ansible.errors import AnsibleError, AnsibleParserError

    class InventoryModule(BaseInventoryPlugin):
        NAME = 'my_csv_plugin'

        def verify_file(self, path):
            '''验证yaml文件名称，只有符合的文件才会被解析'''
            pass
    
        def parse(self, inventory, loader, path, cache):
           '''从数据源返回动态主机信息 '''
           pass
    ```
    
    注意事项
    
    - `DOCUMENTATION `是插件的必须部分，其中描述了插件的信息和选项，这里的选项跟`csv_inventory.yaml` 文件中的选项是一致的。
    - 插件的名称`NAME ` 要与脚本文件的名称(去除`.py`后缀)一致

### 实现`verify_file`方法

在这个方法中，验证`YAML`文件名称的合法性,也就是只有指定的YAML文件名称才能被插件解析

```bash
# Update the verify_file method

    def verify_file(self, path):
        '''Return true/false if this is a 
        valid file for this plugin to consume
        '''
        valid = False
        if super(InventoryModule, self).verify_file(path):
            #base class verifies that file exists 
            #and is readable by current user
            if path.endswith(('csv_inventory.yaml',
                              'csv_inventory.yml')):
                valid = True
        return valid
        
```

### 实现`parse`方法

在这个方法中，我们要解析`YAML`文件中的选项，根据选项获取动态主机源数据，然后解析成固定的结构体返回

1. 解析yaml文件

    ```python
       def parse(self, inventory, loader, path, cache):
          '''Return dynamic inventory from source '''
          super(InventoryModule, self).parse(inventory, loader, path, cache)
          # Read the inventory YAML file
          self._read_config_data(path)
          try:
              # Store the options from the YAML file
              self.plugin = self.get_option('plugin')
              self.inv_dir = self.get_option('path_to_inventory')
              self.inv_file = self.get_option('csv_file')
          except Exception as e:
              raise AnsibleParserError(
                  'All correct options required: {}'.format(e))
          # Call our internal helper to populate the dynamic inventory
          self._populate()
    ```

2. 使用`self._populate()` 构建动态主机

    将csv文件转为json结构体

    ```python
    def _get_structured_inventory(self, inventory_file):
    
        #Initialize a dict
        inventory_data = {}
        #Read the CSV and add it to the dictionary
        try:
            with open(inventory_file, 'r') as fh:
                csvdict = csv.DictReader(fh)
                for rows in csvdict:
                    hostname = rows['Hostname']
                    inventory_data[hostname] = rows
        except Exception as e:
           raise AnsibleParserError(
              'Parsing file error: {}'.format(e))
        return inventory_data

    def _populate(self):
        '''Return the hosts and groups'''
        self.inventory_file = self.inv_dir + '/' + self.inv_file
        self.myinventory = self._get_structured_inventory(self.inventory_file)
    ```

3. 添加主机组

    继续在` _populate(self)`函数中操作，这里我们增加了3个类别的主机组

    ```python
    def _populate(self):
        '''Return the hosts and groups'''
        self.inventory_file = self.inv_dir + '/' + self.inv_file
        self.myinventory = self._get_structured_inventory(self.inventory_file)
        #Create the location, type and os groups
        locations = []
        types = []
        oss = []
        for data in self.myinventory.values():
            if not data['Location'] in locations:
                locations.append(data['Location'])
            if not data['Type'] in types:
                types.append(data['Type'])
            if not data['OS'] in oss:
                oss.append(data['OS'])
        for location in locations:
            self.inventory.add_group(location)
        for type in types:
            self.inventory.add_group(type)
        for os in oss:
            self.inventory.add_group(os)
        #Add the hosts to the groups
        for hostname,data in self.myinventory.items():
            self.inventory.add_host(host=hostname, group=data['Location'])
            self.inventory.add_host(host=hostname, group=data['Type'])
            self.inventory.add_host(host=hostname, group=data['OS'])
    ```

4. 添加主机变量

    ```python hl_lines="27 28"
    def _populate(self):
        '''Return the hosts and groups'''
        self.inventory_file = self.inv_dir + '/' + self.inv_file
        self.myinventory = self._get_structured_inventory(self.inventory_file)
        #Create the location, type and os groups
        locations = []
        types = []
        oss = []
        for data in self.myinventory.values():
            if not data['Location'] in locations:
                locations.append(data['Location'])
            if not data['Type'] in types:
                types.append(data['Type'])
            if not data['OS'] in oss:
                oss.append(data['OS'])
        for location in locations:
            self.inventory.add_group(location)
        for type in types:
            self.inventory.add_group(type)
        for os in oss:
            self.inventory.add_group(os)
        #Add the hosts to the groups
        for hostname,data in self.myinventory.items():
            self.inventory.add_host(host=hostname, group=data['Location'])
            self.inventory.add_host(host=hostname, group=data['Type'])
            self.inventory.add_host(host=hostname, group=data['OS'])
            self.inventory.set_variable(hostname, 'ansible_host', data['IP'])
            self.inventory.set_variable(hostname, 'ansible_os', data['OS'])
    ```

### 脚本示例

```python
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

DOCUMENTATION = r'''
    name: my_csv_plugin
    plugin_type: inventory
    short_description: Returns Ansible inventory from CSV
    description: Returns Ansible inventory from CSV
    options:
      plugin:
          description: Name of the plugin
          required: true
          choices: ['my_csv_plugin']
      path_to_inventory:
        description: Directory location of the CSV inventory
        required: true
      csv_file:
        description: File name of the CSV inventory file
        required: true
'''



from ansible.plugins.inventory import BaseInventoryPlugin
from ansible.errors import AnsibleError, AnsibleParserError
import csv


class InventoryModule(BaseInventoryPlugin):
    NAME = 'my_csv_plugin'


    def verify_file(self, path):
        '''Return true/false if this is possibly a valid file for this plugin to
consume
        '''
        valid = False
        if super(InventoryModule, self).verify_file(path):
            # base class verifies that file exists and is readable by current
            # user
            if path.endswith(('csv_inventory.yaml',
                              'csv_inventory.yml')):
                valid = True
        return valid

    def _get_structured_inventory(self, inventory_file):
    
        #Initialize a dict
        inventory_data = {}
        #Read the CSV and add it to the dictionary
        try:
            with open(inventory_file, 'r') as fh:
                csvdict = csv.DictReader(fh)
                for rows in csvdict:
                    hostname = rows['Hostname']
                    inventory_data[hostname] = rows
        except Exception as e:
           raise AnsibleParserError(
              'Parsing file error: {}'.format(e))
        return inventory_data

    def _populate(self):
        '''Return the hosts and groups'''
        self.inventory_file = self.inv_dir + '/' + self.inv_file
        self.myinventory = self._get_structured_inventory(self.inventory_file)
        #Create the location, type and os groups
        locations = []
        types = []
        oss = []
        for data in self.myinventory.values():
            if not data['Location'] in locations:
                locations.append(data['Location'])
            if not data['Type'] in types:
                types.append(data['Type'])
            if not data['OS'] in oss:
                oss.append(data['OS'])
        for location in locations:
            self.inventory.add_group(location)
        for type in types:
            self.inventory.add_group(type)
        for os in oss:
            self.inventory.add_group(os)
        #Add the hosts to the groups
        for hostname,data in self.myinventory.items():
            self.inventory.add_host(host=hostname, group=data['Location'])
            self.inventory.add_host(host=hostname, group=data['Type'])
            self.inventory.add_host(host=hostname, group=data['OS'])
            self.inventory.set_variable(hostname, 'ansible_host', data['IP'])
            self.inventory.set_variable(hostname, 'ansible_os', data['OS'])
            
    
    def parse(self, inventory, loader, path, cache):
       '''Return dynamic inventory from source '''
       super(InventoryModule, self).parse(inventory, loader, path, cache)
       # Read the inventory YAML file
       self._read_config_data(path)
       try:
           # Store the options from the YAML file
           self.plugin = self.get_option('plugin')
           self.inv_dir = self.get_option('path_to_inventory')
           self.inv_file = self.get_option('csv_file')
       except Exception as e:
           raise AnsibleParserError(
               'All correct options required: {}'.format(e))
       # Call our internal helper to populate the dynamic inventory
       self._populate()

```

## 配置 ansible.cfg

```ini
[defaults]
inventory_plugins  = /etc/ansible/plugins/inventory # 存储插件的目录

[inventory]
enable_plugins = host_list, script, yaml, ini, toml, my_csv_plugin  # 添加自定义的插件
```

> `host_list, script, yaml, ini, toml` 这些都是ansible默认的插件

当前的目录结构

```bash
# tree .
.
├── ansible.cfg
├── csv_inventory
│   └── myinventory.csv
├── hosts
├── plugins
│   └── inventory
│       └── my_csv_plugin.py
└── csv_inventory.yaml
```

## 查看主机信息

通过`ansible-inventory` 可以查看动态主机的信息

以图表的形式返回主机信息

```bash
# ansible-inventory -i csv_inventory.yaml --graph
@all:
  |--@Aliyun:
  |  |--a_nginx01
  |  |--a_web01
  |  |--a_web02
  |--@Centos:
  |  |--a_web01
  |  |--a_web02
  |  |--i_web01
  |  |--i_web02
  |--@Gateway:
  |  |--a_nginx01
  |  |--i_nginx01
  |--@IDC:
  |  |--i_nginx01
  |  |--i_web01
  |  |--i_web02
  |--@Service:
  |  |--a_web01
  |  |--a_web02
  |  |--i_web01
  |  |--i_web02
  |--@Ubuntu:
  |  |--a_nginx01
  |  |--i_nginx01
  |--@ungrouped:

```
以json结构的形式返回
```bash
# ansible-inventory -i csv_inventory.yaml --list
{
    "Aliyun": {
        "hosts": [
            "a_nginx01", 
            "a_web01", 
            "a_web02"
        ]
    }, 
    "Centos": {
        "hosts": [
            "a_web01", 
            "a_web02", 
            "i_web01", 
            "i_web02"
        ]
    }, 
    "Gateway": {
        "hosts": [
            "a_nginx01", 
            "i_nginx01"
        ]
    }, 
    "IDC": {
        "hosts": [
            "i_nginx01", 
            "i_web01", 
            "i_web02"
        ]
    }, 
    "Service": {
        "hosts": [
            "a_web01", 
            "a_web02", 
            "i_web01", 
            "i_web02"
        ]
    }, 
    "Ubuntu": {
        "hosts": [
            "a_nginx01", 
            "i_nginx01"
        ]
    }, 
    "_meta": {
        "hostvars": {
            "a_nginx01": {
                "ansible_host": "10.2.1.1", 
                "ansible_os": "Ubuntu"
            }, 
            "a_web01": {
                "ansible_host": "10.2.1.2", 
                "ansible_os": "Centos"
            }, 
            "a_web02": {
                "ansible_host": "10.2.1.3", 
                "ansible_os": "Centos"
            }, 
            "i_nginx01": {
                "ansible_host": "10.1.1.1", 
                "ansible_os": "Ubuntu"
            }, 
            "i_web01": {
                "ansible_host": "10.1.1.2", 
                "ansible_os": "Centos"
            }, 
            "i_web02": {
                "ansible_host": "10.1.1.3", 
                "ansible_os": "Centos"
            }
        }
    }, 
    "all": {
        "children": [
            "Aliyun", 
            "Centos", 
            "Gateway", 
            "IDC", 
            "Service", 
            "Ubuntu", 
            "ungrouped"
        ]
    }
}
```

> 返回的数据是不是跟脚本一致。



## 执行 ad-hoc 命令

```bash
# ansible -i csv_inventory.yaml all --list-hosts
  hosts (6):
    i_web01
    i_web02
    a_web01
    a_web02
    i_nginx01
    a_nginx01

# ansible -i csv_inventory.yaml all -m ping
i_web02 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
i_nginx01 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
i_web01 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
a_web02 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
a_web01 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
a_nginx01 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}

```

## 执行 playbook

```bash
cat /etc/ansible/test.yml 
---

- hosts: all
  gather_facts: no
  tasks:
    - name: display var
      debug:
        msg: "The mgmt IP is {{ ansible_host }} and platorm is {{ ansible_os }}"


# ansible-playbook -i csv_inventory.yaml test.yml 

PLAY [all] *****************************************************************************************

TASK [display var] *****************************************************************************************
ok: [i_web01] => {
    "msg": "The mgmt IP is 10.1.1.2 and platorm is Centos"
}
ok: [i_web02] => {
    "msg": "The mgmt IP is 10.1.1.3 and platorm is Centos"
}
ok: [a_web01] => {
    "msg": "The mgmt IP is 10.2.1.2 and platorm is Centos"
}
ok: [a_web02] => {
    "msg": "The mgmt IP is 10.2.1.3 and platorm is Centos"
}
ok: [i_nginx01] => {
    "msg": "The mgmt IP is 10.1.1.1 and platorm is Ubuntu"
}
ok: [a_nginx01] => {
    "msg": "The mgmt IP is 10.2.1.1 and platorm is Ubuntu"
}

PLAY RECAP *****************************************************************************************
a_nginx01                  : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
a_web01                    : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
a_web02                    : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
i_nginx01                  : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
i_web01                    : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
i_web02                    : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```
