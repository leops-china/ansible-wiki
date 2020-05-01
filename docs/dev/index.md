# Ansible 开发

## 官方开发文档

http://docs.ansible.com/ansible/dev_guide/index.html

> 非常推荐大家看看 **官方文档**

## 环境

本次所用的环境

- ansible `2.9.6.0`

- os `Centos 7.7 X64`

- python `2.7.5`

## 介绍

Ansible 开发分为两大模块，一是`modules`，二是`plugins`。

首先，要记住这两部分内容在哪个地方执行？

- `modules` 文件被传送到 **远端主机** 并执行。
- `plugins` 是在 **ansible控制节点** 上执行的。

再者是执行顺序？

`plugins` 先于 `modules` 执行。

然后大家明确这两部分内容是干啥用的？

- `modules` 是ansible的核心内容，它使playbook变得更加简单明了，一个task就是完成某一项功能。ansible模块是被传送到远程主机上运行的。所以它们可以用远程主机可以执行的任何语言编写modules。

- `plugins` 是在 **ansible控制节点** 上执行的，用来辅助modules做一些操作。比如连接远程主机，拷贝文件到远程主机之类的。


最后，学习开发之前，要先学会[Debug](/dev/debug/verbose-debug/)

## Ad-hoc 执行过程

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

!!! note
    如果要深入了解执行过程，可以查看更详细的代码执行过程[Ansible ad-hoc执行过程](/images/dev/ansible-working-process-2.9.pdf)


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