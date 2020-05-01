# 在 Jenkins 中使用 Ansible

在 Jenkins 中使用 Ansible 命令，有两种方式：

1. 使用 `shell` 执行ansible命令
2. 使用 `ansible` 插件执行ansible命令

本节将介绍 `ansible` 插件的使用方法

## 节点操作

> 以 centos7 系统为例

**安装 jenkins**

```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
yum install -y java-1.8.0-openjdk jenkins
systemctl enable jenkins
systemctl start jenkins
```

**安装 ansible**

```bash
yum -y install ansible
```

配置 ansible

```ini
#　/etc/ansible/ansible.cfg

[defaults]
# Set the log_path
log_path = ~/ansible.log

# Additional default options for Ansible
forks = 20
host_key_checking = False
retry_files_enabled = False
retry_files_save_path = ~/ansible-installer-retries
nocows = True
remote_user = root
roles_path = /etc/ansible/roles/
gathering = smart
fact_caching = jsonfile
fact_caching_connection = $HOME/ansible/facts
fact_caching_timeout = 600
callback_whitelist = profile_tasks
inventory_ignore_extensions = secrets.py, .pyc, .cfg, .crt, .ini
# work around privilege escalation timeouts in ansible:
timeout = 30

# Uncomment to use the provided example inventory
#inventory = inventory/hosts.example

[inventory]
# fail more helpfully when the inventory file does not parse (Ansible 2.4+)
unparsed_is_failed=true

# Additional ssh options for OpenShift Ansible
[ssh_connection]
retries = 15
pipelining = True
ssh_args = -o ControlMaster=auto -o ControlPersist=600s
timeout = 10
# shorten the ControlPath which is often too long; when it is,
# ssh connection reuse silently fails, making everything slower.
control_path = %(directory)s/%%h-%%r
```

## Jenkins 操作

1. 获取初始密码
   
    ```bash
    # cat /var/lib/jenkins/secrets/initialAdminPassword 
    b3da24e53afd46b9962aebd6b8409d6d
    ```

2. 访问WEB页面` http://192.168.77.131:8080/ `,输入初始密码后，安装常用插件。
    ![png](/images/advanced/jenkins/01.png)

3. 安装完成后，进入jenkins管理界面，安装ansible插件

    在 "Manage Jenkins" => "Manage Plugins" ==> "可选插件" 界面，输入`ansible`筛选插件，选中`Ansible`插件后，直接安装即可。
    ![png](/images/advanced/jenkins/02.png)
4. 设置ansible工具

    在 "Manage Jenkins" =>  "Global Tool Configuration" => "Ansible" 选项中，设置ansible的执行路径
    ![png](/images/advanced/jenkins/03.png)
    
    > 不设置的话，会选取系统的可执行路径



## Ansible 任务

### 执行 ad-hoc

1. 创建一个freestyle类型的任务

2. 在任务中的构建阶段，选择使用` Invoke Ansible Ad-Hoc Command ` 
    ![png](/images/advanced/jenkins/04.png)
    
3. 设置完后，运行任务即可。
   
    ```
    Started by user admin
    Running as SYSTEM
    Building in workspace /var/lib/jenkins/workspace/test_ansible
    [test_ansible] $ /usr/bin/ansible all -i /tmp/inventory1167656924170839709.ini -m ping -f 5
    192.168.77.131 | SUCCESS => {
       "changed": false, 
       "ping": "pong"
    }
    Finished: SUCCESS
    ```

    > 颜色输出需要安装 [AnsiColor](https://plugins.jenkins.io/ansicolor)  插件显示，并在任务中选中"Color ANSI Console Output"选项，以便开启颜色输出

    !!! note
        注意: 此时运行ansible命令的用户是 **jenkins运行用户**。

### 执行 playbook

1. 创建一个freestyle类型的任务

2. 在任务中的构建阶段，选择使用` Invoke Ansible Playbook ` 
   
    ![png](/images/advanced/jenkins/05.png)

    ```
    # /etc/ansible/hosts
    192.168.77.131 ansible_ssh_user=root ansible_ssh_pass=123456

    # /etc/ansible/test.yml
    ---

    - hosts: 192.168.77.131
     gather_facts: no
     tasks:
       - name: ping
         ping:
       - name: Jenkins Environment Variables
         debug: 
           msg: "{{ lookup('env','BUILD_TAG') }}"
    ```

3. 设置完后，运行任务即可。

    ```
    Started by user admin
    Running as SYSTEM
    Building in workspace /var/lib/jenkins/workspace/ansible_playbook
    [ansible_playbook] $ /usr/bin/ansible-playbook /etc/ansible/test.yml -i /etc/ansible/hosts -l all -f 5

    PLAY [192.168.77.131] **********************************************************

    TASK [ping] ********************************************************************
    Monday 20 April 2020  18:16:35 +0800 (0:00:00.055)       0:00:00.055 ********** 
    ok: [192.168.77.131]

    TASK [Jenkins Environment Variables] *******************************************
    Monday 20 April 2020  18:16:36 +0800 (0:00:00.740)       0:00:00.796 ********** 
    ok: [192.168.77.131] => {
       "msg": "jenkins-ansible_playbook-1"
    }

    PLAY RECAP *********************************************************************
    192.168.77.131             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

    Monday 20 April 2020  18:16:36 +0800 (0:00:00.184)       0:00:00.980 ********** 
    =============================================================================== 
    ping -------------------------------------------------------------------- 0.74s
    Jenkins Environment Variables ------------------------------------------- 0.18s
    Finished: SUCCESS
    ```

4. Pipeline 使用

    ```
    pipeline {
       agent any

       stages {
           stage('build') {
               steps {
                   sh 'touch .ansible'
                   ansiColor('xterm') {
                       ansiblePlaybook(
                           installation: 'Ansible',
                           playbook: '/etc/ansible/test.yml',
                           inventory: '/etc/ansible/hosts', 
                           limit: 'all',
                           forks: 5,
                           becomeUser: null,
                           sudoUser: null,
                           colorized: true)
                   }
               }
           }
       }
    }
    ```
	> `sh 'touch .ansible'`  是为了让job创建工作空间，如果没有文件变动的话，job是不创建工作空间的。

    job输出
    ```
    Started by user admin
    Running in Durability level: MAX_SURVIVABILITY
    [Pipeline] Start of Pipeline
    [Pipeline] node
    Running on Jenkins in /var/lib/jenkins/workspace/ansible_pipe
    [Pipeline] {
    [Pipeline] stage
    [Pipeline] { (build)
    [Pipeline] sh
    + touch .ansible
    [Pipeline] ansiColor
    [Pipeline] {
    [Pipeline] ansiblePlaybook
    [ansible_pipe] $ /usr/bin/ansible-playbook /etc/ansible/test.yml -i /etc/ansible/hosts -l all -f 1
    PLAY [192.168.77.131] **********************************************************

    TASK [ping] ********************************************************************
    Monday 20 April 2020  18:25:49 +0800 (0:00:00.041)       0:00:00.041 ********** 
    ok: [192.168.77.131]

    TASK [Jenkins Environment Variables] *******************************************
    Monday 20 April 2020  18:25:50 +0800 (0:00:01.036)       0:00:01.078 ********** 
    ok: [192.168.77.131] => {
       "msg": "jenkins-ansible_pipe-5"
    }

    PLAY RECAP *********************************************************************
    192.168.77.131             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

    Monday 20 April 2020  18:25:50 +0800 (0:00:00.057)       0:00:01.136 ********** 
    =============================================================================== 
    ping -------------------------------------------------------------------- 1.04s
    Jenkins Environment Variables ------------------------------------------- 0.06s
    [Pipeline] }
    [Pipeline] // ansiColor
    [Pipeline] }
    [Pipeline] // stage
    [Pipeline] }
    [Pipeline] // node
    [Pipeline] End of Pipeline
    Finished: SUCCESS
    ```
