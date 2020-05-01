# BlackHole Callback

## 需求
执行命令时，什么都不显示。把回显内容丢到黑洞去。

## 编写插件

在 `/etc/ansible/callback_plugins` 目录中创建`BlackHole.py` 文件，文件内容如下：

```python
# Make coding more python3-ish, this is required for contributions to Ansible
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

from ansible.plugins.callback import CallbackBase

class CallbackModule(CallbackBase):

    '''
    Magic black hole, nothing will show up.
    '''
    CALLBACK_VERSION = 2.0
    CALLBACK_TYPE = 'stdout'
    CALLBACK_NAME = 'BlackHole'

    # only needed if you ship it and don't want to enable by default
    CALLBACK_NEEDS_WHITELIST = True

    def v2_on_any(self, *args, **kwargs):
        pass

    def v2_runner_on_failed(self, result, ignore_errors=False):
        pass

    def v2_runner_on_ok(self, result):
        pass

    def v2_runner_on_skipped(self, result):
        pass

    def v2_runner_on_unreachable(self, result):
        pass

    def v2_runner_on_async_poll(self, result):
        pass

    def v2_runner_on_async_ok(self, result):
        pass

    def v2_runner_on_async_failed(self, result):
        pass

    def v2_playbook_on_start(self, playbook):
        pass

    def v2_playbook_on_notify(self, handler, host):
        pass

    def v2_playbook_on_no_hosts_matched(self):
        pass

    def v2_playbook_on_no_hosts_remaining(self):
        pass

    def v2_playbook_on_task_start(self, task, is_conditional):
        pass

    def v2_playbook_on_cleanup_task_start(self, task):
        pass

    def v2_playbook_on_handler_task_start(self, task):
        pass

    def v2_playbook_on_vars_prompt(self, varname, private=True, prompt=None, encrypt=None, confirm=False, salt_size=None, salt=None, ault=None, unsafe=None):
        pass

    def v2_playbook_on_import_for_host(self, result, imported_file):
        pass

    def v2_playbook_on_not_import_for_host(self, result, missing_file):
        pass

    def v2_playbook_on_play_start(self, play):
        pass

    def v2_playbook_on_stats(self, stats):
        pass

    def v2_on_file_diff(self, result):
        pass

    def v2_playbook_on_include(self, included_file):
        pass

    def v2_runner_item_on_ok(self, result):
        pass

    def v2_runner_item_on_failed(self, result):
        pass

    def v2_runner_item_on_skipped(self, result):
        pass

    def v2_runner_retry(self, result):
        pass

    def v2_runner_on_start(self, host, task):
        pass

```

> 将callback所有的v2回调方法都重写，并且不做任何处理



## 配置 ansible.cfg

```ini
[defaults]
callback_plugins = /etc/ansible/callback_plugins    # 插件目录
stdout_callback = BlackHole                         # stdout 插件
callback_whitelist = BlackHole                      # callback 插件白名单
```

## 执行 playbook

```bash
# cat test.yml 
---

- hosts: localhost

  tasks:
   - debug: msg="hello"

# ansible-playbook test_BlackHole.yml
# ansible-playbook test_BlackHole.yml -vvvv
ansible-playbook 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible-playbook
  python version = 2.7.5 (default, Aug  7 2019, 00:51:29) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
Using /etc/ansible/ansible.cfg as config file
setting up inventory plugins
host_list declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
script declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
auto declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
Parsed /etc/ansible/hosts inventory source with ini plugin
Loading callback plugin BlackHole of type stdout, v2.0 from /etc/ansible/callback_plugins/BlackHole.py
1 plays in test_BlackHole.yml
Using module file /usr/lib/python2.7/site-packages/ansible/modules/system/setup.py
Pipelining is enabled.
<127.0.0.1> ESTABLISH LOCAL CONNECTION FOR USER: root
<127.0.0.1> EXEC /bin/sh -c '/usr/bin/python2 && sleep 0'
META: ran handlers
META: ran handlers
META: ran handlers

```
是不是很神奇呀！playbook 输出信息都没了。



## 执行 ad-hoc 命令

ansible ad-hoc 命令默认使用 `minimal` callback插件，如果要使用自定义的callback插件时，需要添加`bin_ansible_callbacks`参数才能使用。

在配置文件中添加
```ini
[defaults]
bin_ansible_callbacks=True
```

或者设置环境变量开启

``` bash
export ANSIBLE_LOAD_CALLBACK_PLUGINS=1
```

```bash
# ansible localhost -m ping
# ansible localhost -m ping -vvvv
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Aug  7 2019, 00:51:29) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
Using /etc/ansible/ansible.cfg as config file
setting up inventory plugins
host_list declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
script declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
auto declined parsing /etc/ansible/hosts as it did not pass its verify_file() method
Parsed /etc/ansible/hosts inventory source with ini plugin
Loading callback plugin BlackHole of type stdout, v2.0 from /etc/ansible/callback_plugins/BlackHole.pyc
META: ran handlers
Using module file /usr/lib/python2.7/site-packages/ansible/modules/system/ping.py
Pipelining is enabled.
<127.0.0.1> ESTABLISH LOCAL CONNECTION FOR USER: root
<127.0.0.1> EXEC /bin/sh -c '/usr/bin/python2 && sleep 0'
META: ran handlers
META: ran handlers

```
ad-hoc 的执行输出也没了，全部丢入黑洞啦。