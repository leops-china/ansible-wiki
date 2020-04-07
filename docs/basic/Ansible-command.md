本文以 **ansible** 版本 `2.9.6`为准


## ansible

`ansible`命令是 **Ansible**的核心部分，其主要用于执行ad-hoc命令，即单条命令。默认后面需要跟主机和选项部分，默认不指定模块时，使用的是command模块。

```bash
# ansible --help
usage: ansible [-h] [--version] [-v] [-b] [--become-method BECOME_METHOD]
               [--become-user BECOME_USER] [-K] [-i INVENTORY] [--list-hosts]
               [-l SUBSET] [-P POLL_INTERVAL] [-B SECONDS] [-o] [-t TREE] [-k]
               [--private-key PRIVATE_KEY_FILE] [-u REMOTE_USER]
               [-c CONNECTION] [-T TIMEOUT]
               [--ssh-common-args SSH_COMMON_ARGS]
               [--sftp-extra-args SFTP_EXTRA_ARGS]
               [--scp-extra-args SCP_EXTRA_ARGS]
               [--ssh-extra-args SSH_EXTRA_ARGS] [-C] [--syntax-check] [-D]
               [-e EXTRA_VARS] [--vault-id VAULT_IDS]
               [--ask-vault-pass | --vault-password-file VAULT_PASSWORD_FILES]
               [-f FORKS] [-M MODULE_PATH] [--playbook-dir BASEDIR]
               [-a MODULE_ARGS] [-m MODULE_NAME]
               pattern
```

**位置参数**

| 参数    | 说明     |
| ------- | -------- |
| pattern | 主机匹配 |

**选项参数**

| 参数                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| --ask-vault-pass                                             | 提示输入vault 密码。                                         |
| --list-hosts                                                 | 输出匹配主机的列表。                                         |
| --playbook-dir BASEDIR                                       | 指定playbook目录，为`role`,`group_vars/etc`指定相对路径      |
| --syntax-check                                               | 对playbook进行语法检查，且不执行playbook。                   |
| --vault-id=VAULT_IDS                                         | 标识使用的vault id                                           |
| --vault-password-file=VAULT_PASSWORD_FILE                    | 指定vault密码文件                                            |
| --version                                                    | 显示程序版本信息                                             |
| -B SECONDS, --background SECONDS                             | 异步运行时，多长时间超时。                                   |
| -C, --check                                                  | 只是测试一下会改变什么内容，不会真正去执行;相反,试图预测一些可能发生的变化。 |
| -D, --diff                                                   | 当更改文件和模板时，显示这些文件得差异，比--check效果好。    |
| -M MODULE_PATH, --module-path MODULE_PATH                    | 要执行的模块的路径，默认路径`~/.ansible/plugins/modules:/usr/share/ansible/plu<br/>                        gins/modules)` |
| -P POLL_INTERVAL, --poll POLL_INTERVAL                       | 设置轮询间隔，默认15秒                                       |
| -a MODULE_ARGS, --args MODULE_ARGS                           | 指定模块参数                                                 |
| -e EXTRA_VARS, --extra-vars EXTRA_VARS                       | 添加附加变量，比如key=value，yaml，json格式。使用`@`指定文件 |
| -f FORKS, --forks FORKS                                      | 指定定要使用的并行进程数，默认为5个。                        |
| -h, --help                                                   | 显示此帮助信息。                                             |
| -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY | 指定主机清单文件或逗号分隔的主机，默认为/etc/ansible/hosts。 |
| -l SUBSET, --limit SUBSET                                    | 进一步限制所选主机/组模式，只执行`-l`后的主机和组。          |
| -m MODULE_NAME, --module-name MODULE_NAME                    | 要执行的模块，默认为command。                                |
| -o, --one-line                                               | 压缩输出，尝试将所有内容都在一行上输出。                     |
| -t TREE, --tree                                              | 指定tree的输出目录                                           |
| -v, --verbose                                                | 输出执行的详细信息，使用-vvv获得更多，-vvvv 启用连接调试     |

**特权升级选项**

| 参数                          | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| --become-method=BECOME_METHOD | 权限升级方法使用 ，默认为sudo，有效选择：[sudo \| su \| pbrun \| pfexec   \| runas \|    doas \| dzdo] |
| --become-user=BECOME_USER     | 使用哪个用户运行，默认为root                                 |
| -K, --ask-become-pass         | 提供权限提升密码                                             |
| -b, --become                  | 运行权限提升                                                 |

**连接选项**

| 参数                                                         | 说明                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| --private-key=PRIVATE_KEY_FILE,   --key-file=PRIVATE_KEY_FILE | 私钥路径，使用这个文件来验证连接                            |
| --scp-extra-args SCP_EXTRA_ARGS                              | 指定额外的参数传递给`scp` ，例如`-l`                        |
| --sftp-extra-args SFTP_EXTRA_ARGS                            | 指定额外的参数传递给`sftp` ，例如`-f`                       |
| --ssh-common-args SSH_COMMON_ARGS                            | 指定要传递给sftp / scp / ssh的通用参数（例如 ProxyCommand） |
| --ssh-extra-args SSH_EXTRA_ARGS                              | 指定额外的参数传递给`ssh` ，例如`-R`                        |
| -T TIMEOUT,   --timeout=TIMEOUT                              | 指定默认超时时间，默认是10S                                 |
| -c CONNECTION,   --connection=CONNECTION                     | 指定连接类型，默认smart                                     |
| -k, --ask-pass                                               | 要求用户输入请求连接密码                                    |
| -u REMOTE_USER,   --user=REMOTE_USER                         | 指定连接用户                                                |

**示例**：

```bash
ansible all -m ping

ansible 192.168.77.* -m ping

ansible all -m command -a ifconfig

ansible all -m shell -a "ifconfig eth0 |grep 'inet addr' "

ansible -i "192.168.77.129,192.168.77.130" 192.168.77.129  -m ping

ansible -i hosts  all --list-host

ansible -i hosts -l 192.168.77.130 all -m ping -t /tmp -vvvv

ansible web -l @retry_hosts.txt --list-hosts

ansible all -i 192.168.77.133, -m ping -k
```



## ansible-console

交互式命令执行界面

```bash
# ansible-console --help
usage: ansible-console [-h] [--version] [-v] [-b]
                       [--become-method BECOME_METHOD]
                       [--become-user BECOME_USER] [-K] [-i INVENTORY]
                       [--list-hosts] [-l SUBSET] [-k]
                       [--private-key PRIVATE_KEY_FILE] [-u REMOTE_USER]
                       [-c CONNECTION] [-T TIMEOUT]
                       [--ssh-common-args SSH_COMMON_ARGS]
                       [--sftp-extra-args SFTP_EXTRA_ARGS]
                       [--scp-extra-args SCP_EXTRA_ARGS]
                       [--ssh-extra-args SSH_EXTRA_ARGS] [-C] [--syntax-check]
                       [-D] [--vault-id VAULT_IDS]
                       [--ask-vault-pass | --vault-password-file VAULT_PASSWORD_FILES]
                       [-f FORKS] [-M MODULE_PATH] [--playbook-dir BASEDIR]
                       [--step]
                       [pattern]
```

**位置参数**

| 参数    | 说明     |
| ------- | -------- |
| pattern | 主机匹配 |

**选项参数**

| 参数                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| --ask-vault-pass                                             | 提示输入vault 密码。                                         |
| --list-hosts                                                 | 输出匹配主机的列表。                                         |
| --playbook-dir BASEDIR                                       | 指定playbook目录，为`role`,`group_vars/etc`指定相对路径      |
| --step                                                       | 一步一步的运行，每个任务都会循环是否执行                     |
| --syntax-check                                               | 对playbook进行语法检查，且不执行playbook。                   |
| --vault-id=VAULT_IDS                                         | 标识使用的vault id                                           |
| --vault-password-file=VAULT_PASSWORD_FILE                    | 指定vault密码文件                                            |
| --version                                                    | 显示程序版本信息                                             |
| -C, --check                                                  | 只是测试一下会改变什么内容，不会真正去执行;相反,试图预测一些可能发生的变化。 |
| -D, --diff                                                   | 当更改文件和模板时，显示这些文件得差异，比--check效果好。    |
| -M MODULE_PATH, --module-path MODULE_PATH                    | 要执行的模块的路径，默认路径`~/.ansible/plugins/modules:/usr/share/ansible/plu<br/>                        gins/modules)` |
| -f FORKS, --forks FORKS                                      | 指定定要使用的并行进程数，默认为5个。                        |
| -h, --help                                                   | 显示此帮助信息。                                             |
| -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY | 指定主机清单文件或逗号分隔的主机，默认为/etc/ansible/hosts。 |
| -l SUBSET, --limit SUBSET                                    | 进一步限制所选主机/组模式，只执行`-l`后的主机和组。          |
| -v, --verbose                                                | 输出执行的详细信息，使用-vvv获得更多，-vvvv 启用连接调试     |

**特权升级选项**

| 参数                          | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| --become-method=BECOME_METHOD | 权限升级方法使用 ，默认为sudo，有效选择：[sudo \| su \| pbrun \| pfexec   \| runas \|    doas \| dzdo] |
| --become-user=BECOME_USER     | 使用哪个用户运行，默认为root                                 |
| -K, --ask-become-pass         | 提供权限提升密码                                             |
| -b, --become                  | 运行权限提升                                                 |

 **连接选项**

| 参数                                                         | 说明                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| --private-key=PRIVATE_KEY_FILE,   --key-file=PRIVATE_KEY_FILE | 私钥路径，使用这个文件来验证连接                            |
| --scp-extra-args SCP_EXTRA_ARGS                              | 指定额外的参数传递给`scp` ，例如`-l`                        |
| --sftp-extra-args SFTP_EXTRA_ARGS                            | 指定额外的参数传递给`sftp` ，例如`-f`                       |
| --ssh-common-args SSH_COMMON_ARGS                            | 指定要传递给sftp / scp / ssh的通用参数（例如 ProxyCommand） |
| --ssh-extra-args SSH_EXTRA_ARGS                              | 指定额外的参数传递给`ssh` ，例如`-R`                        |
| -T TIMEOUT,   --timeout=TIMEOUT                              | 指定默认超时时间，默认是10S                                 |
| -c CONNECTION,   --connection=CONNECTION                     | 指定连接类型，默认smart                                     |
| -k, --ask-pass                                               | 要求用户输入请求连接密码                                    |
| -u REMOTE_USER,   --user=REMOTE_USER                         | 指定连接用户                                                |

 

**示例：**

```bash
ansible-console all -i 192.168.77.133, -m ping -k

root@all (1)[f:5]$ ping

192.168.77.133 | SUCCESS => {
    "changed": false, 
    "ping": "pong"

}
```

 

## ansible-doc

该指令用于查看模块信息，常用参数有两个-l 和 -s 

```bash
# ansible-doc --help
usage: ansible-doc [-h] [--version] [-v] [-M MODULE_PATH]
                   [--playbook-dir BASEDIR]
                   [-t {become,cache,callback,cliconf,connection,httpapi,inventory,lookup,netconf,shell,module,strategy,vars}]
                   [-j] [-F | -l | -s | --metadata-dump]
                   [plugin [plugin ...]]

```

 **位置参数**

| 参数   | 说明 |
| ------ | ---- |
| plugin | 插件 |

**选项参数**

| 参数                                                         | 说明                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| --metadata-dump                                              | 获取所有插件的metadata json数据                         |
| --playbook-dir BASEDIR                                       | 指定playbook目录，为`role`,`group_vars/etc`指定相对路径 |
| --version                                                    | 显示程序版本信息                                        |
| -F, --list_files                                             | 显示插件名称及其源文件，不显示摘要                      |
| -h, --help                                                   | 显示帮助文件                                            |
| -j, --json                                                   | 使用json格式输出                                        |
| -l, --list                                                   | 列出可用的插件                                          |
| -s, --snippet                                                | 显示指定插件的`playbook`摘要                            |
| -t {become,cache,callback,<br />cliconf,connection,httpapi,<br />inventory,lookup,netconf,<br />shell,module,strategy,vars},<br /> --type {become,cache,callback,<br />cliconf,connection,httpapi,<br />inventory,lookup,netconf,<br />shell,module,strategy,vars} | 指定插件类型，默认`module`                              |

 

**示例：**

```bash
ansible-doc -l
ansible-doc yum
ansible-doc yum -s
ansible-doc -t cache -l
ansible-doc -t become -l
```

## ansible-galaxy

ansible-galaxy 指令用于方便的从https://galaxy.ansible.com/ 站点下载第三方扩展模块，我们可以形象的理解其类似于centos下的yum、python下的pip或easy_install

```bash
# ansible-galaxy --help
usage: ansible-galaxy [-h] [--version] [-v] TYPE ...
```

 **位置参数**

| 参数       | 说明                      |
| ---------- | ------------------------- |
| collection | 管理Ansible Galaxy。      |
| role       | 管理Ansible Galaxy role。 |

 **选项参数**

| 参数          | 说明                                            |
| ------------- | ----------------------------------------------- |
| --version     | 显示程序版本号                                  |
| -h, --help    | 显示此帮助信息                                  |
| -v, --verbose | 详细模式（-vvv表示更多，-vvvv表示启用连接调试） |

 

**示例：**

```bash
ansible-galaxy search tomcat  # 搜索角色
ansible-galaxy install aeriscloud.docker #下载角色

ansible-galaxy list ragingbal.tomcat  

ansible-galaxy info ragingbal.tomcat

ansible-galaxy init abc  # 创建角色模板
# 安装的role在 /root/.ansible/roles/
```

 

##  ansible-playbook

对于需反复执行的、较为复杂的任务，我们可以通过定义 Playbook 来搞定。Playbook 是 Ansible 真正强大的地方，它允许使用变量、条件、循环、以及模板，也能通过角色 及包含指令来重用既有内容。

```bash
# ansible-playbook --help
usage: ansible-playbook [-h] [--version] [-v] [-k]
                        [--private-key PRIVATE_KEY_FILE] [-u REMOTE_USER]
                        [-c CONNECTION] [-T TIMEOUT]
                        [--ssh-common-args SSH_COMMON_ARGS]
                        [--sftp-extra-args SFTP_EXTRA_ARGS]
                        [--scp-extra-args SCP_EXTRA_ARGS]
                        [--ssh-extra-args SSH_EXTRA_ARGS] [--force-handlers]
                        [--flush-cache] [-b] [--become-method BECOME_METHOD]
                        [--become-user BECOME_USER] [-K] [-t TAGS]
                        [--skip-tags SKIP_TAGS] [-C] [--syntax-check] [-D]
                        [-i INVENTORY] [--list-hosts] [-l SUBSET]
                        [-e EXTRA_VARS] [--vault-id VAULT_IDS]
                        [--ask-vault-pass | --vault-password-file VAULT_PASSWORD_FILES]
                        [-f FORKS] [-M MODULE_PATH] [--list-tasks]
                        [--list-tags] [--step] [--start-at-task START_AT_TASK]
                        playbook [playbook ...]
```

 

**位置参数**

| 参数     | 说明         |
| -------- | ------------ |
| playbook | playbook文件 |

**选项参数**

| 参数                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| --ask-vault-pass                                             | 提示输入vault 密码。                                         |
| --flush-cache                                                | 清除fact缓存                                                 |
| --force-handlers                                             | 如果任务失败，也要运行handlers                               |
| --list-hosts                                                 | 输出匹配主机的列表。                                         |
| --list-tags                                                  | 列出所有可用的标签                                           |
| --list-tasks                                                 | 列出将要执行的所有任务                                       |
| --skip-tags=SKIP_TAGS                                        | 跳过运行标记此标签的任务                                     |
| -start-at-task=START_AT_TASK                                 | 在此任务处开始运行                                           |
| --step                                                       | 一步一步的执行：在运行之前确认每个任务                       |
| --syntax-check                                               | 对playbook进行语法检查，且不执行playbook。                   |
| --vault-id=VAULT_IDS                                         | 标识使用的vault id                                           |
| --vault-password-file=VAULT_PASSWORD_FILE                    | 指定vault密码文件                                            |
| --version                                                    | 显示程序版本信息                                             |
| -C, --check                                                  | 只是测试一下会改变什么内容，不会真正去执行;相反,试图预测一些可能发生的变化。 |
| -D, --diff                                                   | 当更改文件和模板时，显示这些文件得差异，比--check效果好。    |
| -M MODULE_PATH, --module-path MODULE_PATH                    | 要执行的模块的路径，默认路径`~/.ansible/plugins/modules:/usr/share/ansible/plu<br/>                        gins/modules)` |
| -e EXTRA_VARS, --extra-vars EXTRA_VARS                       | 添加附加变量，比如key=value，yaml，json格式。使用`@`指定文件 |
| -f FORKS, --forks FORKS                                      | 指定定要使用的并行进程数，默认为5个。                        |
| -h, --help                                                   | 显示此帮助信息。                                             |
| -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY | 指定主机清单文件或逗号分隔的主机，默认为/etc/ansible/hosts。 |
| -l SUBSET, --limit SUBSET                                    | 进一步限制所选主机/组模式，只执行`-l`后的主机和组。          |
| -t TAGS, --tags TAGS                                         | 运行指定的带有tags任务                                       |
| -v, --verbose                                                | 输出执行的详细信息，使用-vvv获得更多，-vvvv 启用连接调试     |

**特权升级选项**

| 参数                          | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| --become-method=BECOME_METHOD | 权限升级方法使用 ，默认为sudo，有效选择：[sudo \| su \| pbrun \| pfexec   \| runas \|    doas \| dzdo] |
| --become-user=BECOME_USER     | 使用哪个用户运行，默认为root                                 |
| -K, --ask-become-pass         | 提供权限提升密码                                             |
| -b, --become                  | 运行权限提升                                                 |

 **连接选项**

| 参数                                                         | 说明                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| --private-key=PRIVATE_KEY_FILE,   --key-file=PRIVATE_KEY_FILE | 私钥路径，使用这个文件来验证连接                            |
| --scp-extra-args SCP_EXTRA_ARGS                              | 指定额外的参数传递给`scp` ，例如`-l`                        |
| --sftp-extra-args SFTP_EXTRA_ARGS                            | 指定额外的参数传递给`sftp` ，例如`-f`                       |
| --ssh-common-args SSH_COMMON_ARGS                            | 指定要传递给sftp / scp / ssh的通用参数（例如 ProxyCommand） |
| --ssh-extra-args SSH_EXTRA_ARGS                              | 指定额外的参数传递给`ssh` ，例如`-R`                        |
| -T TIMEOUT,   --timeout=TIMEOUT                              | 指定默认超时时间，默认是10S                                 |
| -c CONNECTION,   --connection=CONNECTION                     | 指定连接类型，默认smart                                     |
| -k, --ask-pass                                               | 要求用户输入请求连接密码                                    |
| -u REMOTE_USER,   --user=REMOTE_USER                         | 指定连接用户                                                |

**示例：**

```bash
ansible-playbook -i hosts ssh-addkey.yml   # 指定主机清单文件

ansible-playbook -i hosts ssh-addkey.yml  --list-tags   # 列出tags

ansible-playbook -i hosts ssh-addkey.yml  -t install  # 执行install标签的任务

ansible-playbook -i hosts ssh-addkey.yml  -t install -e a=1  # 指定变量
```



## ansible-pull 

pull模式在被配置的机器上运行，速度很快。在这种模式下，你需要提供一个git仓库来供Ansible下载来配置你的机器。

```bash
# ansible-pull --help
usage: ansible-pull [-h] [--version] [-v] [-k]
                    [--private-key PRIVATE_KEY_FILE] [-u REMOTE_USER]
                    [-c CONNECTION] [-T TIMEOUT]
                    [--ssh-common-args SSH_COMMON_ARGS]
                    [--sftp-extra-args SFTP_EXTRA_ARGS]
                    [--scp-extra-args SCP_EXTRA_ARGS]
                    [--ssh-extra-args SSH_EXTRA_ARGS] [--vault-id VAULT_IDS]
                    [--ask-vault-pass | --vault-password-file VAULT_PASSWORD_FILES]
                    [-e EXTRA_VARS] [-t TAGS] [--skip-tags SKIP_TAGS]
                    [-i INVENTORY] [--list-hosts] [-l SUBSET] [-M MODULE_PATH]
                    [-K] [--purge] [-o] [-s SLEEP] [-f] [-d DEST] [-U URL]
                    [--full] [-C CHECKOUT] [--accept-host-key]
                    [-m MODULE_NAME] [--verify-commit] [--clean]
                    [--track-subs] [--check] [--diff]
                    [playbook.yml [playbook.yml ...]]
```

**位置参数**

| 参数     | 说明         |
| -------- | ------------ |
| playbook | playbook文件 |

**选项参数**

| 参数                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| --accept-host-key                                            | 指定仓库的主机秘钥                                           |
| --ask-vault-pass                                             | 提示输入vault 密码。                                         |
| --check                                                      | 只做检查，不做更改                                           |
| --clean                                                      | 工作存储库中的已修改文件将被删除                             |
| --diff                                                       | 更改（小的）文件和模板时，显示这些文件中的差异               |
| --full                                                       | 完整克隆                                                     |
| --list-hosts                                                 | 输出匹配主机列表                                             |
| --purge                                                      | 运行后清除                                                   |
| --skip-tags SKIP_TAGS                                        | 跳过运行标记此标签的任务                                     |
| --track-subs                                                 | 模块将跟踪最新的变化。   这相当于指定--remote标志来git子模块更新 |
| --vault-id=VAULT_IDS                                         | 标识使用的vault id                                           |
| --vault-password-file=VAULT_PASSWORD_FILE                    | 指定vault密码文件                                            |
| --verify-commit                                              | 验证已检出提交的GPG签名，如果失败则中止运行剧本。            |
| --version                                                    | 显示程序版本信息                                             |
| -C CHECKOUT,   --checkout=CHECKOUT                           | 指定克隆的分支                                               |
| -M MODULE_PATH, --module-path MODULE_PATH                    | 要执行的模块的路径，默认路径`~/.ansible/plugins/modules:/usr/share/ansible/plu<br/>                        gins/modules)` |
| -U URL, --url URL                                            | playbook仓库的地址                                           |
| -d DEST, --directory DEST                                    | 指定检出目录                                                 |
| -e EXTRA_VARS, --extra-vars EXTRA_VARS                       | 添加附加变量，比如key=value，yaml，json格式。使用`@`指定文件 |
| -f FORKS, --forks FORKS                                      | 指定定要使用的并行进程数，默认为5个。                        |
| -h, --help                                                   | 显示此帮助信息。                                             |
| -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY | 指定主机清单文件或逗号分隔的主机，默认为/etc/ansible/hosts。 |
| -l SUBSET, --limit SUBSET                                    | 进一步限制所选主机/组模式，只执行`-l`后的主机和组。          |
| -m MODULE_NAME, --module-name MODULE_NAME                    | 仓库模块名称，可选值('git', 'subversion', 'hg', 'bzr')默认为git。 |
| -o, --only-if-changed                                        | 当存储库已更新时才运行剧本                                   |
| -s SLEEP, --sleep SLEEP                                      | 指定睡眠时间                                                 |
| -t TAGS, --tags TAGS                                         | 运行指定的带有tags任务                                       |
| -v, --verbose                                                | 输出执行的详细信息，使用-vvv获得更多，-vvvv 启用连接调试     |

**特权升级选项**

| 参数                  | 说明             |
| --------------------- | ---------------- |
| -K, --ask-become-pass | 提供权限提升密码 |

 **连接选项**

| 参数                                                         | 说明                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| --private-key=PRIVATE_KEY_FILE,   --key-file=PRIVATE_KEY_FILE | 私钥路径，使用这个文件来验证连接                            |
| --scp-extra-args SCP_EXTRA_ARGS                              | 指定额外的参数传递给`scp` ，例如`-l`                        |
| --sftp-extra-args SFTP_EXTRA_ARGS                            | 指定额外的参数传递给`sftp` ，例如`-f`                       |
| --ssh-common-args SSH_COMMON_ARGS                            | 指定要传递给sftp / scp / ssh的通用参数（例如 ProxyCommand） |
| --ssh-extra-args SSH_EXTRA_ARGS                              | 指定额外的参数传递给`ssh` ，例如`-R`                        |
| -T TIMEOUT,   --timeout=TIMEOUT                              | 指定默认超时时间，默认是10S                                 |
| -c CONNECTION,   --connection=CONNECTION                     | 指定连接类型，默认smart                                     |
| -K, --ask-become-pass                                        | 要求用户输入请求连接密码                                    |
| -u REMOTE_USER,   --user=REMOTE_USER                         | 指定连接用户                                                |

**示例：**

```bash
ansible-pull -o -C master -d /tmp/pull -i /tmp/pull/hosts -U https://github.com/lework/Ansible-Pull-Example.git
```



## ansible-config

编辑管理ansible配置

```bash
# ansible-config --help
usage: ansible-config [-h] [--version] [-v] {list,dump,view} ...
```

**位置参数**

| 参数 | 说明               |
| ---- | ------------------ |
| list | 显示所有的参数配置 |
| dump | dump配置           |
| view | 查看配置文件       |

 **选项参数**

| 参数          | 说明                                            |
| ------------- | ----------------------------------------------- |
| --version     | 显示程序版本号                                  |
| -h, --help    | 显示此帮助信息                                  |
| -v, --verbose | 详细模式（-vvv表示更多，-vvvv表示启用连接调试） |

 

**示例：**

```bash
ansible-config view

ansible-config  list

ansible-config  dump
```





 

## ansible-inventory

查看主机清单信息

```bash
# ansible-inventory --help 
usage: ansible-inventory [-h] [--version] [-v] [-i INVENTORY]
                         [--vault-id VAULT_IDS]
                         [--ask-vault-pass | --vault-password-file VAULT_PASSWORD_FILES]
                         [--playbook-dir BASEDIR] [--list] [--host HOST]
                         [--graph] [-y] [--toml] [--vars] [--export]
                         [--output OUTPUT_FILE]
                         [host|group]
```

 **位置参数**

| 参数       | 说明        |
| ---------- | ----------- |
| host/group | 主机/主机组 |

**选项参数**

| 参数                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| --accept-host-key                                            | 指定仓库的主机秘钥                                           |
| --export                                                     | 导出信息，与--list或--graph一起使用                          |
| --output OUTPUT_FILE                                         | 导出信息到文件，与--list或--graph一起使用                    |
| --playbook-dir BASEDIR                                       | 指定playbook目录，为`role`,`group_vars/etc`指定相对路径      |
| --toml                                                       | 使用toml格式输出,默认是json格式                              |
| --vars                                                       | 输出变量信息，与--list或--graph一起使用                      |
| --vault-id=VAULT_IDS                                         | 标识使用的vault id                                           |
| --vault-password-file=VAULT_PASSWORD_FILE                    | 指定vault密码文件                                            |
| --version                                                    | 显示程序版本信息                                             |
| -h, --help                                                   | 显示此帮助信息。                                             |
| -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY | 指定主机清单文件或逗号分隔的主机，默认为/etc/ansible/hosts。 |
| -v, --verbose                                                | 输出执行的详细信息，使用-vvv获得更多，-vvvv 启用连接调试     |
| -y, --yaml                                                   | 使用yaml格式输出,默认是json格式                              |

**动作选项**

| 参数        | 说明                             |
| ----------- | -------------------------------- |
| --graph     | 创建主机清单图                   |
| --host HOST | 输出主机清单信息                 |
| --list      | 以json的格式输出所有主机清单信息 |



**示例：**

```bash
ansible-inventory --export --graph

ansible-inventory -i /etc/ansible/hosts --export --list

ansible-inventory --host=192.168.1.100

ansible-inventory --vars --list
 ```



## ansible-vault

ansible-vault主要应用于配置文件中含有敏感信息，又不希望他能被人看到，vault可以帮你加密/解密这个配置文件。这种playbook文件在执行时，需要加上 `--ask-vault-pass`参数，同样需要输入密码后才能正常执行。

```bash
# ansible-vault --help
usage: ansible-vault [-h] [--version] [-v]
                     {create,decrypt,edit,view,encrypt,encrypt_string,rekey}
                     ...
```

**位置参数**

| 参数           | 说明           |
| -------------- | -------------- |
| create         | 创建加密文件   |
| decrypt        | 解密文件       |
| edit           | 编辑加密文件   |
| view           | 查看加密文件   |
| encrypt        | 加密文件       |
| encrypt_string | 输出加密字符串 |
| rekey          | 重新加密文件   |

**选项参数**

| 参数          | 说明                                            |
| ------------- | ----------------------------------------------- |
| --version     | 显示程序版本号                                  |
| -h, --help    | 显示此帮助信息                                  |
| -v, --verbose | 详细模式（-vvv表示更多，-vvvv表示启用连接调试） |

**示例：**

```bash
ansible-vault create # /tmp/123 创建加密文件

ansible-vault view  # /tmp/123 查看加密文件

ansible-vault encrypt  # /tmp/abc 加密文件

ansible-vault decrypt  # /tmp/abc 解密文件

ansible-vault edit  # /tmp/abc 编辑加密文件

ansible-vault encrypt_string '123'  # 输出加密字符串
```



