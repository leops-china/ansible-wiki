# 3. 快速开始


跟着我，一步一步的开始 ansible 神奇之旅吧！

## 环境信息

control os:  `centos 7.7`

ansible version: `2.9.6`

## 任务

我们将要在目标主机上安装部署`nginx`服务

## 步骤

### 0. 安装ansible

> 本次使用的是 `Centos 7.7 x64` 系统

```bash
yum install -y epel-release
sed -e 's!^mirrorlist=!#mirrorlist=!g' \
        -e 's!^metalink=!#metalink=!g' \
    -e 's!^#baseurl=!baseurl=!g' \
    -e 's!//download\.fedoraproject\.org/pub!//mirrors.ustc.edu.cn!g' \
    -e 's!http://mirrors\.ustc!https://mirrors.ustc!g' \
    -i /etc/yum.repos.d/epel.repo /etc/yum.repos.d/epel-testing.repo
yum install -y ansible
yum update python-jinja2

```

### 1. 定义主机清单

> 定义一个简单的通过ssh认证的主机清单，更多配置见

```
cat /etc/ansible/hosts

192.168.77.135 ansible_ssh_user=root ansible_ssh_pass=123456
```

主机清单中的配置含义

- `192.168.77.135`  定义远程主机ip地址
- `ansible_ssh_user` 连接远程主机的用户
- `ansible_ssh_pass` 连接远程主机的用户密码

### 2. 执行ansible命令

**测试连接状态**

```bash
ansible 192.168.77.135 -m ping
```

命令中的含义
- `192.168.77.135`  用于匹配主机清单中的主机名称
- `-m ping` 指定 `ping` 模块，用于测试与远程主机的连接状态

**安装Nginx**

```bash
ansible 192.168.77.135 -m yum -a 'name=nginx'
```

命令中的含义
- `192.168.77.135`  用于匹配主机清单中的主机名称
- `-m yum` 指定 `yum` 模块，用于安装软件
- `-a 'name=nginx'` 指定模块的参数，`name`是软件的名称，默认操作是安装。

**启动Nginx**

```bash
ansible 192.168.77.135 -m systemd -a 'name=nginx state=started enabled=yes'
```

命令中的含义
- `192.168.77.135`  用于匹配主机清单中的主机名称
- `-m systemd` 指定 `systemd` 模块，用于管理系统服务
- `-a 'name=nginx state=started enabled=yes'` 指定模块的参数，`name`是软件的名称，`state` 指定管理状态，`enabled` 是否开启自启动。

### 3. 验证

```bash
curl http://192.168.77.135:8080

```

### 3. 执行ansible playbook

**定义 playbook**
> 也就是任务编排，将上面3个步骤合并在一起。

```bash
# File: install_nginx.yml

---
- hosts: 192.168.77.135
  tasks:
    - name: 安装 nginx.
      yum: name=nginx
    - name: 启动 nginx.
      systemd: name=nginx state=started enabled=yes
    - name: 检查 nginx.
      uri: url=http://127.0.0.1
      register: curl_result
      until: curl_result.status == 200
      retries: 5
      delay: 3
      changed_when: false
      check_mode: no

```

**执行 playbook**

```bash
ansible-playbook install_nginx.yml
```

恭喜你，你已经学会怎么使用ansible了。下面的课程会使你更加深入的了解 ansible 。

