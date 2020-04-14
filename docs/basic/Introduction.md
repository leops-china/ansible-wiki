# 1. Ansible 介绍

Ansible 是2012年推出的一种通用自动化工具，可用于配置管理或工作流程自动化。配置管理是一种" **基础架构代码** "实践，它将事物编码，例如应该在系统上安装什么包和版本，或者应该运行什么守护进程。工作流自动化可能是从配置基础架构到部署软件的任何事情。Ansible 在2015年时被Redhat公司收购。

Ansible是用Python编写的，它使用SSH在不同的机器上执行命令。Ansible是无代理的，这使得入手更容易。您只需要在相关机器上安装SSH和Python。Ansible使用声明式YAML语言"playbook"将一组主机（"hosts"）映射到定义明确的角色。声明性用于指示Ansible如何设置或更改事物，Ansible才进行必要的更改。

## Ansible 的目标

一切自动化

## ansible的使用范围

- 自动化部署应用
- 自动化管理配置
- 自动化的持续交付
- 自动化的云服务管理
- 自动化网络设备管理

## Ansible是怎么工作的

![ansible-arch](/images/ansible-arch.png)
从上图可以看出，运行ansible的先决条件是，安装ansible到管理节点，定义主机清单，并有一些playbooks定义。


简要的步骤

1. 在控制节点上安装`ansible`
2. 配置主机清单: 将被控节点的连接信息配置到主机清单中。
3. 定义playbook: 指定运行主机和执行任务

让我们来看看我们如何使用Ansible将我们的Ubuntu虚拟机转换为Web服务器。
您在管理节点上运行Ansible Playbook，它查看您在playbook中定义的命令参数，并通知我们定位到网络组中的节点。
Ansible然后读取主机清单以查找分配给Web组的节点。在这一点上，Ansible已经准备好开始工作，所以它将通过ssh远程连接到定义的机器，通常你会想要通过预共享密钥建立一些类型的ssh信任，这样你就不必在进行ssh登陆的时候输入密码。然后Ansible将开始逐步执行playbook中的任务，一次一个任务，从顶部到底部的顺序遍历它们，就像你手动登录执行任务一样。所以，它安装软件包，更新配置文件，使用git部署我们的网站代码，最后启动我们的Web服务。当Ansible很愉快的把一切都按预期的完成，你会得到一个执行成功的状态报告。

可以用动图说明下此次过程。
![ansible-arch](/images/ansible-arch.gif)

## 对管理主机的要求
目前,只要机器上安装了 Python 2（版本2.6或2.7）或Python 3（版本3.5及更高版本）都可以运行Ansible (windows系统不可以做管理主机)
管理主机的系统可以是 Red Hat, Debian, CentOS, OS X, BSD的各种版本.

## 对节点主机的要求
通常我们使用 ssh 与节点通信，默认使用 sftp.  如果 sftp 不可用，可在 ansible.cfg 配置文件中配置成 scp 的方式. 在节点上也需要安装Python 2（2.6或更高版本）或Python 3（3.5或更高版本）

## Ansible 概念

### 控制节点(Control node)
任何装有Ansible的机器可称为 **控制节点** 。 您可以从任何控制节点运行命令和剧本，并调用`/usr/bin/ansible`或`/usr/bin/ansible-playbook`。 您可以将任何安装了Python的计算机用作控制节点,笔记本电脑,共享桌面和服务器都可以运行Ansible。 但是，不能将Windows计算机用作控制节点。您也可以有多个控制节点。

### 管理节点(Managed nodes)
使用Ansible管理的网络设备或服务器可称为 **管理节点**。 受管节点有时也称为 **主机** 。 受管节点上是不需要安装Ansible的。

### 主机清单(Inventory)
托管节点的列表。库存文件有时也称为主机文件。您的目录可以为每个托管节点指定诸如IP地址之类的信息。库存还可以组织托管节点，创建和嵌套组，以便于扩展。要了解更多关于库存的信息，请参见使用[主机清单](/basic/Inventory/)一节。

### 模块(Modules)
Ansible执行的具体代码。每个模块都有特定的用途，从管理特定类型数据库的用户到管理特定类型网络设备上的VLAN接口。您可以使用任务调用单个模块，也可以调用剧本中的几个不同模块。要了解Ansible包含多少个模块，请查看[所有模块](/basic/Reference/Module/)的列表。

### 任务(Tasks)
Ansible的行动单位。tasks包含一组由module组成的任务列表, 您可以使用特别的命令一次性执行单个任务。

### 剧本(Playbooks)
保存了已排序的任务列表，因此可以按此顺序重复运行这些任务。剧本可以包括变量和任务。剧本是用 **YAML** 编写的，易于阅读、编写、共享和理解。要了解更多关于剧本的信息，请查看[剧本](/basic/Playbook/)。


## 社区活跃

> 统计时间: 2020年04月06日

- Ansible releases `304`
- Ansible modules `3387`
- Galaxy Roles `24,251`
- Github Starts `42,547`
- Github Fork `18,764`
- Github Contributors `4,955`

## ansible项目

Ansible Galaxy是一个用于查找，共享，使用Ansible role的在线社区。
https://galaxy.ansible.com/

Ansible Container是一个开源项目，旨在实现整个容器构建，部署和管理过程的自动化。
https://github.com/ansible/ansible-container

Ansible tower
商业项目，使用可视化仪表板，基于角色的访问控制，作业调度，集成通知和图形库存管理来集中和控制IT基础架构。
https://www.ansible.com/products/tower

## Ansible 证书

- AUTOMATION WITH ANSIBLE I    (DO407)
  了解如何安装和配置Ansible，创建和运行剧本以配置系统，并学习管理主机。
- AUTOMATION WITH ANSIBLE II: RED HAT ANSIBLE TOWER  (DO409)
  了解使用 Ansible Tower。
- RED HAT CERTIFICATE OF EXPERTISE IN ANSIBLE AUTOMATION (EX407)
  测试您使用Ansible自动配置系统和应用程序的技能，知识和能力。通过此考试，您将获得Ansible Automation的红帽认证证书。

## Ansible 与其它配置管理的对比

笔者选择了目前几款主流的与 Ansible 功能类似的配置管理软件chef、 Puppet、Saltstack，这里所做的对比不针对各个软件的性能作比较，只是对各个软件的特性做个对比。

|                   | **Ansible**   | **Chef**         | **Puppet**        | **SaltStack**        |
| ----------------- | ------------- | ---------------- | ----------------- | -------------------- |
| **程序语言**      | Python        | Ruby，Erlang     | C++, Clojure      | Python2              |
| **配置文件语言**  | YAML，JSON    | Ruby             | Propfietary       | YAML                 |
| **数据库**        | 否            | PostgreSQL       | PuppetDB          | 无                   |
| **传输方式**      | Ssh           | RabbitMQ         | Mcollective       | ZeroMQ               |
| **发布方式**      | Push          | Pull             | Pull              | Push                 |
| **管理节点**      | A，B，L，O，S | Linux            | Linux             | L，B                 |
| **客户端**        | 否            | A，B，L，O，S，W | A，B，L，O，S，W  | A，B，L，O，S，W     |
| **无代理**        | 是            | 否               | 否                | 否                   |
| **公有云版本**    | AM            | AM/AZ/PR         | 否                | 否                   |
| **公有云管理**    | AM/AZ/OS/GCP  | Fog driver       | AM/AZ/VM/GCP      | salt Cloud           |
| **架构**          | Server        | server/client    | server/client     | server/client        |
| **逐步部署**      | 是            | 是               | 否                | 否                   |
| **企业版UI**      | Ansible Tower | opscode Manage   | Puppet Enterprise | SaltStack Enterprise |
| **开源版UI**      | Semaphore     | Chef Manage      | Foreman           | Slatpad，Saltshaker  |
| **企业版本**      | 是            | 是               | 是                | 是                   |
|                   |               |                  |                   |                      |
| **创建时间**      | 2012年3月6日 |   2009年1月16日  |  2010年9月15日    |  2011年2月21日       |
| **Github Starts** | 42,547        | 6,198            | 5,710             | 10,747                |
| **Github Forks**  | 18,764        | 2,417            | 2,138             | 4,815                |
| **Contributors**  | 4,955         | 586              | 536               | 2,078                |
| **Commits**       | 49,775       | 26,017           | 31,751            |  106,129               |


> 统计时间: 2020年04月06日


## 资源

- 源码：https://github.com/ansible/ansible
- 官方文档： http://docs.ansible.com/
- Jinja2 中文文档： http://docs.jinkan.org/docs/jinja2/
- yaml语法： http://www.yaml.org/
- ansible 电子书: https://www.ansible.com/resources/ebooks
- 白皮书: https://www.ansible.com/resources/whitepapers
- 用户案例: https://www.ansible.com/resources/case-studies
