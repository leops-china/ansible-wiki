# Ansible Tower

[Ansible Tower](https://www.ansible.com/products/tower) 是一个由Red Hat赞助的开源社区项目，它使用户能够更好地控制他们的Ansible项目在IT环境中的使用。Ansible Tower提供基于角色的访问控制，包括对SSH和其他服务使用安全存储的凭证的控制。你可以同步你的Ansible Tower库存与各种各样的云资源，和强大的多剧本工作流允许你建模复杂的过程。使用python语言编写。



## 安装

### 系统要求

- RHEL 7, CentOS 7或更高版本，并且是64位操作系统。
- 系统资源最少2个CPU，4GB RAM。
- /var 分区最小 10GB、IOPS最小为750, 用于存储Tower文件和工作目录。
- 数据库存储目录最少位 20GB、IOPS最少应为1000，用于存储pgsql的数据。
- Ansible Tower 3.6及以上版本才支持 PostgreSQL 10。
- Ansible Tower 3.2及以上版本需要最低 ansible 2.2的版本。

!!! note
	从Tower 3.6 版本之上不再支持ubuntu系统。


### 系统环境

```bash
# cat /etc/centos-release
CentOS Linux release 7.6.1810 (Core) 
# python -V
Python 2.7.5
```

### 下载包

下载`el7`标志的包，代表是centos 7系列系统使用的包

```bash
wget https://releases.ansible.com/ansible-tower/setup-bundle/ansible-tower-setup-bundle-3.6.4-1.el7.tar.gz
tar zxf ansible-tower-setup-bundle-3.6.4-1.el7.tar.gz
cd ansible-tower-setup-bundle-3.6.4-1
```

### 配置 Tower 主机清单

> 本次使用单实例的方式安装tower

在 `inventory` 文件中配置密码信息

```ini hl_lines="7,12,15"
[tower]
localhost ansible_connection=local

[database]

[all:vars]
admin_password='admin'

pg_host=''
pg_port=''

pg_database='awx'
pg_username='awx'
pg_password='awx'
pg_sslmode='prefer'  # set to 'verify-full' for client-side enforced SSL

rabbitmq_username=tower
rabbitmq_password='awx'
rabbitmq_cookie=cookiemonster
```

### 安装 Tower

安装依赖

```bash
yum -y install rsync
```

执行 `setup.sh` 脚本进行安装 Tower。

```bash
./setup.sh
```

等待一段时间后，安装即可完成，安装的日志会存放`/var/log/tower/setup-[安装时间].log` 文件中。

访问节点`80`端口即可访问 tower web页面

## Tower 使用

访问 `https://192.168.77.130` 地址，使用账号密码(`admin/admin`)登录 Tower

![login](/images/ui/tower/login.png)

登录后，需要进行申请许可。

![license](/images/ui/tower/license.png)

!!! note
	这里分享网友一个许可，大家切勿在生产中使用，仅供测试学习Tower。
	```json
	{
		"company_name": "VzerZhang", 
		"contact_email": "vzer.zhang@gmail.com", 
		"contact_name": "zhang vzer", 
		"hostname": "cd82342fe4d840dc89437f1a2aa54934", 
		"instance_count": 1000, 
		"license_date": 2121936571, 
		"license_key": "059aa45908d9989056a212c944781ca398df23ca86d7565f9949c243d64a75f1", 
		"license_type": "enterprise", 
		"subscription_name": "Ansible Tower by Red Hat, Standard (1000 Managed Nodes)"
	}
	```
	
确认好许可，就能进入 Tower 了。

![tower](/images/ui/tower/tower.png)

Tower 页面 跟 awx 基本上一致，操作请看 awx [使用文档](/ui/awx/#awx_2)
