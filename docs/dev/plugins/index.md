# Plugins

插件可以被所有模块使用，这使Ansible的核心功能得到了有效扩展。您也可以编写自己的插件，所有插件都必须满足以下：

- 使用Python语言编写
- 可以抛出异常
- 返回unicode类型的字符串
- 符合Ansible的配置和文档标准

## 使用Python编写插件

您必须使用Python语言来编写插件，这样插件才能由`PluginLoader`加载并作为任何模块都可以使用的Python对象返回。 由于您的插件将在控制节点上执行，因此您必须使用兼容版本的Python形式来编写它。

## 抛出异常

在插件执行过程中遇到的错误时，您应该由`AnsibleError()`或类似的类返回错误的描述消息。 将其他异常包装到错误消息中时，应始终使用Ansible函数 `to_native` 来确保跨Python版本的字符串兼容性：

```python
from ansible.module_utils._text import to_native

try:
    cause_an_exception()
except Exception as e:
    raise AnsibleError('Something happened, this was original exception: %s' % to_native(e))
```

查看 [AnsibleError objects](https://github.com/ansible/ansible/blob/devel/lib/ansible/errors/__init__.py) 

## 字符串编码

插件返回的所有字符串必须转换为Python的`unicode`类型。 转换为`unicode`可确保这些字符串可以通过`Jinja2`模板使用。 转换字符串示例：

```python
from ansible.module_utils._text import to_text
result_string = to_text(result_string)
```

## 插件文档

`DOCUMENTATION` 变量记录着插件的帮助信息

```python
DOCUMENTATION = '''
    callback: test
    type: stdout
    short_description: test callback
    version_added: historical
    description:
        - test callback description
    options:
      remote_addr:
        description:
            - Address
        default: inventory_hostname
        vars:
            - name: ansible_host
        type: str
'''
```

要访问插件中的配置设置，请使用`self.get_option(<option_name>)`。 对于大多数插件类型，控制器会预先填充设置。 如果需要显式填充设置，请使用`self.set_options()`调用。

## 插件类型


### Action

Action插件允许您在控制节点处理的数据与远程执行的模块功能集成在一起。

要创建action插件，请使用 Base(ActionBase) 类作为父类创建一个新类：

```python
from ansible.plugins.action import ActionBase

class ActionModule(ActionBase):
    pass
```

然后，使用`_execute_module`方法调用原始模块来执行模块代码。成功执行模块后，可以修改模块返回的数据。

```python
module_return = self._execute_module(module_name='<NAME_OF_MODULE>',
                                     module_args=module_args,
                                     task_vars=task_vars, tmp=tmp)
```

例如，如果您想检查Ansible控制节点与目标计算机之间的时间差，则可以编写一个action插件来检查本地时间并将其与setup模块的返回数据进行比较：

```python
#!/usr/bin/python
# Make coding more python3-ish, this is required for contributions to Ansible
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

from ansible.plugins.action import ActionBase
from datetime import datetime


class ActionModule(ActionBase):
    def run(self, tmp=None, task_vars=None):
        super(ActionModule, self).run(tmp, task_vars)
        module_args = self._task.args.copy()
        module_return = self._execute_module(module_name='setup',
                                             module_args=module_args,
                                             task_vars=task_vars, tmp=tmp)
        ret = dict()
        remote_date = None
        if not module_return.get('failed'):
            for key, value in module_return['ansible_facts'].items():
                if key == 'ansible_date_time':
                    remote_date = value['iso8601']

        if remote_date:
            remote_date_obj = datetime.strptime(remote_date, '%Y-%m-%dT%H:%M:%SZ')
            time_delta = datetime.now() - remote_date_obj
            ret['delta_seconds'] = time_delta.seconds
            ret['delta_days'] = time_delta.days
            ret['delta_microseconds'] = time_delta.microseconds

        return dict(ansible_facts=dict(ret))
```

> 该代码检查控制节点上的时间，使用setup模块捕获远程计算机的日期和时间，并计算捕获的时间与本地时间之间的时差，以天，秒和微秒为单位返回时间增量。

获取可用的插件列表

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/action)， 本地安装的存在`/usr/lib/python2.7/site-packages/ansible/plugins/action/`目录中


### Cache

cache 插件用于存储由 inventory 插件搜集到的 **fact** 数据。集合中的cache插件目前只支持 fact 缓存。

使用 cache_loader 导入 cache 插件，以便可以使用`self.set_options()`和`self.get_option(<option_name>)`。 如果直接在代码库中导入 cache  插件，则只能通过`ansible.constants`访问选项，并且会破坏 cache 插件供inventory 插件使用的功能。

```python
from ansible.plugins.loader import cache_loader
[...]
plugin = cache_loader.get('custom_cache', **cache_kwargs)
```

cache 插件有两个基类，用于数据库支持的缓存的`BaseCacheModule`和用于文件支持的缓存的`BaseCacheFileModule`。

要创建 cache 插件，首先要创建一个具有适当基类的新`CacheModule`类。 如果您使用`__init__`方法创建插件，则应使用提供的所有args和kwargs初始化基类，以与 inventory 插件缓存选项兼容。 基类调用`self.set_options(direct=kwargs)`。 在调用基类`__init__`方法后，应使用`self.get_option(<option_name>)`访问缓存选项。

新的cache插件应采用`_uri`，`_prefix`和`_timeout`选项，以与现有的cache插件保持一致。

```python
from ansible.plugins.cache import BaseCacheModule

class CacheModule(BaseCacheModule):
    def __init__(self, *args, **kwargs):
        super(CacheModule, self).__init__(*args, **kwargs)
        self._connection = self.get_option('_uri')
        self._prefix = self.get_option('_prefix')
        self._timeout = self.get_option('_timeout')
```

如果使用`BaseCacheModule`基类创建插件，则必须实现`get`，`contains`，`keys`，`set`，`delete`，`flush`和`copy`方法。 `contains`方法应返回一个布尔值，该值指示密钥是否存在并且尚未过期。 与基于文件的缓存不同，如果缓存过期，则`get`方法不会引发KeyError。

如果使用`BaseFileCacheModule`基类创建插件，则必须实现从基类方法`get`和`set`调用的`_load`和`_dump`方法。

如果您的cache插件存储JSON，请在`_dump`或`set`方法中使用`AnsibleJSONEncoder`，在`_load`或`get`方法中使用`AnsibleJSONDecoder`。

获取可用的插件列表

```bash
ansible-doc -l -t cache
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/cache) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/cache` 目录中找的到。

### Callback

callback 插件可以在事件执行的时候增加新行为，默认情况下，callback 插件在命令行程序执行时，输出大量的信息，比如执行的任务名称，执行时间，任务结果等等信息。

要创建回调插件，请使用Base（Callbacks）类作为父类创建一个新类：

```python
from ansible.plugins.callback import CallbackBase

class CallbackModule(CallbackBase):
    pass
```

在新类中，需要覆盖CallbackBase中的特定方法才能在事件执行的时候执行对应的方法，完整列表见`lib/ansible/plugins/callback/__init__.py`

```
def v2_on_any(self,*args,**kwargs):

def v2_runner_on_failed(self,result,ignore_errors=False):
def v2_runner_on_ok(self,result):
def v2_runner_on_skipped(self,result):
def v2_runner_on_unreachable(self,result):
def v2_runner_on_async_poll(self,result):
def v2_runner_on_async_ok(self,result):
def v2_runner_on_async_failed(self,result):

def v2_playbook_on_start(self,playbook):
def v2_playbook_on_notify(self,handler,host):
def v2_playbook_on_no_hosts_matched(self):
def v2_playbook_on_no_hosts_remaining(self):
def v2_playbook_on_task_start(self,task,is_conditional):
def v2_playbook_on_cleanup_task_start(self,task):
def v2_playbook_on_handler_task_start(self,task):
def v2_playbook_on_vars_prompt(self,varname,private=True,prompt=None,encrypt=None,confirm=False,salt_size=None,salt=None,def ault=None,unsafe=None):
def v2_playbook_on_vars_prompt(self,varname,private=True,prompt=None,encrypt=None,confirm=False,salt_size=None,salt=None,def ault=None,unsafe=None):
self.playbook_on_vars_prompt(varname,private,prompt,encrypt,confirm,salt_size,salt,def ault,unsafe)
def v2_playbook_on_import_for_host(self,result,imported_file):
def v2_playbook_on_not_import_for_host(self,result,missing_file):
def v2_playbook_on_play_start(self,play):
def v2_playbook_on_stats(self,stats):

def v2_on_file_diff(self,result):
def v2_playbook_on_include(self,included_file):
def v2_runner_item_on_ok(self,result):
def v2_runner_item_on_failed(self,result):
def v2_runner_item_on_skipped(self,result):
def v2_runner_retry(self,result):
def v2_runner_on_start(self,host,task):
```

特定方法的result值

```python
print(result._task) # 输出任务名
print(result._host) # 输出主机名
print(result._result) # 输出任务执行的结果
print(result.is_changed) # 是否更改
print(result.is_failed)  # 是否失败

```

以下是Ansible计时器插件的示例，但带有一个附加选项，因此可以在Ansible 2.4版及更高版本中配置使用：

```python
# Make coding more python3-ish, this is required for contributions to Ansible
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

# not only visible to ansible-doc, it also 'declares' the options the plugin requires and how to configure them.
DOCUMENTATION = '''
  callback: timer
  callback_type: aggregate
  requirements:
    - whitelist in configuration
  short_description: Adds time to play stats
  version_added: "2.0"
  description:
      - This callback just adds total play duration to the play stats.
  options:
    format_string:
      description: format of the string shown to user at play end
      ini:
        - section: callback_timer
          key: format_string
      env:
        - name: ANSIBLE_CALLBACK_TIMER_FORMAT
      default: "Playbook run took %s days, %s hours, %s minutes, %s seconds"
'''
from datetime import datetime

from ansible.plugins.callback import CallbackBase


class CallbackModule(CallbackBase):
    """
    This callback module tells you how long your plays ran for.
    """
    CALLBACK_VERSION = 2.0
    CALLBACK_TYPE = 'aggregate'
    CALLBACK_NAME = 'namespace.collection_name.timer'

    # only needed if you ship it and don't want to enable by default
    CALLBACK_NEEDS_WHITELIST = True

    def __init__(self):

        # make sure the expected objects are present, calling the base's __init__
        super(CallbackModule, self).__init__()

        # start the timer when the plugin is loaded, the first play should start a few milliseconds after.
        self.start_time = datetime.now()

    def _days_hours_minutes_seconds(self, runtime):
        ''' internal helper method for this callback '''
        minutes = (runtime.seconds // 60) % 60
        r_seconds = runtime.seconds - (minutes * 60)
        return runtime.days, runtime.seconds // 3600, minutes, r_seconds

    # this is only event we care about for display, when the play shows its summary stats; the rest are ignored by the base class
    def v2_playbook_on_stats(self, stats):
        end_time = datetime.now()
        runtime = end_time - self.start_time

        # Shows the usage of a config option declared in the DOCUMENTATION variable. Ansible will have set it when it loads the plugin.
        # Also note the use of the display object to print to screen. This is available to all callbacks, and you should use this over printing yourself
        self._display.display(self._plugin_options['format_string'] % (self._days_hours_minutes_seconds(runtime)))
```
**callback说明信息**

- CALLBACK_VERSION = 2.0   插件版本
- CALLBACK_TYPE = 'aggregate'  插件类型，如果是'stdout'时，只会加载一个这样的回调插件
- CALLBACK_NAME = 'namespace.collection_name.timer'   插件名称，需与文件名称一致。
- CALLBACK_NEEDS_WHITELIST = True 插件是否需要在配置文件配置whitelist。为true是，ansible检查ansible.cfg文件中的callback_whitelist是否有插件名称，有则执行，无则跳过。


请注意，Ansible 2.0版及更高版本的插件需要`CALLBACK_VERSION`和`CALLBACK_NAME`定义才能正常工作。ansible只加载一个`CALLBACK_TYPE=stdout`的callback插件，如果想执行多个callback插件需设置其他类型。

获取可用的插件列表

```bash
ansible-doc -l -t callback
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/callback) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/callback` 目录中找的到。

### Connection

ansible通过使用connection插件来连接远程系统，以便它可以在目标主机上执行任务。Ansible附带了许多connection插件，但每个主机一次只能使用一个。最常用的connection插件是`paramiko`SSH，本机ssh命令和`local` connection类型。 可以通过在task上配置`connection`关键字来选择用哪种方式连接远程系统。

Ansible 2.1版引入了 `smart` connection插件。 `smart` connection类型允许Ansible根据系统功能自动选择`paramiko`或`openssh` connection插件，如果OpenSSH支持ControlPersist，则选择`ssh` connection插件。

获取可用的插件列表

```bash
ansible-doc -l -t connection
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/connection) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/connection` 目录中找的到。

### Filter

filter插件允许你在`playbook`和`Jinja2`模版内操作数据，ansible使用filter plugin来扩展jinja2模版的功能。Ansible附带的大多数过滤器插件都位于`core.py`中。

filter插件可以不配置`DOCUMENTATION`来说明插件选项和帮助信息。

获取可用的插件列表

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/filter) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/filter` 目录中找的到。

### Inventory

在Ansible 2.4版本中添加了inventory插件，inventory插件用于解析动态资源的主机清单。

获取可用的插件列表

```bash
ansible-doc -l -t inventory
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/inventory) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/inventory` 目录中找的到。

### Lookup

用于从外部数据中提取数据并返回到变量或参数中。比如循环`with_*`的用法。

这是一个简单的查找插件实现，此查找将文本文件的内容作为变量返回

```python
# python 3 headers, required if submitting to Ansible
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

DOCUMENTATION = """
        lookup: file
        author: Daniel Hokka Zakrisson <daniel@hozac.com>
        version_added: "0.9"
        short_description: read file contents
        description:
            - This lookup returns the contents from a file on the Ansible controller's file system.
        options:
          _terms:
            description: path(s) of files to read
            required: True
        notes:
          - if read in variable context, the file can be interpreted as YAML if the content is valid to the parser.
          - this lookup does not understand globing --- use the fileglob lookup instead.
"""
from ansible.errors import AnsibleError, AnsibleParserError
from ansible.plugins.lookup import LookupBase
from ansible.utils.display import Display

display = Display()


class LookupModule(LookupBase):

    def run(self, terms, variables=None, **kwargs):


        # lookups in general are expected to both take a list as input and output a list
        # this is done so they work with the looping construct 'with_'.
        ret = []
        for term in terms:
            display.debug("File lookup term: %s" % term)

            # Find the file in the expected search path, using a class method
            # that implements the 'expected' search path for Ansible plugins.
            lookupfile = self.find_file_in_search_path(variables, 'files', term)

            # Don't use print or your own logging, the display class
            # takes care of it in a unified way.
            display.vvvv(u"File lookup using %s as file" % lookupfile)
            try:
                if lookupfile:
                    contents, show_data = self._loader._get_file_contents(lookupfile)
                    ret.append(contents.rstrip())
                else:
                    # Always use ansible error classes to throw 'final' exceptions,
                    # so the Ansible engine will know how to deal with them.
                    # The Parser error indicates invalid options passed
                    raise AnsibleParserError()
            except AnsibleParserError:
                raise AnsibleError("could not locate file in lookup: %s" % term)

        return ret
```

使用插件

```yaml
---
- hosts: all
  vars:
     contents: "{{ lookup('namespace.collection_name.file', '/etc/foo.txt') }}"

  tasks:

     - debug:
         msg: the value of foo.txt is {{ contents }} as seen today {{ lookup('pipe', 'date +"%Y-%m-%d"') }}
```

获取可用的插件列表

```bash
ansible-doc -l -t lookup
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/lookup) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/lookup` 目录中找的到。

### Shell

很像connection插件，ansible使用shell插件在shell环境中执行，目前支持的shell有csh，fish，powershell，sh。

获取可用的插件列表

```bash
ansible-doc -l -t shell
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/shell) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/shell` 目录中找的到。

### Strategy

控制任务执行流程，

获取可用的插件列表

```bash
ansible-doc -l -t strategy
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/strategy) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/strategy` 目录中找的到。

### Terminal

用来连接cli的硬件设备，像交换机，路由器，防火墙。

获取可用的插件列表

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/terminal) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/terminal` 目录中找的到。

### Test

用于验证数据，属于jinja2的功能。可用于条件指令，例如`when:`。

获取可用的插件列表

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/test) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/test` 目录中找的到。

### Vars

Vars插件将额外的变量数据注入到运行的主机中，而这些运行不是来自库存源、剧本或命令行。如`host_vars`和`group_vars`都是有vars插件来完成的。。

获取可用的插件列表

```bash
ansible-doc -l -t vars
```

官方提供的插件文件可以在 [Ansible Core](https://github.com/ansible/ansible/tree/devel/lib/ansible/plugins/vars) 或本地安装的
`/usr/lib/python2.7/site-packages/ansible/plugins/vars` 目录中找的到。


## 自定义的插件存放位置

1. 在`ansible.cfg`配置的插件目录。

    ```ini
    [defaults]
    # set plugin path directories here, separate with colons
    action_plugins     = /usr/share/ansible/plugins/action
    become_plugins     = /usr/share/ansible/plugins/become
    cache_plugins      = /usr/share/ansible/plugins/cache
    callback_plugins   = /usr/share/ansible/plugins/callback
    connection_plugins = /usr/share/ansible/plugins/connection
    lookup_plugins     = /usr/share/ansible/plugins/lookup
    inventory_plugins  = /usr/share/ansible/plugins/inventory
    vars_plugins       = /usr/share/ansible/plugins/vars
    filter_plugins     = /usr/share/ansible/plugins/filter
    test_plugins       = /usr/share/ansible/plugins/test
    terminal_plugins   = /usr/share/ansible/plugins/terminal
    strategy_plugins   = /usr/share/ansible/plugins/strategy
    ```

2. 在环境变量中指定插件目录。

    ```
    ANSIBLE_ACTION_PLUGINS
    ANSIBLE_CACHE_PLUGINS
    ANSIBLE_CALLBACK_PLUGINS
    ANSIBLE_CONNECTION_PLUGINS
    ANSIBLE_FILTER_PLUGINS
    ANSIBLE_INVENTORY_PLUGINS
    ANSIBLE_LOOKUP_PLUGIN
    ANSIBLE_SHELL_PLUGINS
    ANSIBLE_STRATEGY_PLUGINS
    ANSIBLE_TEST_PLUGINS
    ANSIBLE_VARS_PLUGINS
    ```

3. 放置以下目录，可使ansible自动加载插件

    - `~/.ansible/plugins/` 目录中的插件, 比如`~/.ansible/plugins/callback` 目录中，会自动加载callback插件
    - `/usr/share/ansible/plugins/`目录中的插件，比如`/usr/share/ansible/plugins/callback` 目录中，会自动加载callback插件
    - 当您的Playbook同目录下或角色中有以下子文件夹之一时，插件会自动加载：

        ```
        action_plugins
        cache_plugins
        callback_plugins
        connection_plugins
        filter_plugins
        inventory_plugins
        lookup_plugins
        shell_plugins
        strategy_plugins
        test_plugins
        vars_plugins
        ```
