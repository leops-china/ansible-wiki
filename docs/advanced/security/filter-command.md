# 过滤危险命令

批量执行命令时，需要把一些危险命令屏蔽掉，从而将降低使用人员的误操作。

## 测试环境

ansible `2.9.6.0`

os `Centos 7.7 X64`

python `2.7.5`


## 需要过滤规则的模块

- command 
- shell
- script
- raw

## 需要过滤的命令

- rm -rf /
- halt
- poweroff
- reboot
- shutdown -h now
- shutdown -r now

## 编写过滤代码

我们在解析完task后进行过滤，这就是 `/usr/lib/python2.7/site-packages/ansible/playbook/play.py` 中的Play类的load方法

我们在这个文件中添加filter_cmd方法，进行过滤命令。
```python
def filter_cmd(data):
  filter_modules = ('command', 'shell', 'script', 'raw')
  filter_commands = ('rm -rf /','halt', 'poweroff', 'reboot', 'shutdown -h now','shutdown -r now')
  filter_commands = map(lambda x:x.replace(' ', '').lower(), filter_commands)
  for t in data['tasks']:
    if'action' in t:
      if t['action']['module'] in filter_modules:
        if t['action']['args']['_raw_params'].replace(' ', '').lower() in filter_commands:
          raise AnsibleParserError("Refused to execute the [%s] command in the [%s] module." % (t['action']['args']['_raw_params'], t['action']['module']))
    else:
      for m in filter_modules:
        if m in t:
          args=parse_kv(t[m], check_raw=True)
          if args['_raw_params'].replace(' ', '').lower() in filter_commands:
            raise AnsibleParserError("Refused to execute the [%s] command in the [%s] module." % (t[m], m))
```

在Play类的load方法中引用filter_cmd过滤命令
在`p = Play()`上方添加`filter_cmd(data)`

```python
    @staticmethod
    def load(data, variable_manager=None, loader=None):
        if ('name' not in data or data['name'] is None) and 'hosts' in data:
            if isinstance(data['hosts'], list):
                data['name'] = ','.join(data['hosts'])
            else:
                data['name'] = data['hosts']
        filter_cmd(data)
        p = Play()
        return p.load_data(data, variable_manager=variable_manager, loader=loader)
```
在文件顶部引入需要的模块

```python
from ansible.parsing.splitter import parse_kv
```

## 测试ansible
```bash
[root@master ansible]# ansible node1 -m shell -a 'halt'
ERROR! Refused to execute the [halt] command in the [shell] module.
[root@master ansible]# ansible node1 -m shell -a 'rm -rf /'
ERROR! Refused to execute the [rm -rf /] command in the [shell] module.
[root@master ansible]# ansible node1 -m command -a 'shutdown -r now'
ERROR! Refused to execute the [shutdown -r now] command in the [command] module.
[root@master ansible]# ansible localhost -m command -a 'echo shutdown -r now'
localhost | SUCCESS | rc=0 >>
shutdown -r now
```

## 测试ansible-playbook

使用rm删除/
```bash
[root@master ansible]# cat test_filter.yml 
---
- hosts: node1
  tasks:
   - name: test
     command: "Rm -rf / chdir=/tmp/ creates=/tmp/a.txt"
[root@master ansible]# ansible-playbook test_filter.yml 
ERROR! Refused to execute the [Rm -rf / chdir=/tmp/ creates=/tmp/a.txt] command in the [command] module.
```
关机
```bash
[root@master ansible]# cat test_filter.yml 
---

- hosts: node1
  tasks:
   - name: test
     shell: "shutdown -r now"
[root@master ansible]# ansible-playbook test_filter.yml 
ERROR! Refused to execute the [shutdown -r now] command in the [shell] module.
```

测试正常通过。

> 本次测试过滤只是给大家提供一个思路，并非是一个完美的，有很多东西大家可以根据自己的需求进行更改。
