# 其他语言开发module

Ansible是由 **python** 语言开发的，但其支持的模块可以是任何语言，只要模块代码可以在远程执行即可。比如bash脚本需要`bash`解释器执行。

## bash语言

使用bash语言开发module

### 功能实现

创建一个文件。

### 创建module

```bash
# cd /etc/ansible/library/
# cat touch.sh

#!/bin/sh

ANSIBLE_METADATA="{'metadata_version': '1.0',
		  'status': ['preview'],
		  'supported_by': 'community'}"

DOCUMENTATION="
---
module: touch
short_description: Touch a file on the remote host
version_added: '2.9'
description:
  - The touch module touch a file on the remote host.
options:
  file:
    description:
      - Path to a file on the remote host
    required: true
author:
  - 'Lework'
"

EXAMPLES="
# Example from Ansible Playbooks
- name: touch file
  touch:
    file: /tmp/foo
"

RETURN="
path:
    description: Path to a file on the remote host
    type: string
    returned: success
    sample: "/path/to/file.name"
"

args_file=$1

[ ! -f "$args_file" ] && echo -n '{"failed": true, "msg": "missing required arguments: file"}' && exit 1
args_result=$(cat $args_file | gawk -F'file=' '{print $2}' | gawk -F' ' '{print $1}')

[ ! -n "$args_result" ] && echo -n "{\"failed\": true, \"msg\": \"file () is absent, cannot continue\", \"file\": \"$args_result\"}" && exit 1

touch $args_result && echo -n "{\"changed\": true, \"rc\": $?,\"file\": \"$args_result\"}" || echo -n "{\"failed\": true, \"rc\": $?, \"file\": \"$args_result\"}"
exit $?

```
返回值一定是json dumps的字符串。

### 本地测试

ansible的参数都会被写入一个名为 **args** 的文件，代码中的`$1`变量就是这个文件的路径，读取这个文件的内容，就能获取file参数的值。

```bash
# cat args
file=/tmp/foo

# sh touch.sh args
{"changed": true, "rc": 0,"file": "/tmp/foo"}
```


### 执行playbook
```bash
# cat test_touch.yml 
---

- name: test remote_copy module
  hosts: 192.168.77.130
  gather_facts: false
  
  tasks:
    - name: touch file
      touch: file=/tmp/foo
      vars:
        ansible_sh_interpreter: /bin/sh

```

> ansible_sh_interpreter 指定执行模块的可执行文件

执行结果

```bash
# ansible-playbook test_touch.yml 

PLAY [test remote_copy module] *****************************************************************************************

TASK [touch file] *****************************************************************************************
changed: [192.168.77.130]

PLAY RECAP *****************************************************************************************
192.168.77.130             : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
```

### 执行ansible

```bash
# ansible 192.168.77.130 -M /etc/ansible/library/ -m touch -a "file=/tmp/a" -e "ansible_sh_interpreter=/bin/sh"
192.168.77.130 | CHANGED => {
    "changed": true, 
    "file": "/tmp/a", 
    "rc": 0
}

```