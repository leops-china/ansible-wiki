# AWX

AWX 是一个开源社区项目，提供用于管理 Ansible 项目的软件。AWX 托管在 GitHub 上，并提供基于 Web 的用户界面、REST API 和适用于 Ansible 的任务引擎。

Ansible 是一款开发运营工具，可自动执行预置、配置管理、应用程序部署、内部服务编排、持续交付和许多其他 IT 流程。直观的 AWX 控制面板让您能够安排和部署 Ansible Playbook，并提供集中的日志记录、审计和系统跟踪。AWX 可提供 Ansible Tower 的源代码，Ansible Tower 是 AWX 的商业版本。

此快速入门从 [AWX 的 GitHub 存储库](https://github.com/ansible/awx) 的主分支部署代码。您还可以选择从该存储库的其他分支部署代码。 


## Awx install

### 系统环境

- OS: centos 7.7 x64
- IP: 192.168.77.130

### 安装依赖

```bash
yum -y install git gcc gcc-c++ ansible nodejs gettext device-mapper-persistent-data lvm2 bzip2 python-pip python-devel
```

### 安装docker环境

```bash
curl -o /etc/yum.repos.d/docker-ce.repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
sed -i 's#download.docker.com#mirrors.ustc.edu.cn/docker-ce#g' /etc/yum.repos.d/docker-ce.repo

yum -y install docker-ce bash-completion

pip install docker-compose -r http://mirrors.aliyun.com/pypi/simple
curl -L https://raw.githubusercontent.com/docker/compose/master/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose


cp /usr/share/bash-completion/completions/docker /etc/bash_completion.d/
mkdir  /etc/docker
cat > /etc/docker/daemon.json <<EOF
{
    "log-driver": "json-file",
    "log-opts": {
        "max-size": "100m",
        "max-file": "3"
    },
    "default-ulimits": {
        "nofile": {
             "Name": "nofile",
             "Hard": 64000,
             "Soft": 64000
         }
    },
    "live-restore": true,
    "max-concurrent-downloads": 10,
    "max-concurrent-uploads": 10,
    "storage-driver": "overlay2",
    "storage-opts": [
        "overlay2.override_kernel_check=true"
    ],
    "registry-mirrors": [
        "http://hub-mirror.c.163.com"
    ]
}
EOF

systemctl enable --now docker

```

版本信息
```bash
# python -V
Python 2.7.5          

# docker version
'Client:
 Version:           18.09.6
 API version:       1.39
 Go version:        go1.10.8
 Git commit:        481bc77156
 Built:             Sat May  4 02:34:58 2019
 OS/Arch:           linux/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          19.03.8
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.12.17
  Git commit:       afacb8b
  Built:            Wed Mar 11 01:25:42 2020
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.2.5
  GitCommit:        bb71b10fd8f58240ca47fbb579b9d1028eea7c84
 runc:
  Version:          1.0.0-rc6+dev
  GitCommit:        2b18fe1d885ee5083ef9f0838fee39b62d653e30
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683

# docker-compose version
docker-compose version 1.25.5, build unknown
docker-py version: 4.2.0
CPython version: 2.7.5
OpenSSL version: OpenSSL 1.0.2k-fips  26 Jan 2017
```

### 安装 awx

```bash
# wget https://github.com/ansible/awx/archive/11.2.0.tar.gz
# tar zxf 11.2.0.tar.gz
# cd awx-11.2.0/
```

生成加密主机清单文件的密钥

```bash
# openssl rand -base64 30
nir4yYx6Bb4uN/ow98f2tD9Wktm8A/cwgqTgzHLg
```

配置主机清单文件 `installer/inventory`
```ini
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/env python3"

[all:vars]
dockerhub_base=ansible
docker_compose_dir="~/.awx/awxcompose"

awx_task_hostname=awx
awx_web_hostname=awxweb


host_port=80
host_port_ssl=443

pg_username=awx
pg_password=awxpass
pg_database=awx
pg_port=5432
postgres_data_dir="~/.awx/pgdocker"

admin_user=admin
admin_password=password
create_preload_data=True

secret_key=nir4yYx6Bb4uN/ow98f2tD9Wktm8A/cwgqTgzHLg
awx_alternate_dns_servers="8.8.8.8,8.8.4.4"
project_data_dir="~/.awx/projects"
```

执行安装 plyabook

```bash
# cd installer

# ansible-playbook -i inventory install.yml 

PLAY [Build and deploy AWX] ******************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************
ok: [localhost]

TASK [check_vars : include_tasks] ************************************************************************************
included: /root/awx-11.2.0/installer/roles/check_vars/tasks/check_docker.yml for localhost

TASK [check_vars : postgres_data_dir should be defined] **************************************************************
ok: [localhost] => {
    "changed": false, 
    "msg": "All assertions passed"
}

TASK [check_vars : host_port should be defined] **********************************************************************
ok: [localhost] => {
    "changed": false, 
    "msg": "All assertions passed"
}

TASK [local_docker : Generate broadcast websocket secret] ************************************************************
ok: [localhost]

TASK [local_docker : Check for existing Postgres data] ***************************************************************
ok: [localhost]

TASK [local_docker : Determine whether to upgrade postgres] **********************************************************
ok: [localhost]

TASK [local_docker : Remove old data directory] **********************************************************************
ok: [localhost]

TASK [local_docker : Set DockerHub Image Paths] **********************************************************************
ok: [localhost]

TASK [local_docker : Create ~/.awx/awxcompose directory] *************************************************************
changed: [localhost]

TASK [local_docker : Create Redis socket directory] ******************************************************************
changed: [localhost]

TASK [local_docker : Create Memcached socket directory] **************************************************************
changed: [localhost]

TASK [local_docker : Create Docker Compose Configuration] ************************************************************
changed: [localhost] => (item=environment.sh)
changed: [localhost] => (item=credentials.py)
changed: [localhost] => (item=docker-compose.yml)
changed: [localhost] => (item=nginx.conf)
changed: [localhost] => (item=redis.conf)

TASK [local_docker : Set redis config to other group readable to satisfy redis-server] ********************************
changed: [localhost]

TASK [local_docker : Render SECRET_KEY file] **************************************************************************
ok: [localhost]

TASK [local_docker : Start the containers] ****************************************************************************
changed: [localhost]

TASK [local_docker : Update CA trust in awx_web container] ************************************************************
changed: [localhost]

TASK [local_docker : Update CA trust in awx_task container] ***********************************************************
changed: [localhost]

PLAY RECAP ************************************************************************************************************
localhost                  : ok=18   changed=5    unreachable=0    failed=0    skipped=97   rescued=0    ignored=0   
```

启动的容器
```bash
# docker ps
CONTAINER ID        IMAGE                     COMMAND                  CREATED              STATUS              PORTS                  NAMES
df5f7cb15da0        ansible/awx_task:11.2.0   "tini -- /bin/sh -c …"   About a minute ago   Up About a minute   8052/tcp               awx_task
5b774471f6e3        ansible/awx_web:11.2.0    "tini -- /bin/sh -c …"   About a minute ago   Up About a minute   0.0.0.0:80->8052/tcp   awx_web
ad4c005ac0e9        memcached:alpine          "docker-entrypoint.s…"   About a minute ago   Up About a minute   11211/tcp              awx_memcached
f73edd420c15        postgres:10               "docker-entrypoint.s…"   About a minute ago   Up About a minute   5432/tcp               awx_postgres
c006d3e473bd        redis                     "docker-entrypoint.s…"   About a minute ago   Up About a minute   6379/tcp               awx_redis
```

### WEB 界面

访问地址 `http://192.168.77.130`

![awx-login.png](/images/ui/awx/awx-login.png)

输入用户名和密码登录后，就能看到awx的界面了。
![awx01.png](/images/ui/awx/awx01.png)

## Awx 使用


### 添加主机

在 **"资源"** >> **"清单"** 页面中点击右边的 **"+"** 添加清单

![inventory01.png](/images/ui/awx/inventory01.png)

保存之后，点击清单里的 **"主机"** 添加主机信息

![inventory02.png](/images/ui/awx/inventory02.png)

如果说不设置账号密码, 可以添加下 **凭证**，并在模板中选择凭证即可。

![inventory03.png](/images/ui/awx/inventory03.png)


### 添加项目

项目用于管理playbook存放位置，可以存在`本地`，`git仓库`，`svn仓库`等版本工具中。

本次在 `本地` 创建一个示例项目。

首先，在本地项目路径下创建一个`example-playbooks`目录，在目录中创建`helloWorld.yml` playbook

```bash
mkdir -p ~/.awx/projects/example-playbooks

cat <<EOF >>.awx/projects/example-playbooks/
---

- hosts: all
  tasks:
    - name: hello
      debug: msg="hello,world"
EOF
```

然后，在web页面中，在 **"项目"** 创建一个示例项目。
![program1.png](/images/ui/awx/program1.png)


### 添加模板

在awx中，模板即是对playbook的引用。执行模板，就是执行playbook。

在示例项目中，添加一个任务模板。

![template1.png](/images/ui/awx/template1.png)

在模板中，启动任务

![template2.png](/images/ui/awx/template2.png)

任务执行完，就能看到执行的详细信息

![template3.png](/images/ui/awx/template3.png)

### 运行命令

在 **"清单"** >> **"示例清单"** >> **"主机"** 中 选择要执行的主机，点击 **"运行命令"**

![ad-hoc1.png](/images/ui/awx/ad-hoc1.png)

在 **"运行命令"** 界面设置运行的参数

![ad-hoc2.png](/images/ui/awx/ad-hoc2.png)

执行完，就能看到执行的详细信息

![ad-hoc3.png](/images/ui/awx/ad-hoc3.png)



### AWX配置LDAP
这里以Windows AD为例

详细用法可以参考[官方tower文档](https://docs.ansible.com/ansible-tower/latest/html/administration/ldap_auth.html)

设置流程参考:

![ldap-1.png](/images/ui/awx/ldap-1.png)

![ldap-2.png](/images/ui/awx/ldap-2.png)

![ldap-3.png](/images/ui/awx/ldap-3.png)

具体报错信息可以查看 `docker logs -f awx_web`