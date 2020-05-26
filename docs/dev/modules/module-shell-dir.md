# 使用 Shell 脚本操作目录

## 需求

创建或删除目录。


模块使用以下参数。

| 参数  | 说明                    |
| ----- | ----------------------- |
| name  | 目录名                  |
| path  | 创建目录的路径          |
| state | present创建，absent删除 |


## 编写 module

```bash
#!/bin/bash
#
# This code is ansible module example using bash.
 
function exit_json() {
    if [ -n "$2" ] ; then
        json_structure="
            {
                \"changed\": $1,
                $2
            }
        "
    else
        json_structure="
            {
                \"changed\": $1
            }
        "
    fi
    echo $json_structure
    exit 0
}
 
function fail_json() {
    json_structure="
        {
            \"failed\": "true",
            \"msg\": \"$1\"
        }
    "
    echo $json_structure
    exit 1
}
 
function main() {
    # arg parse
    arg_flag=0
    for arg in $(cat $1) ; do
        echo $arg | grep -E ',|\[|\]' > /dev/null 2>&1
        if [ $? -eq 0 ] ; then
            arg2="$arg2$arg"
            arg_flag=1
            continue
        fi
 
        if [ $arg_flag -eq 0 ] ; then
            key=`echo $arg | cut -d '=' -f 1`
            value=`echo $arg | cut -d '=' -f 2`
            declare "module_arg_$key=$value"
            arg_flag=0
        else
            key=`echo $arg2 | cut -d '=' -f 1`
            value=`echo $arg2 | cut -d '=' -f 2`
            declare "module_arg_$key=$value"
            arg_flag=0
        fi
    done
 
    # parameters
    name=$module_arg_name
    path=$module_arg_path
    state=$module_arg_state
 
    # When state is present
    if [ $state == "present" -a -n "$name" -a -n "$path" ] ; then
        if [ -d $path ] ; then
            if [ -d "$path/$name" ] ; then
                exit_json "false"
            else
                result=`mkdir "$path/$name" 2>&1`
                if [ -n "$result" ] ; then
                    fail_json "`echo -n $result`"
                else
                    exit_json "true" "\"directory_path\": \"$path/$name\""
                fi
            fi
        else
            fail_json "Error: not found $module_arg_path"
        fi
    fi
 
    # When state is absent
    if [ $state == "absent" -a -n "$name" -a -n "$path" ] ; then
        if [ -d "$path/$name" ] ; then
            rm -rf "$path/$name" 2>&1 > /dev/null
            if [ -d "$path/$name" ] ; then
                fail_json "Error: failed delete folder $path/$name"
            fi
            exit_json "true" "\"directory_path\": \"$path/$name\""
        else
            exit_json "false"
        fi
    fi
 
    fail_json "Required parameters include: name, path, state"
}
 
main $1
```



## ansible 配置

在 `/etc/ansible/ansible.cfg` 中指定模块目录

```ini
[defaults]
library = /etc/ansible/library/
```

## 执行 ad-hoc

```bash
# ansible localhost -m dir -a "name=test path=/tmp state=present"
localhost | CHANGED => {
    "changed": true,
    "directory_path": "/tmp/test"
}

# file /tmp/test    
/tmp/test: directory

# ansible localhost -m dir -a "name=test path=/tmp state=absent" 
localhost | CHANGED => {
    "changed": true,
    "directory_path": "/tmp/test"
}

# file /tmp/test
/tmp/test: cannot open (No such file or directory)
```

## 执行 playbook

```yaml
---
- name: Directory operation playbook
  hosts: localhost
  gather_facts: no
  tasks:
    - dir:
        name: test
        path: /tmp
        state: present
    - dir:
        name: test2
        path: /tmp
        state: absent
```


执行结果
```bash
# ansible-playbook test_dir.yml
PLAY [Directory operation playbook] *******************************************************************************************************************

TASK [dir] ********************************************************************************************************************************************
changed: [localhost]

TASK [dir] ********************************************************************************************************************************************
ok: [localhost]

PLAY RECAP ********************************************************************************************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   


# file /tmp/test
/tmp/test: directory
# file /tmp/test2
/tmp/test2: cannot open (No such file or directory)
```
