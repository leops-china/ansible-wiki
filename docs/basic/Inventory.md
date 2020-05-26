# 4. 认识主机清单

Ansible 可同时操作属于一个组的多台主机, 组和主机之间的关系通过 `inventory` 文件配置. 默认的文件路径为 `/etc/ansible/hosts`, 执行命令的时候使用 `-i` 参数即可指定主机清单。


## 主机清单示例

主机清单文件主要有 `ini` 和 `yaml` 格式两种语法格式

```ini
mail.example.com       # 定义主机fqdn地址, 且已经与控制节点ssh互信

[webservers]  # 方括号[]中是组名
host1  # 定义主机名称, 且已经与控制节点ssh互信
host2:5522  # 指定连接主机和端口号
localhost ansible_connection=local  # ansible_connection可以定义连接类型, local是在本地执行
host3 http_port=80 maxRequestsPerChild=808  # 定义主机变量, 除了ansible定义的特殊名称外，其他的都是主机变量
host4 ansible_host=192.168.1.50 ansible_port=2222 ansible_user=root ansible_password=12345 # 指定别名，定义主机ssh连接信息
www[1:50].example.com # 定义 1-50范围内的主机
www-[a:f].example.com # 定义 a-f 范围内内的主机

[dbservers]
three.example.com  ansible_python_interpreter=/usr/local/bin/python3  # 定义python执行ansible，这个是指定被控节点的。
192.168.77.123  ansible_ruby_interpreter=/usr/bin/ruby.1.9.3  # 定义ruby执行文件
 

[webservers:vars] # 定义webservers组的变量
ntp_server=ntp.example.com
proxy=proxy.example.com

[server:children] # 定义server组的子成员
webservers
dbservers

[server:vars] # 定义server组的变量
zabbix_server:192.168.77.121
```

上列配置的一些解释：

- 主机可以在多个组中配置。
- `ansible_connection` 是执行主机的连接类型，默认是smart
- `ansible_host` 主机ssh连接地址
- `ansible_port` 主机ssh连接端口
- `ansible_user` 主机ssh连接用户
- `ansible_password` 主机ssh连接用户密码
- `ansible_python_interpreter` 指定python的执行路径
- `[webservers:vars]`  定义webservers组的变量
- `[server:children]`  定义server组的子成员


也可使使用yaml格式来表示

```yaml

all:
  children:
​    usa:
​      children:
​        southeast:
​          children:
​            atlanta:
​              hosts:
​                host1:
​                host2:
​            raleigh:
​              hosts:
​                host2:
​                host3:
​          vars:
​            some_server: foo.southeast.example.com
​            halon_system_timeout: 30
​            self_destruct_countdown: 60
​            escape_pods: 2
​        northeast:
​        northwest:
​        southwest:
```

> yaml格式配置的还是挺复杂的，可读性也差，建议使用`ini`方式来设置主机清单。 


## 默认组

在主机清单中，ansible会自动的生成两个组。

- `all`  所有的主机。
- `ungrouped` 包含没有组的主机。

尽管这两个组是永远存在的，但也有可能是隐藏的，不会出现group_names之类的组列表中。


## 主机变量和组变量

如果你不想在主机清单中定义主机的变量或者组的变量，ansible还支持在特定的目录中定义变量。

变量文件必须以yaml语法定义。

如默认在`/etc/ansible/host_vars/` 目录中定义主机变量，文件名称以主机名称命名，结束可以用'.yml', '.yaml', '.json'三种格式。

```bash
cat /etc/ansible/host_vars/host1
---
ntp_server: acme.example.org
database_server: storage.example.org
```


如默认在`/etc/ansible/group_vars/` 目录中定义组变量，文件名称以组名称命名，结束可以用'.yml', '.yaml', '.json'三种格式。

```bash
cat /etc/ansible/group_vars/webservers
---
ntp_server: acme.example.org
database_server: storage.example.org
```


## 变量合并

我们可以通过多种方式给主机定义变量，如果在各个环节都设置了变量，到底哪个变量生效呢？这就要看ansible的变量优先级，优先级高的会覆盖优先级低的变量。

优先顺序，all最低，host最高

- all group
- parent group
- child group
- host

相同组时，默认情况下，按字母顺序后面组的定义会覆盖前面的。也可以使用ansible_group_priority调整优先级，数值越大优先级越高，默认为1，相同优先级时，后者优先。

```ini
[a_group:vars]
testvar=a
ansible_group_priority=10
[b_group]
testvar=b
```


## 使用多个主机清单

在命令参数中，使用多个 `-i` 就可以指定多个主机清单 

```bash
ansible all -i staging -i production -m ping
ansible all -i /tmp/staging -i /tmp/production -m ping
```

也可以指定一个目录

```
inventory/
  01-openstack.yml          # configure inventory plugin to get hosts from Openstack cloud
  02-dynamic-inventory.py   # add additional hosts with dynamic inventory script
  03-static-inventory       # add static hosts
  group_vars/
    all.yml                 # assign variables to all hosts
```

```bash
ansible all -i inventory -m ping
```


## 主机内置变量列表

**用于主机连接**

| 参数               | 描述                                                         |
| ------------------ | ------------------------------------------------------------ |
| ansible_connection | 与主机的连接类型.比如:local,  ssh 或者 paramiko. Ansible 1.2 以前默认使用 paramiko.1.2 以后默认使用 'smart','smart'   方式会根据是否支持 ControlPersist, 来判断'ssh' 方式是否可行. |

**用于所有连接**

| 参数 |  描述                                          |
| ------------ | ------------------------------------------------------------ |
| ansible_host | 将要连接的远程主机名.与你想要设定的主机的别名不同的话,可通过此变量设置. |
| ansible_port | 连接端口号，如果是ssh的话，默认是22           |
| ansible_user | 用于连接认证的用户名                                            |
| ansible_password | 用于连接认证的用户名密码                                            |

**ssh连接参数**

| 参数 |  描述                                          |
| ------------ | ------------------------------------------------------------ |
| ansible_ssh_private_key_file | ssh 使用的私钥文件.适用于有多个密钥,而你不想使用 SSH 代理的情况. |
| ansible_ssh_common_args      | 此设置附加到sftp，scp和ssh的缺省命令行                       |
| ansible_sftp_extra_args      | 此设置附加到默认sftp命令行。                                 |
| ansible_scp_extra_args       | 此设置附加到默认scp命令行。                                  |
| ansible_ssh_extra_args       | 此设置附加到默认ssh命令行。                                  |
| ansible_ssh_pipelining       | 确定是否使用SSH管道。这可以覆盖ansible.cfg中得设置。      |
| ansible_ssh_executable       | ssh可执行文件                                                |

**权限提升参数**



| 参数               | 描述                                                         |
| ------------------ | ------------------------------------------------------------ |
| ansible_become        | 开启提权，等同于`ansible_sudo`，`ansible_su`              |
| ansible_become_method | 提权方式                                                  |
| ansible_become_user   | 提权用户，等同于`ansible_sudo_user`，`ansible_su_user`    |
| ansible_become_password   | 提权密码,等同于`ansible_sudo_password`，`ansible_su_password` |
| ansible_become_exe    | 提权所用的可执行文件，等同于`ansible_sudo_exe`,`ansible_su_exe`  |
| ansible_become_flags  | 提权命令的参数，等同于`ansible_sudo_flags`,`ansible_su_flags` |

**远程主机环境参数**

| 参数                       | 描述                                                         |
| -------------------------- | ------------------------------------------------------------ |
| ansible_shell_type         | 目标系统的shell类型.默认情况下,命令的执行使用   'sh' 语法,可设置为 'csh' 或 'fish'. |
| ansible_python_interpreter | 目标主机的 python   路径.适用于的情况: 系统中有多个 Python, 或者命令路径不是"/usr/bin/python",比如  \*BSD, 或者 /usr/bin/python |
| ansible_*_interpreter      | 这里的"*"可以是 ruby   或 perl 或其他语言的解释器，作用和ansible_python_interpreter 类似 |
| ansible_shell_executable   | 这将设置ansible控制器将在目标机器上使用的shell，覆盖ansible.cfg中的配置，默认为/bin/sh。 |

**非SSH连接类型参数**

ansible默认是使用 `ssh` 连接主机，但也不限制于这种方式，可以通过使用主机特定参数 `ansible_connection = <connector>`，来更改连接类型。以下是支持的连接类型。

| 参数 |  描述                   |
| ------ | -------------------- |
| local  | 在控制端本地执行     |
| docker | 使用本地Docker客户端 |
| ansible_host | 容器连接的主机 |
| ansible_port | 容器连接的端口 |
| ansible_become | 如果设置为true，则会使用begin_user在容器内进行操作。|
| ansible_docker_extra_args | Docker 的额外参数|

一个创建容器的小例子

```yaml
- name: create jenkins container
  docker_container:
    docker_host: myserver.net:4243
    name: my_jenkins
    image: jenkins

- name: add container to inventory
  add_host:
    name: my_jenkins
    ansible_connection: docker
    ansible_docker_extra_args: "--tlsverify --tlscacert=/path/to/ca.pem --tlscert=/path/to/client-cert.pem --tlskey=/path/to/client-key.pem -H=tcp://myserver.net:4243"
    ansible_user: jenkins
  changed_when: false

- name: create directory for ssh keys
  delegate_to: my_jenkins
  file:
    path: "/var/jenkins_home/.ssh/jupiter"
    state: directory
```

## 在运行的时候增加主机

使用 `add_host` 模块动态添加运行主机，此类主机只有在运行时才会向内存中添加，运行结束后，也不会添加到静态主机清单文件中。

```yaml
- name: add new node into runtime inventory
  add_host:
    hostname: webserver
    groups: web
​    ansible_host: 192.168.77.129
    ansible_port: 22
```

## 限定主机清单的运行主机

使用`--limit hostname`可以在运行任务的时候，只允许在此主机上运行。

```yaml
[root@master ansible]# ansible-playbook test.yml --list-hosts
 playbook: test.yml
  play #1 (test2): test2        TAGS: []
​    pattern: [u'test2']
​    hosts (3):
​      node1
​      node3
​      node2
[root@master ansible]# ansible-playbook test.yml --list-hosts --limit node3,node2
playbook: test.yml
  play #1 (test2): test2        TAGS: []
​    pattern: [u'test2']
​    hosts (2):
​      node3
​      node2
```

## 示例

### 连接本地主机

不需要在主机清单里定义，直接使用 `localhost` 或 `127.0.0.1` 就可以连接本地了

```bash
# ansible localhost -m ping
localhost | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}

# ansible 127.0.0.1 -m ping
127.0.0.1 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}

```

### 使用别名连接主机

**定义主机清单**
```bash
# cat /etc/ansible/hosts

alias_host ansible_host=192.168.77.131 ansible_port=22 ansible_user=root ansible_password=123456 # 指定别名，定义主机ssh连接信息
```
**测试连通性**
```bash
# ansible alias_host -m ping
alias_host | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
```

### 使用 ssh 秘钥连接主机
**开启远程主机秘钥认证**
```bash
# echo 'PubkeyAuthentication yes' >> /etc/ssh/sshd_config
# systemctl restart sshd
```

**配置远程主机秘钥**
```bash
# ssh-keygen -t rsa -P '' -b 4096 -f ~/.ssh/id_rsa
# cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
# chmod 600 ~/.ssh/authorized_keys
```

**将刚刚生成的私钥 `~/.ssh/id_rsa` 拷贝到 ansible 节点**
```bash
# mv id_rsa /opt/131.key
# chmod 600 /opt/131.key
```

**定义主机清单**
```bash
# cat /etc/ansible/hosts
192.168.77.131 ansible_ssh_private_key_file=/opt/131.key
```
> 不指定 `ansible_user` 则使用运行ansible命令的用户

!!! note
    如果 `private_key` 使用了 **passphrase** ，可使用下列命令，将密码保存在 ssh-agent 中。
    ```bash
    ssh-agent bash
    ssh-add /opt/131.key
    ```

**测试连通性**
```bash
# ansible 192.168.77.131 -m ping
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}

```
### 使用 跳板机 连接主机

> 通过 192.168.77.132 连接192.168.77.131， 192.168.77.132 需安装`nc`

**添加132节点到kown_hosts**
```bash
# ssh 192.168.77.132
The authenticity of host '192.168.77.132 (192.168.77.132)' can't be established.
ECDSA key fingerprint is SHA256:2lWSIJMF9r8hnfLwlKONY07eQCeZaDVZ/xWZizr9wqs.
ECDSA key fingerprint is MD5:be:82:d9:23:45:18:f2:e3:fa:32:56:65:c9:b1:4b:07.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.77.132' (ECDSA) to the list of known hosts.
```

1. 使用ssh代理参数配置

**定义主机清单**
```bash
# cat /etc/ansible/hosts
192.168.77.131 ansible_ssh_private_key_file=/root/131.key ansible_ssh_common_args="-o ProxyCommand=\"sshpass -p '123456' ssh -qay -p 22 root@192.168.77.132 'nc %h %p'\""
```
> ansible_ssh_common_args 配置ssh连接的参数

**测试连通性**

```bash
# ansible 192.168.77.131 -m ping
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
```


2. 使用本地ssh配置主机代理

**配置ssh**

```bash
# cat ~/.ssh/config 
Host 192.168.77.131
        User root
        Port 22
        TCPKeepAlive yes
        ForwardAgent yes
        ProxyCommand sshpass -p '123456' ssh -qaY -p 22 root@192.168.77.132 'nc %h %p'
```

**定义主机清单**
```bash
# cat /etc/ansible/hosts
192.168.77.131 ansible_ssh_private_key_file=/opt/131.key
```

**测试连通性**

```bash
# ansible 192.168.77.131 -m ping
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}

```

3. 使用ssh代理

> 不需要在192.168.77.132上安装nc软件了

**定义主机清单**
```bash
# cat /etc/ansible/hosts
192.168.77.131 ansible_ssh_private_key_file=/root/131.key ansible_ssh_common_args="-o ProxyCommand=\"sshpass -p '123456' ssh -W %h:%p -q -p 22 root@192.168.77.132\""
```
> ansible_ssh_common_args 配置ssh连接的参数

**测试连通性**

```bash
# ansible 192.168.77.131 -m ping
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
```

### 命令行指定主机清单

```bash
# ansible -i '192.168.77.131,192.168.77.132' 192.168.77.* -m ping -k
SSH password: 
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
192.168.77.132 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}

```

通过 `-i` 参数， 指定用逗号分隔的主机列表即可。 

不过不能指定`ansible_*` 开头的变量，即不能定义连接密码。

## 动态主机清单

ansible 不仅可以使用`yaml`,`ini`等格式的静态文件配置主机清单，还可以使用动态的源作为主机清单，详细内容请见 [使用动态主机](/advanced/dynamic-hosts)