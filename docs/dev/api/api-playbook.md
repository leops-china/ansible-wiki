# 使用 API 运行 playbook

## 需求

使用 Ansible API的方式执行playbook中的任务

## 环境

- os `Centos 7.7 X64`
- ansible `2.9.6.0`
- python `2.7.5`

## 主机清单

```ini
# cat /etc/ansible/hosts
[test]
node1 ansible_ssh_host=192.168.77.130 ansible_port=22 
node2 ansible_ssh_host=192.168.77.130 ansible_port=22
```

## api 示例

```python
#!/bin/env python
#! coding: utf-8

import os
from ansible.module_utils.common.collections import ImmutableDict
from ansible.parsing.dataloader import DataLoader
from ansible.vars.manager import VariableManager
from ansible.inventory.manager import InventoryManager
from ansible.executor.playbook_executor import PlaybookExecutor
from ansible import context


# 设置ansible选项
context.CLIARGS = ImmutableDict(connection='smart', module_path=['/to/mymodules'], forks=10, become=None,
                                become_method=None, become_user=None, check=False, diff=False, syntax=False, start_at_task=None)


# 设置主机密码，主机未定义密码的时候才生效，conn_pass指连接远端的密码，become_pass指提升权限的密码
passwords = dict(conn_pass='123456', become_pass='123456')

# 主机清单文件
host_path = '/etc/ansible/hosts'

if not os.path.exists(host_path):
  print '[INFO] The [%s] inventory does not exist' % host_path
  sys.exit()


# 初始话需要的类
variable_manager = VariableManager()
# 用来管理变量，包括主机、组、扩展等变量，该类在之前的Inventory内置

# 需要初始化的对象
loader = DataLoader() # 负责查找和读取yaml，json和ini文件

# 创建主机清单，使用path作为配置文件的源文件，或者用逗号分隔的字符串作为主机
inventory = InventoryManager(loader=loader, sources=host_path)

# 变量管理器负责合并所有不同的源
variable_manager = VariableManager(loader=loader, inventory=inventory)

# 多个yaml文件则以列表形式
playbook_path=['/etc/ansible/test.yml']

for i in playbook_path:
  if not os.path.exists(i):
    print '[INFO] The [%s] playbook does not exist' % i
    sys.exit()

playbook = PlaybookExecutor(playbooks=playbook_path,inventory=inventory,
              variable_manager=variable_manager,loader=loader,passwords=passwords)

# 执行playbook
result = playbook.run()

# 返回执行结果
print ('执行结果: %s' % result)
```

##执行结果

```bash
# python test-playbook.py

PLAY [all] *******************************************************************************************************************************************************************************************

TASK [hello] *****************************************************************************************************************************************************************************************
ok: [node1] => {
    "msg": "hello api."
}

PLAY RECAP *******************************************************************************************************************************************************************************************
node1                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

执行结果: 0
[root@node130 ansible]# vim hosts 
[root@node130 ansible]# python test_playbook.py

PLAY [all] *******************************************************************************************************************************************************************************************

TASK [hello] *****************************************************************************************************************************************************************************************
ok: [node1] => {
    "msg": "hello api."
}
ok: [node2] => {
    "msg": "hello api."
}

PLAY RECAP *******************************************************************************************************************************************************************************************
node1                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
node2                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

执行结果: 0
```