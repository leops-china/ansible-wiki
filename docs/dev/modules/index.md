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


### 本地添加模块

Ansible自动将在某些目录中找到的所有可执行文件作为模块加载，因此您可以在以下任意位置创建或添加本地模块：

- 使用环境变量`ANSIBLE_LIBRARY`定义的目录列表，使用逗号分隔。
- `~/.ansible/plugins/modules/`
- `/usr/share/ansible/plugins/modules/`

针对于playbook使用

- 保存在playbook当前目录`library`目录中的文件

针对于role使用

- 保存在role目录下`library`目录中的文件 

也可以在配置文件中指定模块目录
```ini
[defaults]
library        = /usr/share/my_modules/
module_utils   = /usr/share/my_module_utils/
```


## 模块工具

Ansible提供了许多模块实用程序，它们提供了在开发自己的模块时可以使用的辅助功能。 basic.py模块为程序提供访问Ansible库的主要入口点，所有Ansible模块必须至少从basic.py导入：
```python
from ansible.module_utils.basic import *
```
