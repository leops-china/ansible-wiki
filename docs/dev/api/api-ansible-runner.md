# Ansible Runner

[Ansible Runner](https://github.com/ansible/ansible-runner)是ansible官方提供的一个工具和python库，当直接与Ansible进行交互或作为另一个系统的一部分与Ansible进行交互时，无论是通过容器映像接口，作为独立工具还是作为可以导入的Python模块，它都可以提供帮助。 目的是为Ansible提供稳定且一致的接口抽象。

**Ansible Runner** 在 [Ansible Tower / AWX](https://github.com/ansible/awx)中负责运行`ansible`和`ansible-playbook`任务的部分模块化，并从中收集输出。即使 **Ansible** 本身在成长和发展，它也会提供一个不变的通用接口。

详细文档请看 https://ansible-runner.readthedocs.io/en/latest/



## 环境

- os `Centos 7.7 X64`
- ansible `2.9.6.0`
- python `2.7.5`



## 安装

```bash
yum -y install gcc python-devel python-pip
pip install ansible_runner
```



## 示例

```python
#!/bin/env python
#! coding: utf-8

import ansible_runner

data_dir = "/tmp/demo"
myhosts = "/etc/ansible/hosts"

print("执行module")
m = ansible_runner.run(private_data_dir=data_dir, inventory=myhosts, host_pattern='localhost', module='shell', module_args='whoami', extravars={"ansible_ssh_pass": "123456"})

print("{}: {}".format(m.status, m.rc))
# successful: 0
for each_host_event in m.events:
    print(each_host_event['event'])
print("Final status:", m.stats)


print("执行playbook")
# config配置
rc = ansible_runner.RunnerConfig(private_data_dir=data_dir, playbook='/etc/ansible/test.yml', inventory=myhosts,extravars={"ansible_test": "test_playbook"})
# 基本检查
rc.prepare()
# 执行
r = ansible_runner.Runner(config=rc)
p = r.run()
if 'failed' in p:
  print('Exec error:', p)
else:
  # successful: 0
  for each_host_event in r.events:
      print(each_host_event['event'])
  print("Final status:", p[1])
```

执行结果

```bash
# python test_api.py 
执行module
localhost | CHANGED | rc=0 >>
root
successful: 0
playbook_on_start
runner_on_start
runner_on_ok
playbook_on_stats
('Final status:', {'dark': {}, 'skipped': {}, 'ok': {u'localhost': 1}, 'processed': {u'localhost': 1}, 'failures': {}, 'changed': {u'localhost': 1}})
执行playbook

PLAY [all] *********************************************************************

TASK [hello] *******************************************************************
ok: [localhost] => {
    "msg": "hello, ansible."
}

TASK [show var] ****************************************************************
ok: [localhost] => {
    "ansible_test": "test_playbook"
}

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

playbook_on_start
playbook_on_start
runner_on_start
playbook_on_play_start
runner_on_ok
playbook_on_task_start
playbook_on_stats
runner_on_start
runner_on_ok
playbook_on_task_start
runner_on_start
runner_on_ok
playbook_on_stats
('Final status:', 0)
```



### RunnerConfig的参数列表

```
private_data_dir=None
playbook=None
ident=uuid4()
inventory=None
roles_path=None
limit=None
module=None
module_args=None
verbosity=None
quiet=False
json_mode=False
artifact_dir=None
rotate_artifacts=0
host_pattern=None
binary=None
extravars=None
suppress_ansible_output=False
process_isolation=False
process_isolation_executable=None
process_isolation_path=None
process_isolation_hide_paths=None
process_isolation_show_paths=None
process_isolation_ro_paths=None
resource_profiling=False
resource_profiling_base_cgroup='ansible-runner'
resource_profiling_cpu_poll_interval=0.25
resource_profiling_memory_poll_interval=0.25
resource_profiling_pid_poll_interval=0.25
resource_profiling_results_dir=None
tags=None
skip_tags=None
fact_cache_type='jsonfile'
fact_cache=None
ssh_key=None
project_dir=None
directory_isolation_base_path=None
envvars=None
forks=None
cmdline=None
omit_event_data=False
only_failed_event_data=False
```

