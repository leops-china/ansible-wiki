# 适用于 EX407 / EX294 的Ansible示例考试

这是我为准备EX407而创建的Ansible样本考试。我尚未参加EX407考试。

您也可以将其用于新的RHCE 8考试EX294。

与真实考试一样，将不提供样本考试问题的答案。

## 要求

总共有18个问题。

您将需要五个RHEL 7（或CentOS 7）虚拟机才能成功完成所有问题。

一台VM将配置为Ansible控制节点。其他四个VM将用于应用剧本来解决示例考试问题。在整个样本考试中将使用以下FQDN。

1.  **ansible-control.hl.local**  – Ansible控制节点
2.  **ansible2.hl.local**  –托管主机
3.  **ansible3.hl.local**  –托管主机
4.  **ansible4.hl.local**  –托管主机
5.  **ansible5.hl.local**  –托管主机

在继续进行操作之前，需要满足几个要求：

1.  **ansible-control.hl.local** 服务器具有对所有受管服务器的无密码SSH访问（使用root用户）。
2.  **ansible5.hl.local** 服务器已`/dev/sdb`连接1GB辅助磁盘。
3. 在任何服务器上都没有创建普通用户。

## 提示与建议

我试图涵盖尽可能多的考试目标，但是请注意，不会出现与动态清单有关的问题。

有些问题可能取决于其他问题的结果。请先阅读所有问题，然后再继续。

请注意，样本考试的目的是测试您的技能。请不要在评论部分发布您的剧本。

## 考试样题

注意：您具有对所有五台服务器的超级用户访问权限。

### 任务1：Ansible安装和配置

在控制节点上安装ansible软件包（包括所有依赖项）并配置以下内容：

1. 使用 **devops** 密码创建常规的用户 **自动化** 。除非您正在执行需要在清单主机上创建 **自动化** 用户的任务＃2，否则请将该用户用于所有示例考试任务和练习簿。您具有对所有五台服务器的超级用户访问权限。
2. 您为此示例考试创建的所有剧本和其他Ansible配置都应存储在中`/home/automation/plays`。

创建`/home/automation/plays/ansible.cfg`满足以下要求的配置文件：

1. 角色路径应包括`/home/automation/plays/roles`，以及示例考试过程中可能需要的任何其他路径。
2. 库存文件路径为`/home/automation/plays/inventory`。
3. 默认情况下，特权升级是 **禁用** 的。
4. Ansible应该能够一次管理 **10个主机** 。
5. Ansible应该使用 **自动化** 用户连接到所有受管节点。

`/home/automation/plays/inventory`使用以下命令创建清单文件：

1. ansible2.hl.local是 **代理** 主机组的成员。
2. ansible3.hl.local是 **Webservers** 主机组的成员。
3. ansible4.hl.local是 **Webservers** 主机组的成员。
4. ansible5.hl.local是 **数据库** 主机组的成员。

### 任务2：临时命令

在控制节点上生成SSH密钥对。您可以手动执行此步骤。

编写一个`/home/automation/plays/adhoc`使用Ansible ad-hoc命令来实现以下目的的脚本：

1. 在所有清单主机（不是控制节点）上创建用户 **自动化** 。
2. SSH密钥（您生成的）已复制到 **自动化** 用户的所有清单主机中，并存储在中`/home/automation/.ssh/authorized_keys`。
3. 该 **自动化** 允许用户提升对所有库存的主机权限，而无需提供密码。

运行adhoc脚本后，您应该能够使用没有密码的 **自动化** 用户SSH进入所有清单主机，以及运行所有特权命令。

### 任务3：文件内容

创建一个`/home/automation/plays/motd.yml`在所有清单主机上运行的剧本，并执行以下操作：

1. 该剧本应将所有现有内容替换为`/etc/motd`文字。文本取决于主机组。
2. 在 **代理** 主机组中的主机上，该行应为“ Welcome to HAProxy server”。
3. 在 **Web服务器** 主机组中的主机上，该行应为“ Welcome to Apache server”。
4. 在 **数据库** 主机组中的主机上，该行应为“ Welcome to MySQL server”。

### 任务4：配置SSH服务器

创建一个`/home/automation/plays/sshd.yml`在所有清单主机上运行的剧本，并按如下方式配置SSHD守护程序：

1. 标语设置为 `/etc/motd`
2. X11转发禁用
3. MaxAuthTries设置为3

### 任务5：Ansible保管箱

创建Ansible库文件`/home/automation/plays/secret.yml`。加密/解密密码为 **devops** 。

将以下变量添加到Vault：

1.  **user_password** 的值为 ** devops** 
2.  **database_password** 与价值 ** DEVOPS** 

将Ansible保管库密码存储在文件中`/home/automation/plays/vault_key`。

### 任务6：用户和组

已为您提供以下用户列表。

使用`/home/automation/plays/vars/user_list.yml`文件保存此内容。

```
---
users:
  - username: alice
    uid: 1201
  - username: vincent
    uid: 1202
  - username: sandy
    uid: 2201
  - username: patrick
    uid: 2202
```

创建`/home/automation/plays/users.yml`使用库文件`/home/automation/plays/secret.yml`实现以下目的的剧本：

1. 用户ID以1开头的用户应在 **webservers** 主机组中的 **服务器** 上创建。用户密码应通过 **user_password** 变量使用。
2. 应在 **数据库** 主机组中的服务器上创建用户ID以2开头的用户。用户密码应通过 **user_password** 变量使用。
3. 所有用户都应该是辅助组 **轮的** 成员。
4. 应该`/bin/bash`为所有用户设置Shell 。
5. 帐户密码应使用SHA512哈希格式。
6. 每个用户都应该上传一个SSH密钥（使用先前创建的SSH密钥，请参阅任务＃2）。

运行剧本后，用户应该可以无需密码即可通过SSH进入各自的服务器。

### 任务7：计划任务

创建一个`/home/automation/plays/regular_tasks.yml`在 **代理** 主机组中的 **服务器** 上运行的剧本，并执行以下操作：

1. 将创建一个根crontab记录，该记录每小时运行一次。
2. cron作业将文件附加 **date** 命令`/var/log/time.log`的输出。

### 任务8：软件存储库

创建一个`/home/automation/plays/repository.yml`在 **数据库** 主机组中的服务器上运行的剧本，并执行以下操作：

1. 创建一个YUM存储库文件。
2. 存储库的名称是 **mysql56-community** 。
3. 仓库的描述是“ MySQL 5.6 YUM Repo”。
4. 仓库的基本URL是 **http://repo.mysql.com/yum/mysql-5.6-community/el/7/x86_64/** 。
5. 仓库GPG密钥位于 **http://repo.mysql.com/RPM-GPG-KEY-mysql** 。
6. 储存库GPG检查已启用。
7. 存储库已启用。

### 任务9：创建和使用角色

创建一个名为 **sample-mysql** 的角色并将其存储在中`/home/automation/plays/roles`。该角色应满足以下要求：

1. 在设备`/dev/sdb`上创建大小为800MB的主分区号1 。
2. `vg_database`创建一个名为LVM的卷组，该卷组使用上面创建的主分区。
3. `lv_mysql`在卷组中创建了一个名为512MB 的LVM逻辑卷`vg_database`。
4. 在逻辑卷`lv_mysql`上创建了一个XFS文件系统。
5. 逻辑卷`lv_mysql`已永久安装在上`/mnt/mysql_backups`。
6.  **mysql-community-server** 软件包已安装。
7. 防火墙配置为允许MySQL端口TCP 3306上的所有传入流量。
8. MySQL根用户密码应从变量 **database_password** 设置（请参阅任务＃5）。
9. MySQL服务器应已启动并在启动时启用。
10. MySQL服务器配置文件是从`my.cnf.j2`Jinja2模板生成的，具有以下内容：

```
[mysqld]
bind_address = {{ ansible_default_ipv4.address }}
skip_name_resolve
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

symbolic-links=0
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES 

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
```

创建`/home/automation/plays/mysql.yml`使用该角色并在 **数据库** 主机组中的主机上运行的剧本。

### 任务10：创建和使用角色（更多）

创建一个名为 **sample-apache** 的角色并将其存储在中`/home/automation/plays/roles`。该角色应满足以下要求：

1. 该 **httpd的** ， **mod_ssl** 和 **PHP** 的软件包。Apache服务正在运行并在启动时启用。
2. 防火墙配置为允许HTTP端口TCP 80和HTTPS端口TCP 443上的所有传入流量。
3. 每次`/var/www/html/index.html`修改文件时，都应重新启动Apache服务。
4. Jinja2模板文件`index.html.j2`用于创建`/var/www/html/index.html`具有以下内容的文件：

```
The address of the server is: IPV4ADDRESS
```

IPV4ADDRESS是受管节点的IP地址。

创建`/home/automation/plays/apache.yml`使用该角色并在 **webservers** 主机组中的主机上运行的剧本。

### 任务11：从Ansible Galaxy下载角色并使用它们

使用Ansible Galaxy下载并安装 **geerlingguy.haproxy** 角色`/home/automation/plays/roles`。

创建一个`/home/automation/plays/haproxy.yml`在 **代理** 主机组中的 **服务器** 上运行的剧本，并执行以下操作：

1. 使用geerlingguy.haproxy角色在 **Webservers** 主机组中的主机之间负载均衡请求。
2. 使用 **轮询** 负载均衡方法。
3. HAProxy后端服务器应仅配置为使用HTTP（端口80）。
4. 防火墙配置为允许端口80上的所有传入流量。

如果您的剧本有效，则执行“  **curl http://ansible2.hl.local/**  ”应从Web服务器返回输出（请参阅任务＃10）。再次运行该命令应返回其他Web服务器的输出。

### 任务12：安全性

创建一个`/home/automation/plays/selinux.yml`在 **webservers** 主机组中的主机上运行的剧本，并执行以下操作：

1. 使用selinux  **RHEL系统角色** 。
2. 启用 **httpd_can_network_connect**  SELinux布尔值。
3. 更改必须在系统重新引导后继续有效。

### 任务13：使用条件控制播放执行

创建一个`/home/automation/plays/sysctl.yml`在所有清单主机上运行的剧本，并执行以下操作：

1. 如果服务器具有超过2048MB的RAM，则参数 **vm.swappiness** 设置为10。
2. 如果服务器的RAM少于2048MB，则会显示以下错误消息：

 **服务器内存小于2048MB** 

### 任务14：使用存档

创建一个`/home/automation/plays/archive.yml`在 **数据库** 主机组中的主机上运行的剧本，并执行以下操作：

1. `/mnt/mysql_backups/database_list.txt`创建的文件包含以下行：dev，test，qa，prod。
2. 该文件的gzip存档`/mnt/mysql_backups/database_list.txt`已创建并存储在中`/mnt/mysql_backups/archive.gz`。

### 任务15：处理事实

创建一个`/home/automation/plays/facts.yml`在 **数据库** 主机组中的主机上运行的剧本，并执行以下操作：

1. 创建了一个自定义的Ansible事实 **server_role = mysql** ，可以在使用Ansible设置模块时从 ** ansible_local.custom.sample_exam** 中检索该事实。

### 任务16：软件包

创建一个`/home/automation/plays/packages.yml`在所有清单主机上运行的剧本，并执行以下操作：

1. 在 **代理** 主机组中的主机上安装 **tcpdump** 和 **mailx** 软件包。
2. 在 **数据库** 主机组中的主机上安装 **lsof** 和 **mailx** 以及程序包。

### 任务17：服务

创建一个`/home/automation/plays/target.yml`在 **webservers** 主机组中的主机上运行的剧本，并执行以下操作：

1. 将默认启动目标设置为 **multi-user** 。

### 任务18：创建和使用模板来创建定制的配置文件

创建一个`/home/automation/plays/server_list.yml`执行以下操作的剧本：

1. Playbook使用Jinja2模板在 **数据库** 主机组中的主机上`server_list.j2`创建文件。`/etc/server_list.txt`
2. 该文件`/etc/server_list.txt`归 **自动化** 用户所有。
3. 文件权限设置为 **0600** 。
4. SELinux文件标签应设置为 **net_conf_t** 。
5. 该文件的内容是所有清单主机的FQDN的列表。

运行剧本后，文件内容`/etc/server_list.txt`应为以下内容：

```
ansible2.hl.local
ansible3.hl.local
ansible4.hl.local
ansible5.hl.local
```

注意：如果任何清单主机的FQDN发生变化，则重新运行剧本应使用新值更新文件。

> 来源： https://www.lisenet.com/2019/ansible-sample-exam-for-ex407/

