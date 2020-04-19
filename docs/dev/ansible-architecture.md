# Ansible 架构

## Modules

 Ansible通过连接到节点并向其推出称为“ Ansible Modules”的脚本来工作。 大多数模块接受描述系统所需状态的参数。 然后，Ansible执行这些模块（默认情况下通过SSH），并在完成后将其删除。 您的模块库可以驻留在任何计算机上，并且不需要服务器，守护程序或数据库。 

您可以用任何语言 (Ruby、Python、bash等)编写可以返回 **JSON** 的模块。 

## Module utilities

 当多个模块使用相同的代码时，Ansible将这些功能存储为Module utilities，以减少重复和维护。 



## Plugins

 插件增强了Ansible的核心功能。模块在目标系统上以独立的进程执行(通常是在远程系统上)，插件则是在`/usr/ bin/nsible`进程内的控制节点上执行。 插件为Ansible的核心特性提供了选项和扩展—转换数据、日志输出、连接到目录等等。您可以编写一个inventory插件来连接任何返回JSON的数据源。插件必须用Python编写。 
 

## Inventory

默认情况下，Ansible在文件（INI，YAML等）中表示其管理的计算机，当然，你也可以通过动态形式从EC2、Rackspace或OpenStack等数据源获取主机。 

静态文件文件内容

```yaml
---
[webservers]
www1.example.com
www2.example.com

[dbservers]
db0.example.com
db1.example.com
```

## Playbooks

剧本可以很好地协调基础结构中的各个task，并且可以控制并发处理的计算机数量。

一个简单的playbook

```bash
---
- hosts: webservers
serial: 5 # update 5 machines at a time
roles:
- common
- webapp

- hosts: content_servers
roles:
- common
- content
```



## Ansible 搜索路径

模块、模块工具类、插件、剧本和角色可以位于多个位置。如果你编写自己的代码来扩展Ansible的核心功能，你可能在你的Ansible控制节点的不同位置有多个名称相似或相同的文件。搜索路径决定了哪些文件将被指定的剧本所使用。

在整个运行过程中，Ansible的搜索路径会逐渐增加。 当Ansible查找给定运行中包含的每个剧本和角色时，它将与该剧本或角色相关的所有目录追加到搜索路径中。 即使在剧本或角色执行完毕后，这些目录仍在运行期间保持作用域。 Ansible按以下顺序加载模块，模块工具类和插件：  

1.  如果使用`ansible-playbook /path/to/play.yml`运行Ansible，则Ansible会附加以下目录（如果存在）： 
    ```
    /path/to/modules
    /path/to/module_utils
    /path/to/plugins
    ```

2.  如果`play.yml`包含`-import_playbook：/path/to/subdir/play1.yml`，则Ansible将附加以下目录（如果存在）： 
    ```
    /path/to/subdir/modules
    /path/to/subdir/module_utils
    /path/to/subdir/plugins
    ```

3.  如果`play.yml`运行`myrole`，则Ansible将附加以下目录（如果存在）： 
    ```
    /path/to/roles/myrole/modules
    /path/to/roles/myrole/module_utils
    /path/to/roles/myrole/plugins
    ```

4. 可以在`ansible.cfg`中为其指定默认目录或者由相关的环境变量指定 
   ```
   library
   module_utils
   cache_plugins
   filter_plugins
   ```
    对应的环境变量
    ```
    ANSIBLE_LIBRARY
    ANSIBLE_MODULE_UTILS
    ANSIBLE_CACHE_PLUGINS
    ANSIBLE_FILTER_PLUGINS
    ```

    更多的参数设置见[Ansible 配置](/basic/Reference/Config/)

5. 作为Ansible发行版一部分提供的标准目录
   ```bash
   /lib/python2.7/site-packages/ansible/modules/
   /lib/python2.7/site-packages/ansible/module_utils/
   /lib/python2.7/site-packages/ansible/plugins/
   ```

  