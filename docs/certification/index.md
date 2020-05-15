# Ansible 认证

通过红帽 Ansible 自动化专业技能证书考试的 IT 专业人员，证明其具备在企业环境中，熟练运用 Ansible 实现自动化系统管理和部署自动化所需的技能、知识和能力。



可以加入 [https://join.slack.com/t/redhat-certs](https://join.slack.com/t/redhat-certs/shared_invite/zt-7ju3rz7b-_G3Njp3PDwdBG_81SwPeLA) 组一起学习。



## 红帽认证 Ansible 自动化专家

获得红帽 Ansible 自动化专业技能证书的 IT 专业人员能够执行以下任务：

- 使用 Ansible 清单 (inventory) 定义主机组
- 创建 Ansible playbook
- 使用 playbook，将系统配置为指定的状态
- 创建和使用 Ansible 模板来为主机创建自定义的配置文件
- 创建 Ansible 角色
- 利用 playbook 中的 Ansible Vault 保护敏感数据
- 安装 Ansible Tower 并用它来管理系统

### 认证

[红帽 Ansible 自动化专业技能证书考试 (EX407)](https://www.redhat.com/zh/services/training/ex407-红帽-ansible-自动化专业技能证书)

### 官方培训课程

- [利用 Ansible 实现自动化课程 (DO407)](https://www.redhat.com/zh/services/training/do407-automation-ansible-i)
- [利用 Ansible 实现自动化课程及考试 (DO408)](https://www.redhat.com/zh/services/training/do408-automation-ansible-i-exam)

DO407基于红帽企业级操作系统7，利用 Ansible 实现自动化课程 I (DO407) 专为想要借助 Ansible 实现自动化、配置和管理的系统管理员而设计。了解如何安装和配置 Ansible、创建和运行 playbook 来配置系统以及管理 inventory (配置文件)，实现自动化部署、批量部署、批量配置修改及数据中心监控，针对开源提供的playbook实现部署和应用，同时对企业个性化服务、个性化修改提供二次开发和编写的能力。

### 考试介绍

#### 考试概述

红帽认证 Ansible 自动化专家考试（EX407）旨在测试您运用 Ansible 实现系统和应用配置自动化的能力。

通过此项考试后，您将成为[红帽认证 Ansible 自动化专家](https://www.redhat.com/zh/services/certification/rhcoe-ansible-automation)，并将计入红帽认证架构师（RHCA）的认证成绩中。

本课程基于红帽® 企业 Linux® 7.5 和 Ansible 2.7。

现在，此项考试涵盖的材料包含在[红帽认证工程师 (RHCE) 考试 (EX294)](https://www.redhat.com/zh/services/training/ex294-red-hat-certified-engineer-rhce-exam-red-hat-enterprise-linux-8) 的课程中。此项新考试旨在测试您能否使用红帽 Ansible 自动化使不同功能实现自动化并有效扩展基础架构。

#### 考核对象

- 需要管理大量系统的系统管理员
- 在 DevOps 环境中工作、并想实现大部分日常作业量自动化的系统管理员
- 具有基本系统管理背景、并想实现开发流程自动化的开发人员
- 有兴趣成为红帽认证专家或[红帽认证架构师（RHCA）](https://www.redhat.com/zh/services/certification/rhca)的[红帽认证工程师（RHCE）](https://www.redhat.com/zh/services/certification/rhce)

#### 考试前提条件

- 成功完成[利用 Ansible 实现自动化（DO407）](https://www.redhat.com/zh/services/training/do407-automation-ansible-i)课程，或具有使用 Ansible 配置系统的同等经验
- 建议先成为[红帽认证系统管理员（RHCSA）](https://www.redhat.com/zh/services/certification/rhcsa)或具有同等或更高的系统管理经验，但不强制要求

#### 考查要点

我们建议考生在参加此项考试前先成为[红帽认证工程师（RHCE®）](https://www.redhat.com/zh/services/certification/rhce)或至少成为[红帽认证系统管理员（RHCSA®）](https://www.redhat.com/zh/services/certification/rhcsa)，但两者并不强制要求。

为了帮助您备考，请查看本文给出的考试目标，其中列出了操作任务的考查范围。红帽保留添加、更改和删除考试目标的权利。此类变更将在考前公布。

您应能够：

- 了解 Ansible 的核心组件
  - Inventory（配置文件）
  - 模块
  - 变量
  - Fact
  - Play
  - Playbook
  - 配置文件
- 安装和配置 Ansible 控制节点
  - 安装所需软件包
  - 创建静态主机 inventory 文件
  - 创建配置文件
- 配置 Ansible 托管的节点
  - 创建 SSH 密钥并将其分配给托管节点
  - 在托管节点上配置权限提升
  - 使用 ad-hoc Ansible 命令验证有效配置
- 创建运行 ad hoc Ansible 命令的简单 shell 脚本
- 使用静态和动态 inventory 定义主机群组
- 使用现有的动态 inventory 脚本
- 创建 Ansible play 和 playbook
  - 了解如何使用常用的 Ansible 模块
  - 使用变量检索命令运行的结果
  - 使用条件控制 play 的执行
  - 配置错误处理
  - 创建 playbook，将系统配置为指定的状态
- 使用 Ansible 模块执行有关以下内容的系统管理任务：
  - 软件包和存储库
  - 服务
  - 防火墙规则
  - 文件系统
  - 存储设备
  - 文件内容
  - 归档
  - 计划任务
  - 安全性
  - 用户和群组
- 创建和使用模板来创建自定义的配置文件
- 使用 Ansible 变量和 fact
- 创建和使用角色
- 从 Ansible Galaxy 下载角色并使用
- 并行管理
- 利用 playbook 中的 Ansible Vault 保护敏感数据
- 使用提供的文档查找有关 Ansible 模块和命令的特定信息

#### 备考

红帽建议您学习[利用 Ansible 实现自动化一（DO407）](https://www.redhat.com/zh/services/training/do407-automation-ansible-i)课程，以帮助备考。此课程并非强制性要求，考生可以选择只参加考试。

尽管参加红帽培训课程是您备考的一个重要部分，但只参加课程并不能确保顺利通过考试。您的以往经验、实践以及自身资质也是决定能否通过考试的重要因素。

我们拥有众多有关红帽产品系统管理的书籍和学习资源供您选择。红帽未指定任何内容作为备考指南。然而，您可能发现额外的阅读会对加深理解有帮助。

#### 考试形式

这是一项基于实际操作能力的考试，旨在评估您运用 Ansible 实现系统配置和应用部署自动化的能力。考试基于实际操作，要求您执行类似日常工作职责的任务操作。

您需要开发 Ansible playbook 来为特定的角色配置系统，然后将 playbook 应用至系统来实施这些角色。此外，您还需要展示自己针对特定行为运行 Ansible playbook 和配置 Ansible 环境的能力。您将接受相应任务评估，以确定是否达到规定的评测标准。

考试时间为4小时。总分300分，

#### 成绩及公布

考试的官方成绩由[红帽认证中心](https://www.redhat.com/zh/services/certification/certification-central)独家公布。红帽未授权考官或培训合作伙伴直接向考生公布考试结果。考试成绩通常会在 3 个美国工作日内公布。

公布的考试结果为总分。红帽不公布单个项目的成绩，也不会应考生要求提供额外信息。

## 红帽认证高级自动化专家：Ansible 最佳实践

红帽认证高级自动化专家：Ansible 最佳实践能够执行以下任务：

- 理解并使用 Git 来管理 playbook 集合
- 管理 Ansible 任务执行
- 安装和管理 Ansible Tower 的访问权限
- 管理库存清单、凭证、高级库存清单、项目和工作流
- 使用 Ansible Tower API 启动作业

### 认证

[红帽认证高级自动化专家：Ansible 最佳实践（EX447）](https://www.redhat.com/zh/services/training/ex447-red-hat-certified-specialist-advanced-automation-ansible-best-practices-exam)

### 官方培训课程

[高级自动化：Ansible 最佳实践（DO447）](https://www.redhat.com/zh/services/training/do447-advanced-automation-ansible-best-practices)

### 考试介绍

#### 考试概述

红帽认证高级自动化专家：Ansible 最佳实践考试（EX447）旨在通过实际任务操作，考核您使用红帽® Ansible® 引擎和红帽 Ansible Tower 来管理多个系统的知识和技能。

通过此项考试后，您将成为[红帽认证高级自动化专家：Ansible 最佳实践考试](https://www.redhat.com/zh/services/certification/red-hat-certified-specialist-advanced-automation-ansible-best-practices)，并将计入[红帽认证架构师（RHCA®）](https://www.redhat.com/zh/services/certification/rhca)的认证成绩中。

本考试基于红帽企业 Linux 8.0、红帽 Ansible 2.8 和红帽 Ansible Tower 3.5。

#### 考核对象

红帽认证高级自动化专家：Ansible 最佳实践考试适合：想要检验有关 Ansible 最佳实践的广博知识和深入理解、希望在更大和更复杂的项目中应用 Ansible，以及使用 Ansible Tower 的人士，包括：

- 具备丰富经验的 Linux 系统管理员
- DevOps 工程师
- 云管理员
- 其他 IT 专业人员

#### 考试前提条件

- 参加过[高级自动化：Ansible 最佳实践（DO447）](https://www.redhat.com/zh/services/training/do447-advanced-automation-ansible-best-practices)课程，或拥有红帽企业 Linux®、Ansible 和 Ansible Tower 方面的同等工作经验
- 参加过[红帽系统管理三：Linux 自动化（RH294）](https://www.redhat.com/zh/services/training/rh294-red-hat-system-administration-iii-linux-automation)课程，或拥有红帽企业 Linux 和 Ansible 方面的同等工作经验
- 符合考试目标

#### 考查要点

您应能独立完成下列分组任务：

- 理解和运用 Git

- - 克隆 Git 存储库
  - 在 Git 存储库中更新、修改和创建文件
  - 将这些修改过的文件添加回 Git 存储库

- 管理库存清单变量

- - 利用每个主机或组的多个文件，构建主机和组变量
  - 使用特殊变量来覆盖主机、端口或 Ansible 针对特定主机而使用的远程用户
  - 为某些托管主机设置包含多个主机变量文件的目录
  - 以不同的名称或 IP 地址来覆盖库存清单文件中所用的名称

- 管理任务的执行

- - 控制权限执行
  - 运行所选的任务

- 借助过滤器和插件转换数据

- - 使用查找插件，用来自外部源的数据填充变量
  - 使用查找和查询功能，将来自外部源的模板数据化为 playbook 和已部署的模板文件
  - 使用查找插件和过滤器，用除简单列表之外的结构实现循环
  - 使用过滤器，检查、验证和操作包含网络信息的变量

- 委派任务

- - 在另一台主机上运行托管主机的任务，然后控制是否将该任务收集的 fact 委派给托管主机或其他主机

- 安装 Ansible Tower

- - 配置完成后，执行 Ansible Tower 的基本配置

- 管理 Ansible Tower 的访问权限

- - 创建 Ansible Tower 用户和团队并让其相互关联

- 管理库存清单和凭据

- - 管理高级库存清单
  - 从身份管理服务器或数据库服务器创建动态库存清单
  - 创建机器凭据以访问库存清单主机
  - 创建源代码控制凭据

- 管理项目

- - 创建作业模板

- 管理工作流

- - 创建工作流模板

- 使用 Ansible Tower API

- - 编写 API 脚本小程序以启动作业

- 备份 Ansible Tower

- - 备份 Ansible Tower 的实例

对于所有实际任务操作型的红帽考试，您的所有系统配置必须在重启后仍然有效（无需人工干预）。

#### 备考

为了更好备考，红帽建议您学习[高级自动化：Ansible 最佳实践（DO447）](https://www.redhat.com/zh/services/training/do447-advanced-automation-ansible-best-practices)课程。

此类课程并非强制性要求，考生可以选择只参加考试。

尽管参加红帽培训课程是您备考的一个重要部分，但只参加课程并不能确保顺利通过考试。您的以往经验、实践以及自身资质也是决定能否通过考试的重要因素。

我们拥有众多有关红帽产品系统管理的书籍和学习资源供您选择。红帽未指定任何内容作为备考指南。然而，涉猎更多会有助加深您对所学知识的理解。

#### 考试形式

此项考试属于 **上机实践操作考试** ，要求您完成真实的任务。我们将向您提供一个或多个虚拟系统，而您需要执行与真实作业相类似的任务。考试期间不提供互联网接入，您也不得将任何纸质或电子文档带入考场。禁止携带的物品包括：笔记、书籍或任何其他材料。在参加大多数考试时，您都可以使用产品随附的文档。

#### 成绩及公布

考试的官方成绩由[红帽认证中心](https://www.redhat.com/zh/services/certification/certification-central)独家公布。红帽未授权考官或培训合作伙伴直接向考生公布考试结果。考试成绩通常会在 3 个美国工作日内公布。

公布的考试结果为总分。红帽不公布单个项目的成绩，也不会应考生要求提供额外信息。