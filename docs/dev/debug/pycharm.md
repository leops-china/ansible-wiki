# PyCharm 远程调试

## 介绍

PyCharm是一种Python IDE，带有一整套可以帮助用户在使用Python语言开发时提高其效率的工具，比如调试、语法高亮、Project管理、代码跳转、智能提示、自动完成、单元测试、版本控制。此外，该IDE提供了一些高级功能，以用于支持Django框架下的专业Web开发。
本地调试有许多不方便的地方。PyCharm提供了所见及所得的调试界面。调试更加轻松方便。

## 配置PyCharm远程调试

1. 打开pycharm--》RUN ==》Edit Configuration
  ![image.png](/images/pycharm01.png)
2. 点击+号按钮，选择Python Remote Debug
  ![image.png](/images/pycharm02.png)
3. 设置远程debug的监听地址。
 ![image.png](/images/pycharm03.png)
   - **Local host name** 是本机的IP。
   - **Port** 在保证不冲突的情况下可以任意指定。
4. 启动pycharm调试
  ![image.png](/images/pycharm04.png)
  可以看到console里的监听信息，正在等待远程主机连接。
  ![image.png](/images/pycharm05.png)


## 在控制节点上安装远程调试插件

1. 将pycharm-debug.egg文件拷贝到远程主机的python的site-packages目录下，并安装。
  ![image.png](/images/pycharm06.png)
  安装pycharm-debug.egg
  ![image.png](/images/pycharm07.png)

2. 在需要调试的代码中加入远程调试所需的代码
  查找到ansible执行文件
  ![image.png](/images/pycharm08.png)

3. 在程序入口添加下面两行代码
  ```python
  import pydevd
  pydevd.settrace('192.168.77.1', port=9999, stdoutToServer=True, stderrToServer=True)
  ```
  ![image.png](/images/pycharm09.png)
  
4. 启动ansible命令
   ![image.png](/images/pycharm10.png)


## 使用PyCharm调试远程代码

1. 查看pycharm窗口，可以看到有链接进来。
  ![image.png](/images/pycharm11.png)
2. 此时可点击”Download”下载源码
  ![image.png](/images/pycharm12.png)
3. 点击完成后，就可以看到远程的ansible代码。
  ![image.png](/images/pycharm13.png)
4. 调试的一些常用按钮
  ![image.png](/images/pycharm14.png)

