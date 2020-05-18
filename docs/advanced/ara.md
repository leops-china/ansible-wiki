# 使用 ARA 记录 Ansible 执行结果

[ARA](https://github.com/ansible-community/ara) 通过使用 Ansible [callback plugin](https://docs.ansible.com/ansible/latest/plugins/callback.html) 将 Ansible playbook 执行结果保存到本地或远程数据库。

该回调插件利用内置的python API客户端将数据发送到REST API服务器，该服务器上的数据和指标可用于查询，浏览，监视或集成在其他工具和界面中。

![](/images/advanced/ara/ara-recording-workflow.png)

更多介绍见 [ ARA 文档](https://ara.readthedocs.io/en/latest/)



## 安装

安装ansible

```bash
yum -y install python36 python36-pip
pip3.6 install ansible -i https://mirrors.aliyun.com/pypi/simple
```

安装 ara server

```bash
pip3 install Django==2.1.15 -i https://mirrors.aliyun.com/pypi/simple
pip3 install "ara[server]" -i https://mirrors.aliyun.com/pypi/simple
```

版本信息

```bash
# cat /etc/centos-release
CentOS Linux release 7.6.1810 (Core) 

# python -V
Python 2.7.5

# ansible --version
ansible 2.9.9
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.6/site-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 3.6.8 (default, Apr  2 2020, 13:34:55) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
 
# ara-manage version
[ara] Using settings file: /root/.ara/server/settings.yaml
2.1.15
```



## 配置

### 配置插件

在`ansible.cfg`中配置ara插件地址

```bash
# mkdir /etc/ansible
# python3 -m ara.setup.ansible > /etc/ansible/ansible.cfg

# cat /etc/ansible/ansible.cfg
[defaults]
callback_plugins=/usr/local/lib/python3.6/site-packages/ara/plugins/callback
action_plugins=/usr/local/lib/python3.6/site-packages/ara/plugins/action
lookup_plugins=/usr/local/lib/python3.6/site-packages/ara/plugins/lookup
```

也可以使用环境变量

```bash
# python3 -m ara.setup.env
export ANSIBLE_CALLBACK_PLUGINS=${ANSIBLE_CALLBACK_PLUGINS:-}${ANSIBLE_CALLBACK_PLUGINS+:}/usr/local/lib/python3.6/site-packages/ara/plugins/callback
export ANSIBLE_ACTION_PLUGINS=${ANSIBLE_ACTION_PLUGINS:-}${ANSIBLE_ACTION_PLUGINS+:}/usr/local/lib/python3.6/site-packages/ara/plugins/action
export ANSIBLE_LOOKUP_PLUGINS=${ANSIBLE_LOOKUP_PLUGINS:-}${ANSIBLE_LOOKUP_PLUGINS+:}/usr/local/lib/python3.6/site-packages/ara/plugins/lookup
```



在`ansible.cfg`中配置ara插件参数

```bash
[ara]
api_client = http
api_server = http://192.168.77.130:9191
default_labels = dev,test
```

### 配置系统服务

```bash
useradd ansible

cat << EOF > /etc/systemd/system/ara.service
[Unit]
Description=ara
After=network.target

[Service]
Type=simple
User=ansible
Group=ansible
TimeoutStartSec=0
Restart=on-failure
RestartSec=10
RemainAfterExit=yes
ExecStart=/usr/local/bin/ara-manage runserver 0.0.0.0:9191
Environment="ARA_ALLOWED_HOSTS=['*']"

[Install]
WantedBy=multi-user.target
EOF

systemctl daemon-reload
systemctl enable --now ara
```

### 生成表

默认使用sqlite作为数据库

```bash
runuser -s /bin/bash ansible -c "ara-manage makemigrations; ara-manage migrate"
```







## 执行 Playbook

playbook

```bash
---
- hosts: localhost
  tasks:
   - ping:
   - name: Record different things
     ara_record:
       key: "{{ item.key }}"
       value: "{{ item.value }}"
       type: "{{ item.type }}"
     loop:
       - { key: "log", value: "error", type: "text" }
       - { key: "website", value: "http://domain.tld", type: "url" }
```

运行

```bash
# ansible-playbook test.yml

PLAY [localhost] *******************************************************************************************************************************************

TASK [Gathering Facts] *************************************************************************************
ok: [localhost]

TASK [ping] *************************************************************************************
ok: [localhost]

TASK [Record different things] *************************************************************************************
changed: [localhost] => (item={'key': 'log', 'value': 'error', 'type': 'text'})
changed: [localhost] => (item={'key': 'website', 'value': 'http://domain.tld', 'type': 'url'})

PLAY RECAP *************************************************************************************
localhost                  : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```

打开ara web `http://192.168.77.130:9191` 页面就能看到执行的playbook

![](/images/advanced/ara/ara01.png)

点击进去，就能看到详细信息

![](/images/advanced/ara/ara02.png)



## 执行 ad-hoc

```bash
export ANSIBLE_LOAD_CALLBACK_PLUGINS=1

ansible localhost -m ping
```

记录ad-hoc的信息

![](/images/advanced/ara/ara03.png)

