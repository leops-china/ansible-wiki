# 6. 使用 ad-hoc 命令

Ansible ad-hoc 命令使用 `/usr/bin/ansible`命令行工具来自动化一个或多个受管节点上的单个任务。 临时命令既快速又简单，但不可重用。

## ad-hoc 命令

```bash
ansible [pattern] -m [module] -a "[module options]"
```
执行结果说明

rc:  命令返回码（0表示成功）

## ad-hoc 示例

### 执行shell命令

#### command

重启服务器

```bash
ansible servers -a "reboot"
```

不指定`-m` 模块时，将使用ansible的默认模块command，它不会通过shell进行处理，所以像`$HOME`和像`“<”`，`“>”`，`“|”`，`“;” `和`“＆”`将不工作



默认情况下，Ansible使用5个并发进程。 如果你要扩大并发，使用`-f 10` 参数指定数量即可。

```bash
ansible servers -a "reboot" -f 10
```

默认情况下，Ansible连接远端用户是当前用户，使用`-u` 参数可以修改

```bash
ansible servers -a "reboot" -f 10 -u root
```

如果运行用户没有权限执行，使用`--become` 可以提升权限,默认是`sudo`方式

```bash
ansible servers -a "reboot" -f 10 -u root --become
ansible servers -a "reboot" -f 10 -u test --become --become-method sudo --become-user root --ask-become-pass
```

`--become-method` 指定提升方式，`--become-user` 指定提升用户 `--ask-become-pass` 告知提升密码



#### shell

获取web组里得eth0接口信息

```bash
ansible web -m shell -a "ifconfig eth0|grep addr"
```

#### raw

如果说远程主机没有`python` 模块时，可以使用`raw` 模块执行命令

```bash
ansible web -m raw -a "ifconfig eth0|grep addr"
```

#### script

执行脚本

```
ansible web -m script -a ip.sh
```

> 将本地脚本传送到远程节点上运行

 

### 文件管理

#### copy 

 拷贝本地的/etc/hosts 文件到web组所有主机的/tmp/hosts（空目录除外）

```bash
ansible web -m copy -a "src=/etc/hosts dest=/tmp/hosts"
```

 拷贝本地的ntp文件到目的地址，设置其用户及权限，如果目标地址存在相同的文件，则备份源文件。

```bash
ansible web -m copy -a "src=/mine/ntp.conf dest=/etc/ntp.conf owner=root group=root mode=644 backup=yes force=yes"
```

#### fetch

从远端服务器拷贝到本机

```bash
ansible web -m fetch -a "src=/etc/hosts dest=/tmp/temp_hosts flat=yes"
```

#### file 

更改文件的用户及权限

```bash
ansible web -m file -a "dest=/tmp/a.txt mode=600 owner=user group=user"
```

创建目录，类似mkdir -p

```bash
ansible web -m file -a "dest=/tmp/test mode=755 owner=user group=user state=directory"
```

删除文件或者目录

```bash
ansible web -m file -a "dest=/tmp/test state=absent"
```

创建软连接，并设置所属用户和用户组

```bash
ansible web -m file -a  "src=/file/to/link/to dest=/path/to/symlink owner=user group=user state=link"
```

 touch 一个文件并添加用户读写权限，用户组去除写执行权限，其他组减去读写执行权限

```bash
ansible web -m file -a  "path=/etc/foo.conf state=touch mode='u+rw,g-wx,o-rwx'"
```

#### unarchive

将本地的压缩文件解压到目标主机

```bash
ansible web -m unarchive -a "src=foo.tgz dest=/opt/foo“
```



### 管理软件包

apt、yum 模块分表用于管理Ubuntu 系列和RedHat 系列系统软件包

#### apt

更新仓库缓存，并安装"foo"

```bash
ansible web -m apt -a "name=foo update_cache=yes"
```

删除 "foo"
```bash
ansible web -m apt -a "name=foo state=absent"
```


安装  "foo"
```bash
ansible web -m apt -a "name=foo state=present"
```


安装  1.0版本的 "foo"
```bash
ansible web -m apt -a "name=foo=1.00 state=present"
```


安装最新得"foo"
```bash
ansible web -m apt -a "name=foo state=latest"
```


注释：Ansible 支持很多操作系统的软件包管理，使用时-m 指定相应的软件包管理工具模块，如果没有这样的模块，可以自己定义类似的模块或者使用command 模块来安装软件包

#### yum

安装 最新的 Apache
```bash
ansible web -m yum -a  "name=httpd state=latest"
```


删除apache
```bash
ansible web -m yum -a  "name=httpd state=absent"
```


从testing 仓库中安装最后一个版本得apache
```bash
ansible web -m yum -a  "name=httpd enablerepo=testing state=present"
```


更新所有的包
```bash
ansible web -m yum -a  "name=* state=latest"
```


安装远程的rpm包
```bash
ansible web -m yum -a  "name=http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present"
```


安装  'Development tools' 包组
```bash
ansible web -m yum -a  "name='@Development tools' state=present"
```

#### package

使用远程主机的包管理器进行安装，卸载，更新软件。相对于`apt`,`yum`而言，兼容性更好。

安装ntpdate

```bash
ansible web -m package -a  "name=ntpdate stat=present"
```



### 用户和用户组

#### user

添加用户 'user'并设置其 uid 和主要的组'admin'
```bash
ansible web -m user -a "name=user comment='I am user' uid=1040 group=admin"
```


添加用户 'user'并设置其登陆shell，并将其假如admins和developers组
```bash
ansible web -m user -a "name=user shell=/bin/bash groups=admins,developers append=yes"
```

删除用户 'user'
```bash
ansible web -m user -a "name=user state=absent remove=yes"
```


创建 user 用户得 2048-bit SSH key，并存放在 ~user/.ssh/id_rsa
```bash
ansible web -m user -a "name=user generate_ssh_key=yes ssh_key_bits=2048 ssh_key_file=.ssh/id_rsa"
```


设置用户过期日期
```bash
ansible web -m user -a "name=user shell=/bin/zsh groups=nobdy expires=1422403387"
```


创建 test 组，并设置 gid 为1000
```bash
ansible web -m group -a "name=test gid=1000 state=present"
```

删除 test 组
```bash
ansible web -m group -a "name=test state=absent"
```

### 版本控制

#### git

Ansible 模块能够通知变更，当代码更新时，可以告诉 Ansible 做一些特定的任务，比如从git 部署代码然后重启 apache 服务等
```bash
ansible web -m git -a "repo=https://github.com/Icinga/icinga2.git dest=/tmp/myapp   version=HEAD"
```

### 服务管理

#### service

确保 web 组所有主机的 httpd 是启动的
```bash
ansible web -m service -a "name=httpd state=started"
```


重启 web 组所有主机的httpd 服务
```bash
ansible web -m service -a "name=httpd state=restarted"
```


确保web组所有主机的httpd 是关闭的
```bash
ansible web -m service -a "name=httpd state=stopped"
```

#### systemd

启动服务

```bash
ansible web -m systemd -a "state=started name=httpd"
```

重载配置

```bash
ansible web -m systemd -a "daemon_reload=yes"
```

### 防火墙管理

#### iptables

允许tcp 22端口通过
```bash
ansible all -m iptables  -a "chain=INPUT destination_port=22 protocol=tcp jump=ACCEPT"
```

#### firewalld

运行https端口通过

```bash
ansible all -m firewalld -a "service=https permanent=yes state=enabled"
```

### 文件内容操作

#### lineinfile

开启selinux， 替换以SELINUX=开头的行，如果没有匹配到，则新增一条数据。
```bash
ansible all -m lineinfile  -a "dest=/etc/selinux/config regexp=^SELINUX= line=SELINUX=enforcing"
```


删除以SELINUX=开头的行
```bash
ansible all -m lineinfile  -a "dest=/tmp/config regexp=^SELINUX= state=absent"
```


如果文件中, line值不存在，则向文件中添加line的内容
```bash
ansible all -m lineinfile  -a "dest=/tmp/config  line='test'"
```

#### replace

替换文件内容

```bash
ansible all -m  replace  -a "dest=/etc/selinux/config regexp=^SELINUX=disabled replace=SELINUX=enforcing"
```

### 定时任务

每天5点，2点得时候执行 ls -alh > /dev/null

```bash
ansible test -m cron -a "name='check dirs' minute='0' hour='5,2' job='ls -alh > /dev/null'"
```

### 搜集系统信息

搜集主机的所有系统信息

```bash
ansible all -m setup
```

搜集系统信息并以主机名为文件名分别保存在/tmp/facts 目录

```bash
ansible all -m setup --tree /tmp/facts
```

搜集和内存相关的信息

```bash
ansible all -m setup -a 'filter=ansible_*_mb'
```

搜集网卡信息

```bash
ansible all -m setup -a 'filter=ansible_eth[0-2]'
```

### 指定连接方式

```bash
ansible all -i 'centos,' -c docker -m shell -a 'ps aux'
ansible all -i 'centos,' -c local -m shell -a 'ifconfig'
```

### 后台运行

长时间运行的操作可以放到后台执行，ansible 会检查任务的状态；在主机上执行的同一个任

务会分配同一个job ID

后台执行命令3600s，-B 表示后台执行的时间

```bash
ansible all -B 3600 -a "/usr/bin/long_running_operation --do-stuff"
```

**检查任务的状态**

```bash
ansible all -m async_status -a "jid=123456789"
```

后台执行命令最大时间是1800s 即30 分钟，-P 每60s 检查下状态默认15s

```bash
ansible all -B 1800 -P 60 -a "/usr/bin/long_running_operation --do-stuff"
```

## 练习

大家通过下列命令来查看帮助，练习下表格中常用模块的使用。

```bash
ansible-doc file
```


| 类型        | 模块                                                         |
| ----------- | ------------------------------------------------------------ |
| 文件操作    | stat   find   file   lineinfile   blockinfile   template   replace |
| 包管理      | apt   gem   npm   pip   yum   package   easy_install   rpm_key |
| 传输        | fetch   copy   unarchive   get_url                           |
| 用户组      | user   group                                                 |
| 文件包含    | import_tasks   include_tasks   include_vars                  |
| mysql数据库 | mysql_db   mysql_replication   mysql_user                    |
| 服务        | service   systemd   supervisorctl                            |
| 检查        | uri   wait_for                                               |
| 其他        | debug   fail   selinux   set_fact   sysctl   authorized_key  |