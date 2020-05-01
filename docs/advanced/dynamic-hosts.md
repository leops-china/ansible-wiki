ansible 不仅可以从静态文件中获取主机信息，还可以从动态源（包括云主机资源）中获取主机清单。

使用动态主机的时候，我们只需要创建一个脚本或程序，可以在正确的参数输入时已正确的格式打印`json`字符串，就能自定义一个插件。当然，你可以用任何语言实现这个脚本。

!!! note
    目前官方已不推荐使用 **脚本方式** 来动态获取主机信息，推荐使用 **插件方式** 使用动态主机。

## 脚本约定

当我们向脚本输入`--list`参数时，脚本必须将要管理的所有组以json编码的形式输出到标准输出stdout。每个组的值应该是包含每个主机/ip的列表以及定义的变量。下面给出一个简单示例
```json
{
    "databases": {
        "hosts": ["host1.example.com", "host2.example.com"],
        "vars": {
            "a": true
        }
    },
    "webservers": ["host2.example.com", "host3.example.com"],
    "atlanta": {
        "hosts": ["host1.example.com", "host4.example.com", "host5.example.com"],
        "vars": {
            "b": false
        },
        "children": ["marietta", "5points"]
    },
    "marietta": ["host6.example.com"],
    "5points": ["host7.example.com"]
}
```

- `databases` 是主机组名称
- `hosts`  是主机组的主机列表
- `vars`  是主机组的变量
- `children`  是主机组的子组

当我们向脚本输入 `--host <hostname>`参数时，脚本必须输出一个空的json字符串或一个变量的列表/字典，以便temlates和playbook可以使用。输出变量是可选的，如果脚本不希望输出，那输出一个空的列表/字典也是可以的。下面一个简单的示例
```json
{
    "favcolor": "red",
    "ntpserver": "wolf.example.com",
    "monitoring": "pack.example.com"
}
```

定义hostvars的主机变量，下面一个简单的示例
```
{

    # results of inventory script as above go here
    # ...

    "_meta": {
        "hostvars": {
            "moocow.example.com": {
                "asdf": 1234
            },
            "llama.example.com": {
                "asdf": 5678
            }
        }
    }
}
```

- `hostvars` 指的是主机变量
- `moocow.example.com` 主机名称，与主机组内的名称对应
- `"asdf": 1234`  主机变量


总体而言，一个简单的`inventory`数据结构如下

```json
{
    "all": {
        "hosts": ["address"],
        "vars": {},
    },
    "_meta": {
        "hostvars": {
            "address": {
                "variable_name": "value",
            }
        },
    },
    "group_name": ["address"]
}
```

## 简单例子

获取自定义的主机信息

```python
#!/usr/bin/env python

'''
Example custom dynamic inventory script for Ansible, in Python.
'''

import os
import sys
import argparse

try:
    import json
except ImportError:
    import simplejson as json

class ExampleInventory(object):

    def __init__(self):
        self.inventory = {}
        self.read_cli_args()
    
        # Called with `--list`.
        if self.args.list:
            self.inventory = self.example_inventory()
        # Called with `--host [hostname]`.
        elif self.args.host:
            # Not implemented, since we return _meta info `--list`.
            self.inventory = self.empty_inventory()
        # If no groups or vars are present, return empty inventory.
        else:
            self.inventory = self.empty_inventory()
    
        print json.dumps(self.inventory);
    
    # Example inventory for testing.
    def example_inventory(self):
        return {
            'group': {
                'hosts': ['192.168.77.129', '192.168.77.130'],
                'vars': {
                    'ansible_ssh_user': 'root',
                    'ansible_ssh_pass': '123456',
                    'example_variable': 'value'
                }
            },
            '_meta': {
                'hostvars': {
                    '192.168.77.129': {
                        'host_specific_var': 'foo'
                    },
                    '192.168.77.130': {
                        'host_specific_var': 'bar'
                    }
                }
            }
        }
    
    # Empty inventory for testing.
    def empty_inventory(self):
        return {'_meta': {'hostvars': {}}}
    
    # Read the command line args passed to the script.
    def read_cli_args(self):
        parser = argparse.ArgumentParser()
        parser.add_argument('--list', action = 'store_true')
        parser.add_argument('--host', action = 'store')
        self.args = parser.parse_args()

# Get the inventory.
ExampleInventory()
```

本脚本中`example_inventory`中直接返回了一个json结构，大家可以解析各种源数据来构建json结构返回即可。


## 脚本使用

赋予插件可执行权限
```bash
chmod +x test_inventory.py
```

`--list` 数据
```bash
./test_inventory.py --list
{
  "_meta": {
    "hostvars": {
      "192.168.77.130": {
        "host_specific_var": "foo"
      }, 
      "192.168.77.131": {
        "host_specific_var": "bar"
      }
    }
  }, 
  "group": {
    "hosts": [
      "192.168.77.130", 
      "192.168.77.131"
    ], 
    "vars": {
      "ansible_ssh_pass": "123456", 
      "ansible_ssh_user": "root", 
      "example_variable": "value"
    }
  }
}
```
`--host` 数据
```bash
[root@node130 ~]# ./test_inventory.py --host 192.168.77.130
{
  "host_specific_var": "foo"
}
[root@node130 ~]# ./test_inventory.py --host 192.168.77.131
{
  "host_specific_var": "bar"
}

```
### 执行 ad-hoc 命令

在命令中使用 `-i` 选项指定脚本路径即可获取动态主机信息

```bash
ansible all -i test_inventory.py -m ping
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
# ansible-playbook -i test_inventory.py test.yml 

PLAY [all] *****************************************************************************************

TASK [ping] *****************************************************************************************
ok: [192.168.77.131]
ok: [192.168.77.130]

PLAY RECAP *****************************************************************************************
192.168.77.130             : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.77.131             : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```

查看定义的主机变量
```bash
# ansible all -i test_inventory.py -m debug -a "var=host_specific_var"
192.168.77.130 | SUCCESS => {
    "host_specific_var": "foo"
}
192.168.77.131 | SUCCESS => {
    "host_specific_var": "bar"
}

# ansible all -i test_inventory.py -m debug -a "var=example_variable"
192.168.77.130 | SUCCESS => {
    "example_variable": "value"
}
192.168.77.131 | SUCCESS => {
    "example_variable": "value"
}
```

### 执行 playbook

```bash
# cat test_inventory_script.yml 
---
- hosts: all
  gather_facts: no
  tasks:
    - debug: var=host_specific_var
    - debug: var=example_variable

# ansible-playbook -i test_inventory.py test_inventory_script.yml 

PLAY [all] *****************************************************************************************

TASK [debug] *****************************************************************************************
ok: [192.168.77.130] => {
    "host_specific_var": "foo"
}
ok: [192.168.77.131] => {
    "host_specific_var": "bar"
}

TASK [debug] *****************************************************************************************
ok: [192.168.77.130] => {
    "example_variable": "value"
}
ok: [192.168.77.131] => {
    "example_variable": "value"
}

PLAY RECAP *****************************************************************************************
192.168.77.130             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.77.131             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

## 插件使用

你可以使用 inventory  plugin 来获取云主机信息，使用方式见 [ 使用动态主机管理云服务](/advanced/dynamic-inventory/)

你也可以自己开发 inventory  plugin 来从源获取主机方式，详细信息见 [从csv源获取主机信息](/dev/plugins/Inventory-csv)