# 模块架构

如果您正在使用Ansible Core代码、编写Ansible模块或开发动作插件，那么本次深入研究可帮助您了解Ansible程序流程是如何执行的。 如果您只是在剧本中使用Ansible模块，则可以跳过此部分。 



## 模块类型

Ansible在其代码库中支持几种不同类型的模块。 其中一些是为了向后兼容，而其他一些则是为了实现灵活性。

### Aaction plugins

对于playbook来说，**action** 插件看起来是模块。大多数 **action** 插件的使用文档都位于同名的模块中。 一些 **action** 插件可以完成所有工作，而该模块仅提供文档。 一些 **action** 插件则和模块一起执行。 ` normal`  **action ** 插件会执行没有特殊 **action** 插件的模块。 **action** 插件始终在控制节点上执行。 

有一些 **action** 插件在控制节点上就能完成所有的工作。例如：`debug` **action **插件(打印文本供用户查看)和`assert` **action **插件(测试剧本中的值是否满足某些条件)完全在控制节点上执行。

大多数 **action** 插件会在控制节点上设置一些值，然后在受管节点上调用一个模块来对这些值进行处理。 例如：`template` **action **插件使用来自剧本中的变量，在控制节点上的临时目录中构建文件。 然后，它将临时文件传输到远程系统上的临时目录中。 之后，它将调用在远程系统上运行的`copy`模块，以将文件移至其最终位置，再去设置文件属性等信息。 

**action** 插件在`python2.7`的默认存储位置 `/usr/lib/python2.7/site-packages/ansible/plugins/**action**/`

### New-style modules

Ansible附带的所有模块都属于此类别。 您可以使用 **任何语言** 编写模块，但所有官方模块（Ansible附带）均使用Python或`PowerShell`。

新式模块以某种方式将模块的参数嵌入其中。老式的模块需要将参数文件复制到受管节点，这样效率较低，因为它需要两次连接而不是一次连接。

#### Python

新式Python模块使用  [Ansiballz framework](https://docs.ansible.com/ansible/latest/dev_guide/developing_program_flow_modules.html#ansiballz)  框架来构建模块。 这些模块使用来自`ansible.module_utils`的导入的模块代码，例如参数解析，将返回值格式化为`JSON`以及各种文件操作。 

#### PowerShell

新式PowerShell模块使用  [Module Replacer framework](https://docs.ansible.com/ansible/latest/dev_guide/developing_program_flow_modules.html#module-replacer)  框架构建模块。这些模块在被发送到受管节点之前，会获得一个嵌入其中的PowerShell代码文件。 

### JSONARGS modules

使用此模式写的模块一般都是脚本，其主体中包含字符串`<<INCLUDE_ANSIBLE_MODULE_JSON_ARGS>>`。 该字符串就是JSON格式的参数字符串。 如下所示：

```python
json_arguments = """<<INCLUDE_ANSIBLE_MODULE_JSON_ARGS>>"""
```

扩展写法

```python
json_arguments = """{"param1": "test's quotes", "param2": "\"To be or not to be\" - Hamlet"}"""
```

这些模块通常使用JSON库解析`json_arguments`的内容，然后在整个代码中使用它们。

### Non-native want JSON modules

如果模块在任何位置都包含字符串`WANT_JSON`，则Ansible会将其视为非本地模块，该模块接受文件名作为其唯一的命令行参数。 该文件名用于包含JSON字符串（包含模块参数）的临时文件。 模块需要在退出之前打开文件，读取和解析参数，对数据进行操作，并将其返回数据作为JSON编码的字典打印到stdout。 

一个ruby编写的模块

```ruby
#!/usr/bin/ruby
# WANT_JSON

require 'rubygems'
require 'json'

# this is a bare minimum example of a 'facts' module that returns some variables into the ansible
# namespace.  It may not be sufficiently idiomatic and doesn't do a lot of error checking. 

File.open(ARGV[0]) do |fh|

   data = JSON.parse(fh.read())

   begin
      a = data['a'].to_i() 
      b = data['b'].to_i()
   rescue
      # to raise an error, return failed=True and a msg string.

      print JSON.dump({
          'failed' => true,
          'msg'    => 'failed to parse inputs x or y'
      })

      # the error code here is not so important, the JSON is!

      exit(1)
   end

   # we may also wish to return changed=True or changed=False
   # if we were modifying system resources to support handlers and change tracking
   # if the module decides to not run, it can also return skipped=True

   result = {
      'a'   => a,
      'b'   => b,
      'sum' => a + b,
   }

   print JSON.dump(result)

end
```

playbook

```yaml
- hosts: example_servers
  gather_facts: False
  tasks:
    - name: 'call our ruby utility module'
      action: my_ruby_calculator a=7 b=100
      register: my_result
    - action: debug var=my_result
```

实际上的执行

```bash
# cat /path/to/test.json
{
    "a" : 2,
    "b" : 3
}

# ruby ./modules/my_calculator /path/to/test.json
```

### Binary modules

从Ansible 2.2开始，模块也可以是二进制程序。 Ansible并不会处理不同系统的运行时依赖，因此它们自己处理二进制运行时的依赖项。 尽管有这些缺点，但如果这是访问某些资源的唯一方法，则可能必须针对特定的二进制库编译成自定义模块。 

一个go语言的二进制模块 [helloworld.go](https://github.com/ansible/ansible/tree/devel/test/integration/targets/binary_modules/library/helloworld.go)

### Old-style modules

老式模块类似于[want JSON 模块](#New-style modules)，只是它们参数是以`key=value`形式保存在文件中，而不是JSON。 如果模块中没有任何标记可以表明它是其他类型之一，则Ansible会确定该模块为老式模块。 

一个bash脚本的例子

```bash
#!/bin/sh

args_file=$1

[ ! -f "$args_file" ] && echo -n '{"failed": true, "msg": "missing required arguments: file"}' && exit 1
args_result=$(cat $args_file | gawk -F'file=' '{print $2}' | gawk -F' ' '{print $1}')

[ ! -n "$args_result" ] && echo -n "{\"failed\": true, \"msg\": \"file () is absent, cannot continue\", \"file\": \"$args_result\"}" && exit 1

touch $args_result && echo -n "{\"changed\": true, \"rc\": $?,\"file\": \"$args_result\"}" || echo -n "{\"failed\": true, \"rc\": $?, \"file\": \"$args_result\"}"
exit $?
```

参数的形式

```bash
# cat args
file=/tmp/foo

# sh touch.sh args
{"changed": true, "rc": 0,"file": "/tmp/foo"}
```

## 模块是如何执行的

当用户使用`ansible`或`ansible-playbook`时，他们指定要执行的任务。 任务通常是模块的名称以及要传递给模块的几个参数。 在远程计算机上执行之前，Ansible会获取这些值并以各种方式对其进行处理。


### Executor/task_executor

**TaskExecutor** 接收从剧本（或在`/usr/bin/ansible`的情况下从命令行）解析的模块名称和参数。

它使用名称来确定是在查看 **模块** 还是在查看 **Action Plugin**。 如果是模块，它将加载 **"Normal Action Plugin"**，并将名称，变量和有关任务的其他信息传递给该action插件以进行进一步处理。

### `normal` action plugin

`normal` action 插件将在远程主机上执行该模块。在远程主机主要内容就是执行模块。

- 它为任务加载适当的 **连接插件**，然后根据需要传输或执行以创建与该主机的连接。
- 它将Ansible的所有内部属性添加到模块的参数（例如，将no_log传递给模块的属性）。
- 它可以与其他插件（connection, shell, become，其他action插件）一起使用，以在远程计算机上创建临时文件，然后进行清理。
- 它将模块和模块参数推送到远程主机。
- 它处理模块的所有特殊情况（例如，异步执行或Windows模块周围的复杂性，这些模块必须与Python模块具有相同的名称，以便可以从其他Action Plugins进行内部模块调用。 ）

此功能大部分来自`BaseAction`类，该类位于`plugins/action/__ init__.py`中。 它使用`Connection`和`Shell`对象进行工作。

>  当使用`async`参数运行任务时，Ansible将使用 **async** action插件而不是 **normal** action插件来调用它。 



### Executor/module_common.py

`executor/module_common.py` 用于组装要发送到受管节点的模块。 首先读入模块内容，然后检查以确定其类型：

- [PowerShell](#PowerShell) 和 [JSON-args](#JSONARGS modules) 模块通过模块替换器传递。
- 新式Python模块由 Assembler frameworks 组装。
- [Non-native-want-JSON](https://docs.ansible.com/ansible/latest/dev_guide/developing_program_flow_modules.html#flow-want-json-modules), [Binary modules](https://docs.ansible.com/ansible/latest/dev_guide/developing_program_flow_modules.html#flow-binary-modules), 和 [Old-Style modules](https://docs.ansible.com/ansible/latest/dev_guide/developing_program_flow_modules.html#flow-old-style-modules)   不会被改变。

组装步骤完成之后，对所有具有*shebang*的模块进行最后修改。 Ansible检查*shebang*行中的解释器是否具有通过` ansible_$X_interpreter `清单变量配置的特定路径。 如果有，Ansible会将该路径替换为模块中给定的解释器路径。 此后，Ansible将完整的模块数据和模块类型返回到 **normal action** ，该action将继续执行模块。



### Assembler frameworks

Ansible支持两个汇编程序框架：**Ansiballz** 和 **Module Replacer** (旧的)。

#### Module Replacer framework

Module Replacer 框架是实现新型模块的原始框架，并且仍用于`PowerShell`模块。 它本质上是一个预处理器（就像熟悉该编程语言的C预处理器一样）。 它对模块文件中的特定子字符串模式进行直接替换。 有两种类型的替换：

- 仅在模块文件中发生的替换。 这些是模块的公共替换字符串，可用于获取有用的样板或访问参数。
  -  ` from ansible.module_utils.MOD_LIB_NAME import * ` 替换成 `ansible.module_utils.MOD_LIB_NAME` 。这些仅应与新型Python模块一起使用。
  - `#<<INCLUDE_ANSIBLE_MODULE_COMMON>>`等同于`ansible.module_utils.basic import *`，并且也仅适用于新型Python模块。
  - `#POWERSHELL_COMMON`替换`ansible/module_utils/powershell.ps1`的内容。 它只能与新型Powershell模块一起使用。
- `ansible.module_utils`代码使用的替换。 这些是内部替换模式。 它们可以在上面的公共替换中内部使用，但不应直接由模块使用。
  - `<<ANSIBLE VERSION>>`被ANSIBLE VERSION替换。在Ansiballz框架框架下的新型Python模块中，正确的方法是实例化一个`AnsibleModul`e，然后从:attr:`AnsibleModule.ansible_version`访问这个版本。
  - `<<INCLUDE_ANSIBLE_MODULE_COMPLEX_ARGS>>`替换成一个字符串，该字符串是模块参数在Python中的JSON编码。 在JSON字符串上使用`repr`可以安全地嵌入到Python文件中。 在Ansiballz框架下的新型Python模块中，可以通过实例化`AnsibleModule`然后使用`AnsibleModule.params`来更好地进行访问。
  -  `<<SELINUX_SPECIAL_FILESYSTEMS>>`替换成一个字符串，该字符串是以逗号分隔的文件系统列表，这些文件系统在SELinux中具有与文件系统相关的安全上下文。 在新型Python模块中，如果确实需要这样做，则应实例化`AnsibleModule`，然后使用`AnsibleModule._selinux_special_fs`。 该变量还从文件系统名称的逗号分隔字符串更改为文件系统名称的实际python列表。  
  - `<<INCLUDE ANSIBLE MODULE JSON ARGS>>`将MODULE参数替换为JSON字符串。必须注意正确引用字符串，因为JSON数据可能包含引号。这种模式在新型Python模块中没有被替代，因为它们可以通过另一种方式获得模块参数。 
  -  当字符串`syslog.LOG_USER`与syslog工具一起出现时，就会被替换， `syslog_facility`  是在ansible.cfg或任何适用于此主机的 `ansible_syslog_facility`  编目变量中命名的。在新型的Python模块中，这种情况略有改变。如果您确实需要访问它，您应该实例化一个`AnsibleModule`，然后使用`AnsibleModule._syslog_facility`访问它。它不再是实际的syslog工具，现在是syslog工具的名称。

#### Ansiballz framework

Ansiballz框架在Ansible 2.1中采用，并用于所有新型Python模块。 与 **Module Replacer** 不同，Ansiballz在` ansible/module_utils `中使用真实的导入Python对象，而不仅仅是对模块进行预处理。 它通过构造一个zip文件来做到这一点-包括模块文件，模块导入的` ansible/module_utils `中的文件以及一些传递模块参数的样板文件。 然后，对zipfile进行Base64编码，然后将其包装在一个小的Python脚本中，该脚本会解码Base64编码，并将zipfile放入受管节点上的temp目录中。 然后，它仅从zip文件中提取Ansible模块脚本，并将其也放置在临时目录中。 然后，它将`PYTHONPATH`设置为在zip文件中查找Python模块，并将Ansible模块作为特殊名称`__main__`导入。 将其导入为`__main__`会使Python认为它正在执行脚本，而不是简单地导入模块。 这样，Ansible可以在远程计算机上的Python单个副本中运行包装过的脚本和模块代码。

在Ansiballz中，从`ansible.module_utils`包中导入的任何Python模块都会触发将该Python文件包含到zipfile中。模块中`#<<INCLUDE_ANSIBLE_MODULE_COMMON>>`的实例由`ansible.module_utils.basic import *`转换而来。然后，`ansible/module-utils/basic.py`也包含在zipfile中。 自身将扫描`module_utils`中包含的文件，并从`module_utils`中导入其他Python模块，以便将其包含在zip文件中。 

## 参数传递

两个框架通过不同的方式传递参数：

- 在Module Replacer框架中，模块参数被转换成json化的字符串，并被替换到组合的模块文件中。
- 在Ansiballz框架中，json化的字符串是zipfile的一部分。就在包装器脚本将Ansible模块作为主模块导入之前，它用变量值对私有的`_ANSIBLE_ARGS`变量`basic.py`进行了monkey-patch。当`ansible.module_utils.basic.AnsibleModule`实例化时 ， 它将解析此字符串并将args放入`AnsibleModule.params`中，模块的其他代码可以在其中访问它。 

## 内部参数

除了用户在playbook中指定的参数外，Module Replacer框架和Ansiballz框架都向模块发送额外的参数。这些额外的参数是帮助实现全局Ansible特性的内部参数。模块通常不需要明确地知道这些，因为功能是在ansible实现的。模块跑龙套。基本的，但某些功能需要从模块的支持，所以了解他们也是有帮助开发的。

此处列出的内部参数是全局的。 如果需要在自定义模块中添加本地内部参数，请为该特定模块创建一个action插件-有关示例，请参见copy action插件中的`_original_basename`。

### _ansible_no_log

布尔值。 每当task或paly中的参数指定no_log时，并将其设置为True。 任何调用`AnsibleModule.log()`的模块都会自动处理此问题。 如果模块实现自己的日志记录，则需要检查该值。 要访问模块，请实例化`AnsibleModule`，然后检查`AnsibleModule.no_log`的值。

### _ansible_debug

布尔值。 打开或关闭更详细的日志记录，并打开模块执行的外部命令的日志记录。 如果模块使用`AnsibleModule.debug()`而不是`AnsibleModule.log()`，则仅在`_ansible_debug`设置为True时才记录消息。 要进行设置，请在ansible.cfg中添加`debug: true`或设置环境变量ANSIBLE_DEBUG。 要访问模块，请实例化`AnsibleModule`并访问`AnsibleModule._debug`。

### _ansible_diff

布尔值。 如果模块支持，则告诉模块显示要对模板文件进行的更改的统一差异。 要进行设置，请传递`--diff`命令行选项。 要访问模块，请实例化`AnsibleModule`并访问`AnsibleModule._diff`。

### _ansible_verbosity

未使用的。此值可用于对日志进行更细粒度的控制。

### _ansible_selinux_special_fs

列表。 具有特殊SELinux上下文的文件系统的名称。 AnsibleModule方法使用它们，该方法对文件进行操作（更改属性，移动和复制）。 要进行设置，请在ansible.cfg中添加一个用逗号分隔的文件系统名称字符串：

```ini
# ansible.cfg
[selinux]
special_context_filesystems=nfs,vboxsf,fuse,ramfs,vfat
```

大多数模块可以使用内置的AnsibleModule方法来处理文件。 要访问需要了解这些特殊上下文文件系统的模块，请实例化`AnsibleModule`并检查`AnsibleModule._selinux_special_fs`中的列表。

在 Module Replacer 框架中，将替换`ansible.module_utils.basic.SELINUX_SPECIAL_FS `,  在Module Replacer中，它是一个用逗号分隔的文件系统名称字符串。 在Ansiballz下是一个实际列表。

### _ansible_syslog_facility

此参数控制Ansible模块登录到哪个syslog工具。 要进行设置，请更改ansible.cfg中的`syslog_facility`值。 大多数模块应该只使用`AnsibleModule.log()`，然后再利用它。 如果模块必须自己使用它，则应实例化`AnsibleModule`，然后从`AnsibleModule._syslog_facility`检索syslog工具的名称。 Ansiballz代码比旧的Module Replacer框架代码更简洁：

```python
# Old module_replacer way
import syslog
syslog.openlog(NAME, 0, syslog.LOG_USER)

# New Ansiballz way
import syslog
facility_name = module._syslog_facility
facility = getattr(syslog, facility_name, syslog.LOG_USER)
syslog.openlog(NAME, 0, facility)
```

### _ansible_version

此参数传递运行该模块的Ansible版本。 要访问它，模块应实例化`AnsibleModule`，然后从`AnsibleModule.ansible_version`检索它。 这将替换Module Replacer 框架中的`ansible.module_utils.basic.ANSIBLE_VERSION`。

## 模块返回值和不安全字符串

在模块执行结束时，它将要返回的数据格式化为JSON字符串，并将该字符串打印到其标准输出。`normal` action插件接收JSON字符串，将其解析为Python字典，然后将其返回给执行程序。

如果Ansible模板化每个字符串返回值，则很容易受到有权访问受管节点的用户的攻击。 如果不道德的用户将恶意代码伪装成Ansible返回值字符串，然后在控制器上将这些字符串模板化，则Ansible可以执行任意代码。 为了防止出现这种情况，Ansible将返回数据中的所有字符串标记为“Unsafe”，逐字发射字符串中的任何Jinja2模板，而不是Jinja2对其进行扩展。

通过`ActionPlugin._execute_module()`调用模块返回的字符串将由`normal` action插件自动标记为“Unsafe”。 如果另一个action插件通过其他方式从模块检索信息，则它必须自己将其返回数据标记为“Unsafe”。

如果action插件未能将其结果标记为“不Unsafe”，则Ansible在将结果返回给执行程序时会再次审核结果，将所有字符串标记为“Unsafe”。 `normal` action插件以结果数据作为参数来保护自己和它调用的任何其他代码。 执行程序中的检查可保护所有其他action插件的输出，从而确保由Ansible运行的后续任务也不会从这些结果中获取任何模板。

## 特殊事项

### Pipelining

Ansible可以通过以下两种方式之一将模块传输到远程计算机：

- 它可以将模块写到远程主机上的临时文件中，然后使用与远程主机的第二个连接来使用模块所需的解释器执行它
- 或者，它也可以使用Pipelining来执行模块，将模块导入远程解释器的stdin中。

目前，Pipelining仅适用于用Python编写的模块，因为Ansible只知道Python支持这种操作模式。 支持Pipelining意味着，模块有效载荷通过有线发送之前采用的任何格式，都必须由Python通过stdin执行。

### 为什么在stdin传递参数?

选择通过stdin传递参数的原因如下：

- 与`ANSIBLE_PIPELINING`结合使用时，可以防止模块的参数临时保存到远程计算机的磁盘上。 这使得远程计算机上的恶意用户更难（但并非不可能）窃取自变量中可能存在的任何敏感信息。
- 命令行参数是不安全的，因为大多数系统允许非特权用户读取进程的完整命令行。
- 环境变量通常比命令行更安全，但是一些系统限制环境的总体大小。如果达到这个限制，可能会导致参数截断。

## AnsibleModule

### 参数

提供给`AnsibleModule`的`arguments_spec`定义了模块支持的参数，以及它们的类型，默认值和更多内容。

```python
module = AnsibleModule(argument_spec=dict(
    top_level=dict(
        type='dict',
        options=dict(
            second_level=dict(
                default=True,
                type='bool',
            )
        )
    )
))
```

参数的选项

#### type

type允许您定义为参数接受的值的类型。类型的默认值是str。可能的值是

- str
- list
- dict
- bool
- int
- float
- path
- raw
- jsonarg
- json
- bytes
- bits

`raw`类型，不执行任何类型验证或类型大小写，并维护传递值的类型。

#### elements

当`type ='list'`时，elements与type结合使用。 然后可以将elements定义为`elements ='int'`或任何其他类型，指示指定列表中的每个元素都应该属于该类型。

#### default

`default`选项允许在不向模块提供参数的情况下为场景的参数设置默认值。未指定时，默认值为None。

#### fallback

`fallback`接受一个元组，其中第一个参数是一个可调用的（函数），将用于基于第二个参数执行查找。 第二个参数是可调用对象接受的值的列表。

最常用的可调用方法是`env_fallback`，当不提供参数时，它将允许参数有选择地使用环境变量。

```python
username=dict(fallback=(env_fallback, ['ANSIBLE_NET_USERNAME']))
```

#### choices

options接受参数将接受的choices列表。选择的类型应该与类型匹配。

#### required

required接受一个布尔值，True或False表示该参数是必需的。 这不应与默认值结合使用。

#### no_log

no_log接受布尔值（True或False），该布尔值明确指示参数值是否应在日志和输出中屏蔽。

#### aliases

aliases接受参数的替代参数名称的列表，例如参数为`name`但模块接受`aliases=['pkg']`的情况，以允许pkg与`name`互换

#### options

options实现了创建子选项的功能， 本节的示例演示了选项的使用。 在这种情况下，类型或元素应该是dict。

#### apply_defaults

apply defaults与options一起工作，并允许应用子选项的默认值，即使在没有提供顶级参数的情况下也是如此。

#### removed_in_version

`remove_in_version`指明将在哪个Ansible版本中删除不推荐使用的参数。