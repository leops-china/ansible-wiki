# Ansible 最佳实践

介绍下ansible如何写作，如何执行，如何在生产中使用。

## 如何写作

### 像对待代码一样对待你的ansible

- 拥有版本控制
- 拥有可重复性
  - 从基本的playbook目录结构和静态的主机清单来构建roles
  - 后续可以自己开发模块和插件

### 不要使用个性化的书写方式

1. 为你的风格创建一个标准

   1. 使用标签
   2. 使用一致的空格缩进
   3. 任务、角色、变量和角色的语义化命名
   4. 目录结构

2. 执行的风格

   1. 先检查语法
   2. 列出执行主机
   3. 列出tasks任务
   4. 再去执行

3. 一个很好的[openshift-ansible]( https://github.com/openshift/openshift-ansible/blob/master/docs/style_guide.adoc )风格

    !!! note
        **python**

        **Python最大行长度**

        - 所有行不应超过80个字符。
        - 所有的行必须不超过120个字符。

        **ansible**

        **Ansible Yaml 文件扩展名称**

        -  所有Ansible Yaml文件必须是一个`.yml`扩展名(而不是`.YML`，`.yaml`等)。 

        **Ansible CLI变量**

        - 要从ansible CLI传递进来的变量必须有一个`cli_`前缀

        **Ansible全局变量**

        - 全局变量的前缀必须是`g_`

        **Ansible角色变量**

        - 角色变量必须有至少3个字符的前缀。请参阅下面的特定命名规则。

         **角色名称中包含3个(或更多)单词**

         以每个单词的第一个字母为例。

         3字符的示例：

         - Role name: made_up_role
         - Prefix: mur

         ```
         mur_var1: value_one
         ```

         4字符的示例:

         - Role name: totally_made_up_role
         - Prefix: tmur

         ```
         tmur_var1: value_one
         ```

         **角色名称中有两个(或少于两个)单词**

         编一个有意义的前缀。
          1 单词的示例:

         - Role name: ansible
         - Prefix: ans

         ```
         ans_var1: value_one
         ```

         2 单词的示例:

         - Role name: ansible_tower
         - Prefix: tow

         ```
         tow_var1: value_one
         ```

         **角色名称前缀冲突**

         ```yaml
         - hosts: localhost
           roles:
           - { role: made_up_role, mur_var1: val1 }
           - { role: my_uber_role, mur_var1: val2 }
         ```

         即使两个角色都具有相同的前缀（mur），并且即使两个角色都有一个名为mur_var1的变量，因为 **角色变量被限制在角色本身**，这两个变量也永远不会存在于各自的角色之外。意味着这不是问题。

         仅当my_uber_role取决于made_up_role时才有问题，反之亦然。 或者，如果这两个角色中的任何一个都包含另一个角色。

         当然，这是一个极不可能发生的极端情况。 如果是这样，请另当处理。

### 使用git

每个分享的playbook都需要有一致的目录结构，并且使用git仓库存储记录每一次提交。

```
site.yml                  # 主要的playbook，可以调用其他playbook
webservers.yml            # webserver使用的 playbook
deployonce.yml            # 适用于一次性部署的 playbook
inventories/
    production/           # 通过不同环境来区分主机清单      
        hosts             # 生产服务器的主机清单文件
        group_vars/       
        host_vars/   
    london/               # 其他的分组主机清单
roles/    
    requirements.yml      # 依赖的其他角色   
    common/               # 基本配置 
    webtier/              # 用于特定功能的角色
```

###  inventory 

**使用别名给主机节点起一个有意义的名字**

| 主机                                                         | 有意义的名称                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 10.1.2.75<br/>10.1.5.45<br/>10.1.4.5<br/>10.1.0.40           | db1 ansible_host=10.1.2.75<br />db2 ansible_host=10.1.5.45<br/>db3 ansible_host=10.1.4.5<br/>db4 ansible_host=10.1.0.40 |
| w14301.acme.com<br/>w17802.acme.com<br/>w19203.acme.com<br/>w19304.acme.com | web1 ansible_host=w14301.acme.com<br/>web2 ansible_host=w17802.acme.com<br/>web3 ansible_host=w19203.acme.com<br/>web4 ansible_host=w19203.acme.com |

**给主机分配不同用途的组，以便于不同情况下的批量使用**

```ini
# 按服务类型
[db]
db[1:4]

[web]
web[1:4]

# 按环境
[dev]
db1
web1

[testing]
db3
web3

[prod]
db2
web2
db4
web4

# 按区域
[east]
db1
web1
db3
web3

[west]
db2
web2
db4
web4
```

**尽可能使用动态源。要么作为单一来源，要么让Ansible统一多个来源**

- 自动保持清单同步
- 减少人为的错误
- 变化发生时没有延迟
- 让其他人管理主机清单

### 变量

合适的变量名可以使playbook更具可读性，并避免变量名冲突。

```yaml
# 看不懂的变量名称
a: 25
data: ab
data2: abc
id: 123

# 一眼就能看懂的变量用途
apache_max_keepalive: 25
apache_port: 80
tomcat_port: 8080
```

通过将角色名作为前缀添加到变量中来避免冲突和混淆。

```yaml
apache_max_keepalive: 25
apache_port: 80
tomcat_port: 8080
```

 为变量设置在合适的位置

- 根据变量的设置，修改地点和时间，为变量找到合适的位置

- 将逻辑(任务)与变量分离，减少重复模式

- 不要利用每一种可能性来存储变量- 将其固定到一个已定义的方案中，并尽可能减少存储位置


### playbook

**使用YAML语法**

```yaml
- name: install telegraf
  yum: name=telegraf-{{ telegraf_version }} state=present update_cache=yes enablerepo=telegraf
  notify: restart telegraf
  
- name: start telegraf
  service: name=telegraf state=started
```

上面的方式是不可取的，需要使用`KEY:VALUE`的形式

```yaml
- name: install telegraf
  yum:
    name: "telegraf-{{ telegraf_version }}"
    state: present
    update_cache: yes
    enablerepo: telegraf
    notify: restart telegraf
      
- name: start telegraf  
  service:    
    name: telegraf
    state: started
```

**不要忽略任务名**

```yaml
- hosts: web
  name: installs and starts apache
  
  tasks:
   - name: install apache packages
     yum:
       name: httpd
       state: latest
       
   - name: starts apache service
     service:
       name: httpd        
       enabled: yes
```

为每个任务指定`name`,可以友好的输出执行信息

```bash
PLAY [install and starts apache] ********************************
TASK [setup] ********************************
ok: [web1]
TASK [install apache packages] ********************************
ok: [web1]
TASK [starts apache service] ********************************
ok: [web1]
```

### 使用block

block可以帮助组织代码，还可以启用回滚或输出数据以进行关键性更改。

```yaml
- block:
    copy:
      src: critical.conf
      dest: /etc/critical/crit.conf
    service:
      name: critical
      state: restarted
  rescue:
    command: shutdown -h now
```

## 如何执行

### 调试执行

Ansible为命令行交互和故障排除提供多个选项

- `-vvvv` 打印debug信息
- `--setp` 一步一步的执行
- `--check` 执行检查，并不修改目标
- `--diff` 对比执行结果
- `--start-at-task` 从哪一个任务开始执行

### 分析运行的内容

Ansible 提供了许多选项来显示你将要运行的内容

- ` --list-tasks ` 列出运行的任务
- ` --list-tags` 列出运行的tag
- `--list-hosts` 列出运行的主机
- `--syntax-check` 执行语法检测

### 无主机清单的快速启动

如果需要对一些没有在主机清单中定义的主机，可以使用以下命令快速启动

- 单次任务

    ```bash
    ansible all -i neon.qxyz.de, -m service -a "name=redhat state=present"
    ```

- 执行playbook

  ```bash
  ansible-playbook -i neon.qxyz.de,neon2.qxyz.de site.yml
  ```

> 注意，单个主机要有`,`结尾

### 使用正确的工具

**对于服务，不能只启动，还需要测试**

```yaml
- name: start myapp
  service:
    name: myapp
    state: started
    
- name: check for proper response
  uri:
    url: http://localhost/myapp
    return_content: yes
    register: result
    until: '"Hello World" in result.content'
    retries: 10
    delay: 1
```

**尽量避免使用命令模块-始终先查找对应的模块**

| 系统命令                                                     | 模块                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| - name: add user<br />  command: useradd appuser             | \- name: add user<br />  user: <br />      name: appuser<br />      state: present |
| \- name: install apache<br />  command: yum install httpd    | \- name: install apache<br />   yum: <br />       name: httpd<br />       state: latest |
| - name: start apache<br />  shell: \|<br />    service httpd start && chkconfig httpd on | \- name: start apache<br />  service:<br />      name: httpd<br />      state: started<br />      enabled: yes |

**标记更改过的文件**

如果未标记更改过的文件，则可能会意外覆盖它们

- 将模板输出文件标记为由Ansible生成
- 使用`ansible_managed**`变量和注释过滤器
    ```jinja2
    {{ ansible_managed | comment }}
    ```



###  使用ROLES 和  Galaxy  

**尽可能使用角色**， 角色可以让你您能够封装您的操作。

- 像playbook一样——让角色专注于目标和功能
- 将每个角色存储在专用的Git仓库中
-  通过`role/requirements.yml`文件包含角色，通过`ansible-galaxy`工具导入
- 限制角色的依赖性

**从`galaxy`获取角色，但是要小心，并根据自己的需要使用它们**

- galaxy  提供了数以千计的角色 
- 角色的质量差异很大
- 一定要半信半疑地接受建议 
- 选择可信或知名的作者



###  正确访问目标



在可能的情况下，root访问比sudo - use sudo更难跟踪

- Ansible只能以root身份运行
- 但是由于登录和安全的原因，通常要求非root访问
- 使用`become`提权方法-所以Ansible脚本是通过sudo执行(sudo很容易跟踪)
- 最好的:创建一个Ansible专属用户
- 不要试图将sudo权限限制在某些命令中——那样可能导致Ansible不能工作



### 调试问题

**检查目标计算机上的日志**

在`/var/log/message`中存在下列的日志信息

```
ansible-node sshd[2395]: pam_unix(sshd:session): session  opened for user liquidat by (uid=0)
ansible-node ansible-yum[2399]: Invoked with name=['httpd']  list=None install_repoquery=True conf_file=None  disable_gpg_check=False state=absent disablerepo=None  update_cache=False enablerepo=None exclude=None
```

**保留代码在目标机器上执行**

使用`ANSIBLE_KEEP_REMOTE_FILES` 环境变量，可以使ansible不删除在目标节点的代码

```bash
ANSIBLE_KEEP_REMOTE_FILES=1 ansible target-node -m yum -a "name=httpd state=absent"
```

通常代码存在远端执行用户的家目录`.ansible/tmp`目录下，使用下列命令可以再次执行

```
$ /bin/sh -c 'sudo -u $SUDO_USER /bin/sh -c "/usr/bin/python /home/user/.ansible/tmp/..."
```

**使用调试模块**

可以使用`debug`模块在playbook中输出一些调试信息

```yaml
- name: Output debug message
  debug:
    msg: "This always displays"

- name: Output debug message
  debug:
    msg: "This only displays with ansible-playbook -vv+"
    verbosity: 2
    
- name: Output debug hostvars
  debug:
    var: hostvars
```

## 如何在生产中使用

### 使用Tower

- Tower是Ansible开发的
- 可以扩展Ansible的限制以满足企业需求，比如可扩展性，API，RBAC，主机等
- Tower通过**问号提示**提供程序内帮助，包括例子或链接到进一步的文档
- Tower可以使用不同的分支多次导入存储库
- 在项目更新期间，Tower自动导入角色
- Tower可以使用动态和智能库存清单，可以合并多个库存清单，并负责同步和缓存
- Tower给job模板提供了很多选项，比如添加标签，检查模板，执行后通知功能等
- Tower可以使多个剧本组合成一个工作流程 
- Tower提供多租户功能，来帮助团队分隔工作环境。
- Tower提供的凭证只能由Tower使用，保证了安全性。
- Tower可以在作业成功、失败或总是失败时发送通知—例如邮件、IRC、web hook等等
- 可以将所有的日志从Tower发送到日志处理中心Splunk, Loggly, ELK, REST等
- Tower可以很容易的建立HA架构，也可以在网络隔离的地方建立单点。 

### 使用Ansible

- 保证ansible管理节点的安全性
- 记录ansible的执行日志
- 使用git仓库来管理ansible的playbook，roles，inventory等等
- 使用block块来推送执行成功，失败的通知