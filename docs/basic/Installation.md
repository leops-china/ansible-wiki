# 2. 安装 Ansible

学会一个软件的第一件事，就是要在各种环境上安装这个软件，安装好，我们才能进入下一步，跟着我一起来安装 `ansible` 吧

!!! note "对管理主机的要求"
    目前,只要机器上安装了 Python 2（版本2.6或2.7）或Python 3（版本3.5及更高版本）都可以运行Ansible (windows系统不可以做管理主机)
    管理主机的系统可以是 Red Hat, Debian, CentOS, macOS, BSD的各种版本.

!!! note "对节点主机的要求"
    通常我们使用 ssh 与节点通信，默认使用 sftp.  如果 sftp 不可用，可在 ansible.cfg 配置文件中配置成 scp 的方式. 在节点上也需要安装Python 2（2.6或更高版本）或Python 3（3.5或更高版本）

    如果节点启用了`selinux`, 在使用`copy`/`file`/`template`时需要安装 `libselinux-python` 包。

    如果想通过ansible给节点主机安装python模块，可以使用`raw`模块，命令如: 

    ```bash
    ansible myhost --become -m raw -a "yum install -y python2"
    ```
     `raw` 模块 可以原生执行shell命令
    

## 在管理节点上安装ansible


> 大家选择下面的一种方式进行安装 `ansible`

``` bash tab="CentOS/RHEL"
sed -e 's!^#baseurl=!baseurl=!g' \
       -e  's!^mirrorlist=!#mirrorlist=!g' \
       -e 's!mirror.centos.org!mirrors.aliyun.com!g' \
       -i  /etc/yum.repos.d/CentOS-Base.repo

yum install -y epel-release

sed -e 's!^mirrorlist=!#mirrorlist=!g' \
    -e 's!^metalink=!#metalink=!g' \
    -e 's!^#baseurl=!baseurl=!g' \
    -e 's!//download\.fedoraproject\.org/pub!//mirrors.aliyun.com!g' \
    -e 's!http://mirrors\.aliyun!https://mirrors.aliyun!g' \
    -i /etc/yum.repos.d/epel.repo /etc/yum.repos.d/epel-testing.repo

yum install -y ansible
```

``` bash tab="Ubuntu"
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

``` bash tab="Debian"
deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
$ sudo apt update
$ sudo apt install ansible
```


``` bash tab="FreeBSD"
$ sudo pkg install py27-ansible
# or
$ sudo pkg install py36-ansible
```


``` bash tab="dnf"

$ sudo dnf install ansible
```

``` bash tab="mac"
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
sudo CFLAGS=-Qunused-arguments CPPFLAGS=-Qunused-arguments pip install ansible -i https://mirrors.ustc.edu.cn/pypi/web/simple
# 通过此方式安装的没有生成/etc/ansible文件，可以手动生成，配置文件示例到https://github.com/ansible/ansible/tree/devel/examples

```

``` bash tab="pip"
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
pip install ansible -i https://mirrors.ustc.edu.cn/pypi/web/simple

# 通过此方式安装的没有生成/etc/ansible文件，可以手动生成，配置文件示例到https://github.com/ansible/ansible/tree/devel/examples

```


``` bash tab="Python3"
yum install -y python36 python36-tools
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3.6 get-pip.py 
pip3.6 install ansible -i https://mirrors.ustc.edu.cn/pypi/web/simple
# 通过此方式安装的没有生成/etc/ansible文件，可以手动生成，配置文件示例到https://github.com/ansible/ansible/tree/devel/examples
```

``` bash tab="源码"
yum install -y  python-setuptools
easy_install pip
wget https://github.com/ansible/ansible/archive/v2.9.6.tar.gz
tar zxf v2.9.6.tar.gz
cd ./ansible-2.9.6
pip install -r ./requirements.txt
python setup.py install
mkdir /etc/ansible/
cp examples/{ansible.cfg,hosts} /etc/ansible/
```

``` bash tab="离线安装"
# 以目标主机centos7为测试
# 1. 下载ansible及依赖系统包
curl -sSL https://cdn.jsdelivr.net/gh/lework/script/shell/get_packages.sh | bash -s - centos7 ansible
# 2. 下载好的离线包在当前目录的package_centos7_ansible
ls package_centos7_ansible
# 3. 将目录拷贝到目标主机,在当前目录安装
yum localinstall *.rpm
```



## bash命令行自动补全

> 在Ansible 2.9之后，就支持了命令行参数补齐功能

``` bash tab="CentOS/RHEL"
yum install epel-release
yum install python-argcomplete
```

``` bash tab="apt"
$ sudo apt install python-argcomplete
```

``` bash tab="pip"
pip install argcomplete
```

**将补全加入环境变量**

```bash
activate-global-python-argcomplete
source /etc/profile
```

在bash 小于4.2 时，使用下列命令注册

```bash
$ eval $(register-python-argcomplete ansible)
$ eval $(register-python-argcomplete ansible-config)
$ eval $(register-python-argcomplete ansible-console)
$ eval $(register-python-argcomplete ansible-doc)
$ eval $(register-python-argcomplete ansible-galaxy)
$ eval $(register-python-argcomplete ansible-inventory)
$ eval $(register-python-argcomplete ansible-playbook)
$ eval $(register-python-argcomplete ansible-pull)
$ eval $(register-python-argcomplete ansible-vault)
source /etc/profile
```
