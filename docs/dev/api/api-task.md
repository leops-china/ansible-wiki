# 使用 API 运行 task

## 需求

使用 Ansible API的方式执行task任务

## 环境

- os `Centos 7.7 X64`
- ansible `2.9.6.0`
- python `2.7.5`

## api 示例

```python
#!/usr/bin/env python
#! coding: utf-8


import json
import shutil
from ansible.module_utils.common.collections import ImmutableDict
from ansible.parsing.dataloader import DataLoader
from ansible.vars.manager import VariableManager
from ansible.inventory.manager import InventoryManager
from ansible.playbook.play import Play
from ansible.executor.task_queue_manager import TaskQueueManager
from ansible.plugins.callback import CallbackBase
from ansible import context
import ansible.constants as C

class ResultCallback(CallbackBase):
    """自定义 callback，即在运行 api 后调用本类中的 v2_runner_on_ok()
    """
    def v2_runner_on_ok(self, result, **kwargs):
        """打印一个json数据的结果
        """
        host = result._host
        print(json.dumps({host.name: result._result}, indent=4))
        print('---')

# 设置ansible选项
context.CLIARGS = ImmutableDict(connection='local', module_path=['/to/mymodules'], forks=10, become=None,
                                become_method=None, become_user=None, check=False, diff=False)

# 需要初始化的对象
loader = DataLoader() # 负责查找和读取yaml，json和ini文件

# 设置主机密码，主机未定义密码的时候才生效，conn_pass指连接远端的密码，become_pass指提升权限的密码
passwords = dict(conn_pass='123456', become_pass='123456')

# 实例化ResultCallback，来处理输出结果
results_callback = ResultCallback()

# 创建主机清单，使用path作为配置文件的源文件，或者用逗号分隔的字符串作为主机
inventory = InventoryManager(loader=loader, sources='localhost,')

# 变量管理器负责合并所有不同的源
variable_manager = VariableManager(loader=loader, inventory=inventory)

# 创建数据结构, 这里基本上我们yaml文件定义的信息
play_source =  dict(
        name = "Ansible Play", # paly name
        hosts = 'localhost', # patterns
        gather_facts = 'no', # paly 关键字
        tasks = [
            dict(action=dict(module='shell', args='ls'), register='shell_out'),
            dict(action=dict(module='debug', args=dict(msg='{{shell_out.stdout}}')))
         ]
    )

# 创建play对象，playbook会使用这个对象
play = Play().load(play_source, variable_manager=variable_manager, loader=loader)

# 实例化任务队列管理器，它负责创建和设置所有对象来遍历主机列表和任务
tqm = None
try:
    tqm = TaskQueueManager(
              inventory=inventory,
              variable_manager=variable_manager,
              loader=loader,
              passwords=passwords,
              stdout_callback=results_callback,  # 使用自定义的callback插件，默认是`default`插件
          )
    result = tqm.run(play) # 在队列中执行play
    print('任务执行返回码: %s' % result)  # 返回码，只要有一个 host 出错就会返回 非0 数字
finally:
    # 总是要清理子进程和其通信信息
    if tqm is not None:
        tqm.cleanup()

    # 删除 ansible 临时目录
    shutil.rmtree(C.DEFAULT_LOCAL_TMP, True)
```

执行结果

```bash
# python test-api.py 
{
    "localhost": {
        "stderr_lines": [], 
        "changed": true, 
        "end": "2020-05-03 23:02:39.296937", 
        "_ansible_no_log": false, 
        "stdout": "ansible.cfg\nasynctest.yaml\ncallback_plugins\ncsv_inventory\ndebuger.yaml\nfilter_plugins\ngroup_vars\nhosts\nlibrary\nplugins\nroles\nsplit.yml\ntest-api.py\ntest_black_hole.yml\ntest_inventory_script.yml\ntest_remote_copy.yml\ntest_touch.yml\ntest.yml", 
        "cmd": "ls", 
        "start": "2020-05-03 23:02:39.292814", 
        "delta": "0:00:00.004123", 
        "stderr": "", 
        "rc": 0, 
        "invocation": {
            "module_args": {
                "warn": true, 
                "executable": null, 
                "_uses_shell": true, 
                "strip_empty_ends": true, 
                "_raw_params": "ls", 
                "removes": null, 
                "argv": null, 
                "creates": null, 
                "chdir": null, 
                "stdin_add_newline": true, 
                "stdin": null
            }
        }, 
        "stdout_lines": [
            "ansible.cfg", 
            "asynctest.yaml", 
            "callback_plugins", 
            "csv_inventory", 
            "debuger.yaml", 
            "filter_plugins", 
            "group_vars", 
            "hosts", 
            "library", 
            "plugins", 
            "roles", 
            "split.yml", 
            "test-api.py", 
            "test_black_hole.yml", 
            "test_inventory_script.yml", 
            "test_remote_copy.yml", 
            "test_touch.yml", 
            "test.yml"
        ], 
        "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python"
        }
    }
}
---
{
    "localhost": {
        "msg": "ansible.cfg\nasynctest.yaml\ncallback_plugins\ncsv_inventory\ndebuger.yaml\nfilter_plugins\ngroup_vars\nhosts\nlibrary\nplugins\nroles\nsplit.yml\ntest-api.py\ntest_black_hole.yml\ntest_inventory_script.yml\ntest_remote_copy.yml\ntest_touch.yml\ntest.yml", 
        "changed": false, 
        "_ansible_verbose_always": true, 
        "_ansible_no_log": false
    }
}
---
任务执行返回码: 0
```

## TaskQueueManager 字段说明

- `inventory` --> 由ansible.inventory模块创建，用于导入inventory文件
- `variable_manager` --> 由ansible.vars模块创建，用于存储各类变量信息
- `loader` --> 由ansible.parsing.dataloader模块创建，用于数据解析
- `passwords` --> 登录密码，可设置加密信息
- `stdout_callback` --> 回调函数
- `run_tree` --> 是否以tree模式运行
- `forks` --> 设置并行数

## TaskQueueManager.run方法的返回状态码

    RUN_OK                = 0    
    RUN_ERROR             = 1  
    RUN_FAILED_HOSTS      = 2
    RUN_UNREACHABLE_HOSTS = 4
    RUN_FAILED_BREAK_PLAY = 8
    RUN_UNKNOWN_ERROR     = 255
