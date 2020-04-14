# 使用 PyCharm 远程开发

在linux主机上使用vim开发Ansible模块或插件，对于新手来说不是很方便。大多数人的工作环境都是基于Windows环境的，但是 Ansible 不能运行在Windows环境下，这个时候我们想使用Windows环境下的PyCharm 工具时，只能通过远程连接的方式进行开发playbook或模块插件。

接下来，跟我一起来配置 PyCharm 工具，使其能够远程开发Ansible相关程序。



## 远程主机

OS: `cetnos 7.7 x64`

Python: `2.7.5`

Ansible: `2.9.6`

## 工作空间

新建一个工作目录，本次使用`D:\dev\ansible`目录

## 设置Python Interpreter

使用 PyCharm 打开创建好的工作目录，选中项目，打开选项`Files`=>`Settings`=>`Project: ansible`=>`Project Interpreter`

在`Project Interpreter` 右侧选择`Add`添加
![pycharm-ide](/images/dev/pycharm-ide01.png)

选择 `SSH Interpreter` 进行设置远程主机的连接信息
![pycharm-ide](/images/dev/pycharm-ide02.png)

输入连接信息后，还需填写认证信息。
![pycharm-ide](/images/dev/pycharm-ide03.png)

认证通过后，就要设置远程主机的 `Python` 可执行路径和需要同步的目录
![pycharm-ide](/images/dev/pycharm-ide04.png)
> 本次使用的时工作目录和远程的`/etc/ansible`目录进行同步

设置完成后，点击 **OK** 确认设置
![pycharm-ide](/images/dev/pycharm-ide05.png)

## 同步目录
我们工作空间此刻还是空的，需要与远程目录进行同步，将远程目录的数据下载到工作空间

选中项目，打开选项`Tools`=>`Deployment`=>`Download from root@192.168.77.130:22`
![pycharm-ide](/images/dev/pycharm-ide06.png)

等待一会，就同步完成了
![pycharm-ide](/images/dev/pycharm-ide07.png)


## 开发文件

这个时候，我们在`library`目录中创建一个`remote_copy.py` 文件
![pycharm-ide](/images/dev/pycharm-ide08.png)

可以发现，我们在Windows上也能import ansible相关信息了。

![pycharm-ide](/images/dev/pycharm-ide09.png)
pycharm会在后台起一个进程来监控工作空间的变动，如有变动将会同步到远程主机目录

点击左下角的`Python Console` 可以进入远程主机的python解释器中
![pycharm-ide](/images/dev/pycharm-ide10.png)

## 执行命令

在我们需要运行ansible模块或插件时，我们可以远程连接到主机上进行操作ansible命令运行playbook

打开选项`Tools`=>`Start SSH session...`, 选择 192.168.77.130 主机
![pycharm-ide](/images/dev/pycharm-ide11.png)

连接成功后，就可以在`Terminal`界面操作ansible命令了

![pycharm-ide](/images/dev/pycharm-ide12.png)

## Debug代码

见 [PyCharm 远程调试](/dev/debug/pycharm/)
