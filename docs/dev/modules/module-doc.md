# 添加module的文档说明

所有模块必须按以下顺序定义以下部分：

1. ANSIBLE_METADATA
2. DOCUMENTATION
3. EXAMPLES
4. RETURNS
5. Python imports


1. 定义ANSIBLE_METADATA，该变量描述有关其他工具使用的模块的信息
    ```python
    ANSIBLE_METADATA = {'metadata_version': '1.0',
    					'status': ['preview'],
    					'supported_by': 'community'}
    ```
1. 定义DOCUMENTATION，该变量描述模块的描述信息，参数，作者和许可信息。
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
1. 定义EXAMPLES，该变量用来描述模块的一个或多个示例使用
	```python
	EXAMPLES = '''
	# Example from Ansible Playbooks
	- name: backup a config file
	  remote_copy:
	        source: /tmp/foo
	        dest: /tmp/bar
	'''
	```

1. 定义RETURN，该变量用来描述模块的返回数据信息
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
   
   字符串的格式为yaml格式。

可以通过ansible-doc 来查看这些信息
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

## 用于格式化字符串的一些选项，用于DOCUMENTATION


|函数|	描述	|例子|
|:|:|
|U() 	|格式化url 	|Required if I(state=present)|
|I()	|格式化选项名称	|Mutually exclusive with I(project_src) and I(files)|
|M()	|格式化模块名称	|See also M(win_copy) or M(win_template).|
|C()	|格式化文件和选项值	|Or if not set the environment variable C(ACME_PASSWORD) will be used.|


## Documentation 加载外部的文档


某些类别的模块有共同的文档信息，就可以使用docs_fragments共享出来。
所有的docs_fragments都可以在lib/ansible/utils/module_docs_fragments/ 目录下找到

在Documentation 字符串中添加下列字段，就可以添加外部的文档信息
```
extends_documentation_fragment: 
  - files
   - validate
```
