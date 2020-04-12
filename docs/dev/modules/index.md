## 模块介绍

模块(也称为task插件或library插件)是可以从命令行或playbook任务中使用的独立单元。Ansible通常在远程目标节点上执行每个模块，并收集返回值。

可以使用下列命令执行模块

```bash
ansible webservers -m service -a "name=httpd state=started"
ansible webservers -m ping
ansible webservers -m command -a "/sbin/reboot -t now"
```

> 每个模块都支持采用参数。 几乎所有模块都采用key = value参数，以空格分隔。 一些模块不带任何参数，而command/shell模块仅采用要运行命令的字符串。

在playbook中使用模块

```bash
- name: reboot the servers
  action: command /sbin/reboot -t now
  
- name: reboot the servers
  command: /sbin/reboot -t now
  
- name: restart webserver
  service:
    name: httpd
    state: restarted
```

获取模块的帮助信息

```bash
ansible-doc yum
```

获取可用的模块列表

```bash
ansible-doc -l
```

更多命令介绍见[ansible-doc](/basic/Ansible-command/#ansible-doc)

### 在开发模块之前，现问下自己几个问题？

1. 官方是否有提供的类似功能模块？
     可从下面两个连接确定官方提供的模块，以免重复造轮子
	- 官方已发布的模块 http://docs.ansible.com/ansible/modules.html
	- 官方正在开发的模块 https://github.com/ansible/ansible/labels/module
	
2. 你需要开发一个action 插件么？
	action插件是在ansible主机上运行，而不是在目标主机上运行的。对于类似file/copy/template功能的模块，在模块执行前需要在ansible主机上做一些操作的。有关action插件的开发请移步到

### 明确几点
	- 模块是传送到目标主机上运行的。
	- 模块的返回值必须是json dumps的字符串。

> 模块的通用返回值见[模块返回值](/dev/modules/module-return/)

## 执行模块的过程

```bash
# ansible 192.168.77.130 -m ping -vvv
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Aug  7 2019, 00:51:29) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
Using /etc/ansible/ansible.cfg as config file
host_list declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
script declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
auto declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
Parsed /etc/ansible/hosts inventory source with ini plugin
META: ran handlers
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'echo ~root && sleep 0'"'"''
<192.168.77.130> (0, '/root\n', '')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'( umask 77 && mkdir -p "` echo /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356 `" && echo ansible-tmp-1586615361.42-9030567083356="` echo /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356 `" ) && sleep 0'"'"''
<192.168.77.130> (0, 'ansible-tmp-1586615361.42-9030567083356=/root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356\n', '')
<192.168.77.130> Attempting python interpreter discovery
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'echo PLATFORM; uname; echo FOUND; command -v '"'"'"'"'"'"'"'"'/usr/bin/python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.6'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.5'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python2.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python2.6'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/libexec/platform-python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/bin/python3'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python'"'"'"'"'"'"'"'"'; echo ENDFOUND && sleep 0'"'"''
<192.168.77.130> (0, 'PLATFORM\nLinux\nFOUND\n/usr/bin/python\n/usr/bin/python2.7\n/usr/libexec/platform-python\n/usr/bin/python\nENDFOUND\n', '')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'/usr/bin/python && sleep 0'"'"''
<192.168.77.130> (0, '{"osrelease_content": "NAME=\\"CentOS Linux\\"\\nVERSION=\\"7 (Core)\\"\\nID=\\"centos\\"\\nID_LIKE=\\"rhel fedora\\"\\nVERSION_ID=\\"7\\"\\nPRETTY_NAME=\\"CentOS Linux 7 (Core)\\"\\nANSI_COLOR=\\"0;31\\"\\nCPE_NAME=\\"cpe:/o:centos:centos:7\\"\\nHOME_URL=\\"https://www.centos.org/\\"\\nBUG_REPORT_URL=\\"https://bugs.centos.org/\\"\\n\\nCENTOS_MANTISBT_PROJECT=\\"CentOS-7\\"\\nCENTOS_MANTISBT_PROJECT_VERSION=\\"7\\"\\nREDHAT_SUPPORT_PRODUCT=\\"centos\\"\\nREDHAT_SUPPORT_PRODUCT_VERSION=\\"7\\"\\n\\n", "platform_dist_result": ["centos", "7.4.1708", "Core"]}\n', '')
Using module file /usr/lib/python2.7/site-packages/ansible/modules/system/ping.py
<192.168.77.130> PUT /root/.ansible/tmp/ansible-local-50740hJgOb9/tmpp7Dy_u TO /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/AnsiballZ_ping.py
<192.168.77.130> SSH: EXEC sshpass -d8 sftp -o BatchMode=no -b - -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 '[192.168.77.130]'
<192.168.77.130> (0, 'sftp> put /root/.ansible/tmp/ansible-local-50740hJgOb9/tmpp7Dy_u /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/AnsiballZ_ping.py\n', '')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'chmod u+x /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/ /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/AnsiballZ_ping.py && sleep 0'"'"''
<192.168.77.130> (0, '', '')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 -tt 192.168.77.130 '/bin/sh -c '"'"'/usr/bin/python /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/AnsiballZ_ping.py && sleep 0'"'"''
<192.168.77.130> (0, '\r\n{"invocation": {"module_args": {"data": "pong"}}, "ping": "pong"}\r\n', 'Shared connection to 192.168.77.130 closed.\r\n')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'rm -f -r /root/.ansible/tmp/ansible-tmp-1586615361.42-9030567083356/ > /dev/null 2>&1 && sleep 0'"'"''
<192.168.77.130> (0, '', '')
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "invocation": {
        "module_args": {
            "data": "pong"
        }
    }, 
    "ping": "pong"
}
META: ran handlers
META: ran handlers
```



首先，将模块文件读入内存，然后添加传递给模块的参数，最后将模块中所需要的类添加到内存，由zipfile压缩后，再由base64进行编码，写入到模版文件内。

通过默认的连接方式，一般是ssh。ansible通过ssh连接到远程主机，创建临时目录，并关闭连接。然后将打开另外一个ssh连接，将模版文件以sftp方式传送到刚刚创建的临时目录中，写完后关闭连接。然后打开一个ssh连接将任务对象赋予可执行权限，执行成功后关闭连接。

最后，ansible将打开第三个连接来执行模块，并删除临时目录及其所有内容。模块的结果是从标准输出stdout中获取json格式的字符串。ansible将解析和处理此字符串。如果有任务是异步控制执行的，ansible将在模块完成之前关闭第三个连接，并且返回主机后，在规定的时间内检查任务状态，直到模块完成或规定的时间超时。

使用了 **管道连接** 后，与远程主机只有一个连接，命令通过数据流的方式发送执行。

配置方式
```
vim /etc/ansible/ansible.cfg
pipelining = True
```
执行过程

```bash
# ansible 192.168.77.130 -m ping  -vvv
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Aug  7 2019, 00:51:29) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
Using /etc/ansible/ansible.cfg as config file
host_list declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
script declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
auto declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
Parsed /etc/ansible/hosts inventory source with ini plugin
META: ran handlers
<192.168.77.130> Attempting python interpreter discovery
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'echo PLATFORM; uname; echo FOUND; command -v '"'"'"'"'"'"'"'"'/usr/bin/python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.6'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.5'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python2.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python2.6'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/libexec/platform-python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/bin/python3'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python'"'"'"'"'"'"'"'"'; echo ENDFOUND && sleep 0'"'"''
<192.168.77.130> (0, 'PLATFORM\nLinux\nFOUND\n/usr/bin/python\n/usr/bin/python2.7\n/usr/libexec/platform-python\n/usr/bin/python\nENDFOUND\n', '')
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'/usr/bin/python && sleep 0'"'"''
<192.168.77.130> (0, '{"osrelease_content": "NAME=\\"CentOS Linux\\"\\nVERSION=\\"7 (Core)\\"\\nID=\\"centos\\"\\nID_LIKE=\\"rhel fedora\\"\\nVERSION_ID=\\"7\\"\\nPRETTY_NAME=\\"CentOS Linux 7 (Core)\\"\\nANSI_COLOR=\\"0;31\\"\\nCPE_NAME=\\"cpe:/o:centos:centos:7\\"\\nHOME_URL=\\"https://www.centos.org/\\"\\nBUG_REPORT_URL=\\"https://bugs.centos.org/\\"\\n\\nCENTOS_MANTISBT_PROJECT=\\"CentOS-7\\"\\nCENTOS_MANTISBT_PROJECT_VERSION=\\"7\\"\\nREDHAT_SUPPORT_PRODUCT=\\"centos\\"\\nREDHAT_SUPPORT_PRODUCT_VERSION=\\"7\\"\\n\\n", "platform_dist_result": ["centos", "7.4.1708", "Core"]}\n', '')
Using module file /usr/lib/python2.7/site-packages/ansible/modules/system/ping.py
Pipelining is enabled.
<192.168.77.130> ESTABLISH SSH CONNECTION FOR USER: root
<192.168.77.130> SSH: EXEC sshpass -d8 ssh -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o Port=22 -o 'User="root"' -o ConnectTimeout=10 -o ControlPath=/root/.ansible/cp/09e16ea432 192.168.77.130 '/bin/sh -c '"'"'/usr/bin/python && sleep 0'"'"''
<192.168.77.130> (0, '\n{"invocation": {"module_args": {"data": "pong"}}, "ping": "pong"}\n', '')
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "invocation": {
        "module_args": {
            "data": "pong"
        }
    }, 
    "ping": "pong"
}
META: ran handlers
META: ran handlers
```

执行完后，会有一个ssh的管道, 下次连接远程主机时，会直接使用这个管道，而不必重新建立连接。

```bash
# ps aux | grep [a]nsible
root      50757  0.0  0.3 176416  3424 ?        Ss   22:29   0:00 ssh: /root/.ansible/cp/09e16ea432 [mux]
```



## 模块工具

Ansible提供了许多模块实用程序，它们提供了在开发自己的模块时可以使用的辅助功能。 basic.py模块为程序提供访问Ansible库的主要入口点，所有Ansible模块必须至少从basic.py导入：
```python
from ansible.module_utils.basic import *
```
