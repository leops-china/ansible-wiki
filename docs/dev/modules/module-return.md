
# 模块返回值

Ansible模块通常返回一个数据结构，其数据可以注册为变量，或由Ansible输出到控制台。



## 通用返回值

> 所有模块通用的返回值

|名称	|类型	|说明|
|:---|:---|:---|
|backup_file	|str	|对于一些modules使用了backup变量，返回备份的文件路径|
|changed	|bool|	表示任务是否必须进行更改。|
|failed	|bool	|表示任务是否失败。|
|invocation|	dict	|有关如何调用模块的信息。|
|msg	|str|	存储通用消息的字符串|
|rc|	int|	命令行程序的返回码|
|results	|dict	|如果该键存在，则表示该任务存在循环，并且它包含每个项目的模块“results”的列表。|
|skipped|	bool	|表示该任务是否被跳过|
|stderr	|str|	命令行程序的错误输出|
|stderr_lines|	list	|它将stderr字符串按行分割存储在列表中|
|stdout	|str|	命令行程序的标准输出|
|stdout_lines	|list	|它将stdout字符串按行分割存储在列表中|

## 内部使用
---

这些值是ansible内部定义的,模块可以使用，但不能用作注册变量。

|名称	|类型	|说明|
|:---|:---|:---|
|ansible_facts	|dict	|该key应包含一个字典，附加到分配给主机的fact。 这些可以直接访问，不需要使用注册的变量。|
|exception	|dict	|该key包含由模块中的异常引起的追溯信息。 它只能以高度详细程度显示（-vvv）。|
|warnings|	list	|此键包含将显示给用户的字符串列表。|
|deprecations|dict	|返回msg和version的字典列表|
