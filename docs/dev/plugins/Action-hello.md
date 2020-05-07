# action plugins: hello

## 需求

编写一个hello插件

## 编写插件

文件路径 `action_plugins/hello.py`

```bash
#!/usr/bin/env python

from ansible.plugins.action import ActionBase


class ActionModule(ActionBase):

    def run(self, tmp=None, task_vars=None):

        if task_vars is None:
            task_vars = dict()
        result = super(ActionModule, self).run(tmp, task_vars)

        args = self._task.args.copy()
        if 'name' not in args:  # 设置模块默认参数
            args['name'] = 'Tom'
        result.update(self._execute_module(module_args=args, task_vars=task_vars), _ansible_verbose_always=True) # 执行模块并更新模块返回数据,不指定module_name时，默认使用action 名称

        return result # 返回字典信息
```

## 编写模块

文件路径: `library/hello.py`

```python
#!/usr/bin/env python

ANSIBLE_METADATA = {'metadata_version': '1.0',
					'status': ['preview'],
					'supported_by': 'community'}

DOCUMENTATION = '''
---
module: hello
version_added: "0.1"
short_description: Hello module
description:
    - Module to say hello.
options:
    name:
        description:
            - Name to greet.
        default: False
'''

EXAMPLES = '''
- action: hello name='tom'

- hello:
    name: tom
'''

from ansible.module_utils.basic import AnsibleModule

def main():
    argument_spec = dict(
        name = dict(required=True, type='str'),
    )

    module = AnsibleModule(argument_spec=argument_spec)

    result = { "changed": False, "rc" : 0}

    name = module.params.get('name')

    if name:
        result['msg'] = "Hello %s!" % name
    else:
        result['failed'] = True
        result['msg'] = "Empty name is invalid"
        result['rc'] = 1

    if result.get('failed'):
        module.fail_json(**result)
    else:
        module.exit_json(**result)


if __name__ == '__main__':
    main()
```



## 执行 playbook

```yaml
# cat test_action.yml
---
- hosts: 192.168.77.130
  gather_facts: no
  tasks:
   - action: hello name='bob'
   - hello:
   - hello:
       name: ''
```

执行结果

```bash
# ansible-playbook test_action.yml

PLAY [192.168.77.130] *************************************************************************************

TASK [hello] *************************************************************************************
ok: [192.168.77.130] => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "msg": "Hello bob!", 
    "rc": 0
}

TASK [hello] *************************************************************************************
ok: [192.168.77.130] => {
    "changed": false, 
    "msg": "Hello Tom!", 
    "rc": 0
}

TASK [hello] *************************************************************************************
fatal: [192.168.77.130]: FAILED! => {
    "changed": false, 
    "msg": "Empty name is invalid", 
    "rc": 1
}

PLAY RECAP *************************************************************************************
192.168.77.130             : ok=2    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0 
```

## 执行 ad-hoc

配置`ansible.cfg`,设置自定义的插件目录

```ini
[defaults]
library            = /etc/ansible/library
action_plugins     = /etc/ansible/action_plugins
```

```bash
# ansible 192.168.77.130 -m hello
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "msg": "Hello Tom!", 
    "rc": 0
}

# ansible 192.168.77.130 -m hello -a "name=bob"
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "msg": "Hello bob!", 
    "rc": 0
}

# ansible 192.168.77.130 -m hello -a "name="   
192.168.77.130 | FAILED! => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "msg": "Empty name is invalid", 
    "rc": 1
}
```

