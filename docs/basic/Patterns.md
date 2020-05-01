# 5. Patterns 匹配

**Patterns** 是定义Ansible要执行的主机。Ansible Patterns 可以引用一个主机，一个IP地址，一个清单组，一个集合组或清单中的所有主机。 Patterns 具有高度的灵活性，您可以排除或要求主机的子集，使用 **通配符** 或 **正则表达式** 来定义 Patterns 。

**命令格式**

```
ansible <pattern> -m <module_name> -a "<module options>"

ansible-playbook -l <pattern>  [options] playbook.yml
```

**使用示例**

```
ansible * -m service -a "name=httpd state=restarted"

ansible-playbook  -l all playbook.yml
```



在 **playbook** 的剧本中，需要在每个 **play** 中`hosts: `行中定义

```
- name: <play_name>
  hosts: <pattern>
```

**使用示例**

```
- name: restart webservers
  hosts: webservers
```



## 常用匹配

| 描述               | Pattern(s)                      | Targets                                   |
| ------------------ | ------------------------------- | ----------------------------------------- |
| 所有主机           | `all` 或者 `*`                  | 主机清单中的所有主机                      |
| 一个主机(精确匹配) | `host1` 或者 `192.168.77.131`   | `host1` 或者 `192.168.77.131`             |
| 多个主机           | `host1:host2` 或者`host1,host2` | `host1:host2` 或者`host1,host2`           |
| 一个组             | `webservers`                    | `webservers`组中的主机                    |
| 多个组(或匹配)     | `webservers:dbservers`          | `webservers`和`dbservers`所有的主机       |
| 排除组(非模式匹配) | webservers:!atlanta             | `webservers`组中除`atlanta`之外的所有主机 |
| 交集组(交集匹配)   | webservers:&dbservers           | `webservers`和`dbservers`都存在的主机     |

 

**通配符匹配**

```
*.com
web*.com:dbserver
```

`*`表示所有字符

 

**组合匹配**

```
webservers:dbservers:&staging:!phoenix
```

在webservers 或者dbservers 组中，必须还存在于staging 组中，但是不在phoenix 组中



## 局限性

**Patterns** 依赖于 **主机清单** (inventory)，如果说匹配不到主机清单里的数据，则会返回如下警告

```bash
# ansible none -m ping 
[WARNING]: Could not match supplied host pattern, ignoring: none
[WARNING]: No hosts matched, nothing to do
```

## 高级特性

### 使用变量

在ansible-palybook 命令中，你也可以使用变量来组成这样的表达式，但是你必须使用`-e`的选项来指定这个表达式

**playbook**

```bash
# cat  playbook.yml
---
- name: Using variables in patterns
  hosts: "{{ hosts }}"
  tasks:
    - name: ping
      ping:

```

**执行playbook**

```bash
ansible-playbook playbook.yml -e "hosts=192.168.77.131"
ansible-playbook playbook.yml -e "hosts=192.168.77.132"
```

### 使用切片

可以使用下标来选择组中的各个主机或范围，类似python中的切片

```
webservers[0]
webservers[1:]
webservers[0:25]
```

- `[0]`表示组第一个成员

- `[1:]` 表示组内第2个含第2个之后的所有成员
- `[0:25] `表示组第1个到第24个成员

### 正则表达式

在开头的地方使用“~”，表示这是一个正则表达式

```
~(web|db).*\.example\.com
```

### 限定主机

可以使用命令行选项更改playbook中定义的Patterns 的行为

```
ansible-playbook site.yml -l 192.168.77.129

ansible-playbook site.yml -l @retry_hosts.txt
```

只执行`-l`后的主机, `@`开头指定文件