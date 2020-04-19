# 添加module的文档说明



所有模块都需按以下顺序定义以下部分：

1. shebang
2. ANSIBLE_METADATA
3. DOCUMENTATION
4. EXAMPLES
5. RETURNS
6. Python imports



## 定义 `shebang`

这里以python语言为例，定义python解释器路径和编码，另外许可信息也要添加进来。

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

# Copyright: (c) 2018, Terry Jones <terry.jones@example.org>
# GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)
```


## 定义ANSIBLE_METADATA
该变量描述有关其他工具使用的模块的信息
```python
ANSIBLE_METADATA = {'metadata_version': '1.0',
                    'status': ['preview'],
                    'supported_by': 'community'}
```

- `metadata_version` 是ansible元数据(`ANSIBLE_METADATA`)的版本
- `supported_by` 指的是谁支持这个模块，默认值`community`, 其他的可选值core, network, certified
- `status`  字符串列表，描述模块稳定的程度。可选值stableinterface(稳定),preview(预览，可能不稳定)，deprecated(弃用)，removed(删除状态，只保留不使用)

## 定义DOCUMENTATION

该变量描述模块的描述信息，参数，作者和其他信息。

```python
DOCUMENTATION = '''
---
module: remote_copy
short_description: Copy a file on the remote host
version_added: "2.9"
description:
- The remote_copy module copies a file on the remote host from a given source to a provided destination.
options:
source:
  description:
    - Path to a file on the source file on the remote host
  required: true
dest:
  description:
    - Path to the destination on the remote host for the copy
  required: true
author:
- "Lework"
'''
```

- `module` 模块名称，必须与文件名称一致，但没有扩展名`.py`
- `short_description` 简短描述
- `version_added` 模块在ansible哪个版本添加的
- `description` 详细描述
- `options`  模块的选项
- option-name 选项名称
- description 描述
- required 是否必须
- default 默认值
- choices 接受的值列表
- type 值类型
- elements list元素的数据类型
- aliases 选项别名
- version_added 在ansible哪个版本添加的
- suboptions 如果此选项采用字典或字典列表，则可以在此处定义结构。
- `author` 模块的作者名称
- `deprecated` 弃用标识
- requirements 依赖列表
- seealso 对其他模块的引用
- notes 其他信息

## 定义EXAMPLES

该变量用来描述模块的一个或多个示例使用

使用yaml格式的使用示例。

```python
EXAMPLES = '''
# Example from Ansible Playbooks
- name: backup a config file
remote_copy:
      source: /tmp/foo
      dest: /tmp/bar
'''
```

## 定义RETURN

该变量用来描述模块的返回数据信息

添加参数source和dest返回信息
```python
RETURN = '''
source:
   description: Path to a file on the source file on the remote host
   type: str
   returned: success
   sample: "/path/to/file.name"
dest:
   description: Path to the destination on the remote host for the copy
   type: string
   returned: success
   sample: "/path/to/destination.file"
'''
```

字符串的格式为yaml格式，如果模块没有返回值则应该`RETURN = r''' # '''` 返回

- return name: 返回的参数名称
  - description 参数描述
  - returned 是成功(success)返回还是总要(always)返回
  - type 数据类型
  - elements 如果type ='list'，则指定列表元素的数据类型。
  - sample 值示例
  - version_added 在ansible哪个版本添加的
  - contains 可选的。 要描述嵌套的返回值

## Python impots

使用`AnsibleModule` 来构建ansible模块

```python
from module_utils.basic import AnsibleModule
```

## 显示模块帮助信息
可以通过 `ansible-doc` 来查看这些帮助信息

显示全部信息

```bash
# ansible-doc -M /etc/ansible/library/ remote_copy
> REMOTE_COPY    (/etc/ansible/library/remote_copy.py)

        The remote_copy module copies a file on the remote host from a given source to a provided destination.

  * This module is maintained by The Ansible Community
OPTIONS (= is mandatory):

= dest
        Path to the destination on the remote host for the copy


= source
        Path to a file on the source file on the remote host



AUTHOR: Lework
        METADATA:
          status:
          - preview
          supported_by: community
        

EXAMPLES:

# Example from Ansible Playbooks
- name: backup a config file
  remote_copy:
        source: /tmp/foo
        dest: /tmp/bar


RETURN VALUES:

source:
    description: Path to a file on the source file on the remote host
    type: str
    returned: success
    sample: "/path/to/file.name"
dest:
    description: Path to the destination on the remote host for the copy
    type: string
    returned: success
    sample: "/path/to/destination.file"

```

显示简短信息

```bash
# ansible-doc -M /etc/ansible/library/ remote_copy -s
```

## 模块文档中的链接

您可以从模块文档链接到其他模块文档，在docs.ansible.com上可以超链接到其他资源以及Internet上其他资源。 这些链接的正确格式是：


| 函数 | 描述                 | 例子                                                         |
| ---- | -------------------- | ------------------------------------------------------------ |
| L()  | 格式化带有标题的链接 | L(IOS Platform Options guide,../network/user_guide/platform_ios.html) |
| U()  | 格式化url            | Required if I(state=present)                                 |
| I()  | 格式化选项名称       | Mutually exclusive with I(project_src) and I(files           |
| M()  | 格式化模块名称       | See also M(win_copy) or M(win_template).                     |
| C()  | 格式化文件和选项值   | Or if not set the environment variable C(ACME_PASSWORD) will be used. |


## Documentation 加载外部的文档

某些类别的模块有共同的文档信息，就可以使用docs_fragments共享出来。
所有的docs_fragments都可以在lib/ansible/utils/module_docs_fragments/ 目录下找到

在 Documentation 字符串中添加下列字段，就可以添加外部的文档信息
```
extends_documentation_fragment: 
  - files
  - validate
```

示例: example_fragment.py

```python
class ModuleDocFragment(object):
    # Standard documentation
    DOCUMENTATION = r'''
    options:
      # options here
    '''

    # Additional section
    OTHER = r'''
    options:
      # other options here
    '''
```

