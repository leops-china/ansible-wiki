# remote_copy 模块

通过这个简单的自定义模块，来了解下ansible的模块是怎么编写的。

## 需求

该模块的目的是在远程主机上将远程源文件复制到远程目标文件

## 创建模块

1. 将这个模块放在 **library** 目录下，命名为`remote_copy.py`
   可以使用` ANSIBLE_LIBRARY`环境变量来指定模块的存放位置。也可以在playbook当前目录下创建library目录。
   
    ```bash
    # mkdir /etc/ansible/library
    # ls
    remote_copy.py
    ```
	
2. 在文件头部加入下列语句，表示该模块使用python运行
    ```pyhton
    #!/usr/bin/python
    # -*- coding: utf-8 -*-
    # Copyright: (c) 2020, lework
    # GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)
    ```
3. 导入我们所需要的库
    ```python
    import os
    import shutil
    from ansible.module_utils.basic import AnsibleModule
    ```

4. 创建模块的入口，并使用AnsibleModule类中的argument_spec来接受参数
    ```python
    def main():
        module_args = dict(
                source=dict(required=True, type='str'),
                dest=dict(required=True, type='str')
        )

        module = AnsibleModule(
            argument_spec=module_args
        )
    )
    ```
	在我们的模块中，我们提供了两个参数，第一个参数是`source`，用来定义源文件;第二个参数是`dest`，用来定义目的地。这两个参数被标记为必须定义的。类型是字符串。

5. 定义模块的返回参数

	```python
    result = dict(
        changed=False,
        source='',
        dest=''
    )
	```
	模块返回的不仅仅是自定义的，还会返回通用的数据，详细见[模块返回值](/dev/modules/module-return/)

6. 使用shutil.copy拷贝文件
	```
        if not os.path.isfile(module.params['source']):
            module.fail_json(msg='The source '+ module.params['source'] +' file was not found', **result)

        try:
            shutil.copy(module.params['source'], module.params['dest'])
        except Exception as e:
            module.fail_json(msg=e, **result)
    ```
	
	!!! tips
		`module.fail_json` 停止执行并返回错误信息。

7. 拷贝完成后，退出执行并返回json数据
	```python
    module.exit_json(**result)
    ```
	此命令将退出模块执行

8. 最后，告诉程序使用main()来执行模块
    ```python
    if __name__ == '__main__':
        main()
    ```
9. 现在我们的模块是可以运行的了。

	**本地执行，测试下模块运行**

	指定模块参数

	```json
	// args.json 
	{
       "ANSIBLE_MODULE_ARGS": {
           "source": "/tmp/a",
           "dest": "/tmp/b"
       }
	}
	
	```
   
	执行模块
   
	```bash
	# python remote_copy.py args.json 
   
	{"source": "", "dest": "", "changed": false, "failed": true, "invocation": {"module_args": {"dest": "/tmp/b", "source": "/tmp/a"}}, "msg": "The source /tmp/a file was not found"}
	```
   
	可以看到msg信息提示source文件不存在，false状态为 **failed** 表明模块执行失败
   
	创建源文件并执行模块
   
	```bash
	# touch /tmp/a
	# python remote_copy.py args.json
	
	{"invocation": {"module_args": {"dest": "/tmp/b", "source": "/tmp/a"}}, "changed": true}
	```
   
	> 模块运行正常
   
	**下面将使用一个playbook来测试我们的remote_copy**
	
	```yaml
	- name: test remote_copy module
	  hosts: node1
	  gather_facts: false

	  tasks:
	    - name: ensure foo
	      file: path=/tmp/foo state=touch
       
	    - name: do a remote copy
	      remote_copy: source=/tmp/foo dest=/tmp/bar
	```
	
	这里我们使用了一个任务，来使源文件一直存在。
	```bash
    # ansible-playbook test_remote_copy.yml 

     PLAY [test remote_copy module] **************************************************************************************

        TASK [ensure foo] **************************************************************************************
     changed: [192.168.77.130]

        TASK [do a remote copy] **************************************************************************************
     changed: [192.168.77.130]

        PLAY RECAP **************************************************************************************
        192.168.77.130             : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0 
	```
   
	使用ansible命令执行模块

	```bash
    # ansible 192.168.77.130 -M /etc/ansible/library/ -m remote_copy -a 'source=/tmp/foo dest=/tmp/bar'
        192.168.77.130 | CHANGED => {
            "ansible_facts": {
                "discovered_interpreter_python": "/usr/bin/python"
            }, 
            "changed": true, 
            "dest": "/tmp/bar", 
            "gid": 0, 
            "group": "root", 
            "mode": "0644", 
            "owner": "root", 
            "size": 0, 
            "source": "/tmp/foo", 
            "state": "file", 
            "uid": 0
    }
	```

	> ansible 命令使用-M来指定模块目录，返回数据中除了我们定义的，还有些ansible定义的数据。

### 提供 fact 数据
---

与作为模块退出的一部分返回的数据类似，模块也可以直接创建fact数据，通过名为ansible_facts键返回数据到主机。无需为任务register一个变量来获取数值。
```python
    remote_facts = {'rc_source': module.params['source'], 'rc_dest': module.params['dest'] }
    result['ansible_facts'] = remote_facts

    module.exit_json(**result)
```
> 注意： module.exit_json 中需带上remote_facts返回

在playbook中添加查看fact的任务

```yaml
- name: show a fact
  debug: var=rc_dest
```
运行playbook查看返回的数据

```bash
ansible-playbook test_remote_copy.yml

PLAY [test remote_copy module] *****************************************************************************************

TASK [ensure foo] *****************************************************************************************
changed: [192.168.77.130]

TASK [do a remote copy] *****************************************************************************************
changed: [192.168.77.130]

TASK [show a fact] *****************************************************************************************
ok: [192.168.77.130] => {
    "rc_dest": "/tmp/bar"
}

PLAY RECAP *****************************************************************************************
192.168.77.130             : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```



### 指定检查模式

模块可以选择支持检查模式<http://docs.ansible.com/ansible/playbooks_checkmode.html>。 如果用户在检查模式下运行可执行安全性，则模块应该尝试预测和报告是否发生更改，但实际上不会进行任何更改（不支持检查模式的模块也不会采取任何动作，但只是不会报告其可能的更改）。

对于您的模块支持检查模式，您必须在实例化AnsibleModule对象时传递`supports_check_mode = True`。 当启用检查模式时，AnsibleModule.check_mode属性将计算为True。 例如：
```python
    module = AnsibleModule(
        argument_spec=module_args,
        supports_check_mode=True
    )

    if module.check_mode:
       module.exit_json(**result)
```
在进行检查模式的时候，不执行拷贝动作，看下列运行状态。

```bash
# ansible-playbook test_remote_copy.yml -C

PLAY [test remote_copy module] *****************************************************************************************

TASK [ensure foo] *****************************************************************************************
ok: [192.168.77.130]

TASK [do a remote copy] *****************************************************************************************
ok: [192.168.77.130]

TASK [show a fact] *****************************************************************************************
ok: [192.168.77.130] => {
    "rc_dest": "/tmp/bar"
}

PLAY RECAP *****************************************************************************************
192.168.77.130             : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

# ansible 192.168.77.130 -m shell -a 'ls /tmp/bar'
192.168.77.130 | FAILED | rc=2 >>
ls: 无法访问/tmp/bar: 没有那个文件或目录non-zero return code
```

可以看到，再检查模式下，模块没有执行拷贝操作。

### 定义帮助信息

单单是代码运行还不够，我们还需要为模块添加一些说明信息，以助于其他人使用模块。

#### 定义ANSIBLE_METADATA

使用`ANSIBLE_METADATA`变量描述有关其他工具使用的模块的信息， 在文件的头部定义。

```python
ANSIBLE_METADATA = {'metadata_version': '1.0',
					'status': ['preview'],
					'supported_by': 'community'}
```

#### 定义DOCUMENTATION

接着`ANSIBLE_METADATA`，定义`DOCUMENTATION`变量描述模块的描述信息，参数，作者和许可信息。

```python
DOCUMENTATION = '''
---
module: remote_copy
short_description: Copy a file on the remote host
version_added: "2.9"
description:
  - The remote_copy module copies a file on the remote host from a given source to a provided destination.
options:
  source:
    description:
      - Path to a file on the source file on the remote host
    required: true
  dest:
    description:
      - Path to the destination on the remote host for the copy
    required: true
author:
  - "Lework"
'''
```

#### 定义EXAMPLES

接着`DOCUMENTATION`, 使用`EXAMPLES`变量用来描述模块的一个或多个示例使用

```python
EXAMPLES = '''
# Example from Ansible Playbooks
- name: backup a config file
  remote_copy:
        source: /tmp/foo
        dest: /tmp/bar
'''
```

#### 定义RETURN

使用`RETURN`变量用来描述模块的返回数据信息

```python
RETURN = '''
source:
    description: Path to a file on the source file on the remote host
    type: str
    returned: success
    sample: "/path/to/file.name"
dest:
    description: Path to the destination on the remote host for the copy
    type: string
    returned: success
    sample: "/path/to/destination.file"
'''
```

### 查看帮助

```bash
# ansible-doc -M /etc/ansible/library/ remote_copy
> REMOTE_COPY    (/etc/ansible/library/remote_copy.py)

        The remote_copy module copies a file on the remote host from a given source to a provided destination.

  * This module is maintained by The Ansible Community
OPTIONS (= is mandatory):

= dest
        Path to the destination on the remote host for the copy


= source
        Path to a file on the source file on the remote host



AUTHOR: Lework
        METADATA:
          status:
          - preview
          supported_by: community
        

EXAMPLES:

# Example from Ansible Playbooks
- name: backup a config file
  remote_copy:
        source: /tmp/foo
        dest: /tmp/bar


RETURN VALUES:

source:
    description: Path to a file on the source file on the remote host
    type: str
    returned: success
    sample: "/path/to/file.name"
dest:
    description: Path to the destination on the remote host for the copy
    type: string
    returned: success
    sample: "/path/to/destination.file"

```



## 模块文件

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
# Copyright: (c) 2020, lework
# GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)

ANSIBLE_METADATA = {'metadata_version': '1.0',
		    'status': ['preview'],
	            'supported_by': 'community'}

DOCUMENTATION = '''
---
module: remote_copy
short_description: Copy a file on the remote host
version_added: "2.9"
description:
  - The remote_copy module copies a file on the remote host from a given source to a provided destination.
options:
  source:
    description:
      - Path to a file on the source file on the remote host
    required: true
  dest:
    description:
      - Path to the destination on the remote host for the copy
    required: true
author:
  - "Lework"
'''

EXAMPLES = '''
# Example from Ansible Playbooks
- name: backup a config file
  remote_copy:
	source: /tmp/foo
	dest: /tmp/bar
'''

RETURN = '''
source:
    description: Path to a file on the source file on the remote host
    type: str
    returned: success
    sample: "/path/to/file.name"
dest:
    description: Path to the destination on the remote host for the copy
    type: string
    returned: success
    sample: "/path/to/destination.file"
'''

import os
import shutil
from ansible.module_utils.basic import AnsibleModule

def main():
    module_args = dict(
            source=dict(required=True, type='str'),
            dest=dict(required=True, type='str')
    )

    result = dict(
        changed=False,
        source='',
        dest=''
    )

    module = AnsibleModule(
        argument_spec=module_args,
        supports_check_mode=True
    )

    if module.check_mode:
       module.exit_json(**result)

    if not os.path.isfile(module.params['source']):
        module.fail_json(msg='The '+ module.params['source'] +' file was not found', **result)

    try:
        shutil.copy(module.params['source'], module.params['dest'])
    except Exception as e:
        module.fail_json(msg=e, **result)

    result['source'] = module.params['source']
    result['dest'] = module.params['dest']

    if os.path.isfile(module.params['dest']):
        result['changed'] = True
       
    remote_facts = {'rc_source': module.params['source'], 'rc_dest': module.params['dest'] }
    result['ansible_facts'] = remote_facts

    module.exit_json(**result)

if __name__ == '__main__':
    main()

```

这是一个非常简单的模块使用，