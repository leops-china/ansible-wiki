# filter plugins: split

## 需求

1. 实现python的字符串分割
2. 实现re的正则表达式分割

## Filter 类

```python
class FilterModule(object):
    ''' A filter to split a string into a list. '''
    def filters(self):
        return {
            'filter_name' : filter_function,
        }
```
所有的filter类都是上诉构造

- `filter_name`  是 Ansible Jinja2 filter的name。
- `filter_function(string)`  是处理字符的方法, 如`{{ 'test' | filter_name }}`， test字符串会传递给string。

## 编写插件

```python
# cat filter_plugins/split.py
import re

def split_string(string, seperator=None, maxsplit=-1):
    try:
        return string.split(seperator, maxsplit)
    except:
        return list(string)

def split_regex(string, seperator_pattern):
    try:
        return re.split(seperator_pattern, string)
    except:
        return list(string)

class FilterModule(object):
    ''' A filter to split a string into a list. '''
    def filters(self):
        return {
            'split' : split_string,
            'split_regex' : split_regex,
        }
```

## 运行 playbook
```bash
# cat split.yml
- hosts: localhost
  gather_facts: no
  tasks:
    - debug: msg={{ 'a b c' | split }}
    - debug: msg={{ '1c2c3' | split('c') }}
    - debug: msg={{ 'dev.example.com' | split_regex('\.') }}
    
# ansible-playbook split.yml

PLAY [localhost] *****************************************************************************************

TASK [debug] *****************************************************************************************
ok: [localhost] => {
    "msg": [
        "a", 
        "b", 
        "c"
    ]
}

TASK [debug] *****************************************************************************************
ok: [localhost] => {
    "msg": [
        "1", 
        "2", 
        "3"
    ]
}

TASK [debug] *****************************************************************************************
ok: [localhost] => {
    "msg": [
        "dev", 
        "example", 
        "com"
    ]
}

PLAY RECAP *****************************************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```



## 运行 ad-hoc 命令

执行ad-hoc命令时，需要指定插件目录，可以在`anisble.cfg`中指定，也可以使用环境变量

在`ansible.cfg`中指定

```ini
# cat ansible.cfg
[defaults]
filter_plugins     = /etc/ansible/filter_plugins
```

或使用环境变量

```bash
export ANSIBLE_FILTER_PLUGINS=/etc/ansible/filter_plugins
```

执行命令

```bash
# ansible localhost -m debug -a "msg={{'a b c' | split }}"
localhost | SUCCESS => {
    "msg": [
        "a", 
        "b", 
        "c"
    ]
}
```

