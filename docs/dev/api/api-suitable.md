# 使用 suitable

前面我们使用了官方提供的内部API接口，因为是ansible内部使用的，所以入手还是比较难的，这里我们使用一个开源的对ansible api进行封装后的一个项目 [suitable](https://github.com/seantis/suitable)，关于它到详细信息可以查看 [项目文档](http://suitable.readthedocs.org)。

本文仅用小例子来简单使用suitable。

## 环境

- os `Centos 7.7 X64`
- ansible `2.9.6.0`
- python `2.7.5`

## 安装

```bash
pip install suitable
```

## 示例

```python
from suitable import Api

api = Api(servers=['192.168.77.130'],
                  connection='smart',
                  remote_user='root',
                  remote_pass='123456',
                  become=True,
                  become_user='root',
                  sudo=True,
                  ssh_extra_args='-o StrictHostKeyChecking=no')

facts_data = api.setup()

shell_result = api.shell('whoami')

command_result = api.command('whoami')

print('facts:', facts_data)
print('shell:', shell_result)
print('command:', command_result)
```

执行结果

```bash
# python test.py 
('facts:', {'unreachable': {}, 'contacted': {'192.168.77.130': {'_ansible_no_log': False, 'success': True, u'invocation': {u'module_args': {u'filter': u'*', u'gather_subset': [u'all'], u'fact_path': u'/etc/ansible/facts.d', u'gather_timeout': 10}}, 'changed': False, '_ansible_verbose_override': True, u'ansible_facts': {u'ansible_processor_count': 
..... # 省略一大部分内容
u'cap_sys_tty_config', u'cap_mknod', u'cap_lease', u'cap_audit_write', u'cap_audit_control', u'cap_setfcap', u'cap_mac_override', u'cap_mac_admin', u'cap_syslog', u'35', u'36', u'37+ep'], u'ansible_processor_threads_per_core': 1, u'ansible_product_name': u'VMware Virtual Platform', u'ansible_all_ipv4_addresses': [u'172.17.0.1', u'192.168.77.130'], u'ansible_python_version': u'2.7.5'}}}})

('shell:', {'unreachable': {}, 'contacted': {'192.168.77.130': {'stderr_lines': [], u'changed': True, u'end': u'2020-05-04 22:30:18.457327', '_ansible_no_log': False, 'success': True, u'stdout': u'root', u'cmd': u'whoami', u'start': u'2020-05-04 22:30:18.408973', u'delta': u'0:00:00.048354', u'stderr': u'', u'rc': 0, u'invocation': {u'module_args': {u'warn': True, u'executable': None, u'_uses_shell': True, u'strip_empty_ends': True, u'_raw_params': u'whoami', u'removes': None, u'argv': None, u'creates': None, u'chdir': None, u'stdin_add_newline': True, u'stdin': None}}, 'stdout_lines': [u'root'], 'ansible_facts': {u'discovered_interpreter_python': u'/usr/bin/python'}}}})

('command:', {'unreachable': {}, 'contacted': {'192.168.77.130': {'stderr_lines': [], u'changed': True, u'end': u'2020-05-04 22:30:18.741639', '_ansible_no_log': False, 'success': True, u'stdout': u'root', u'cmd': [u'whoami'], u'start': u'2020-05-04 22:30:18.737730', u'delta': u'0:00:00.003909', u'stderr': u'', u'rc': 0, u'invocation': {u'module_args': {u'warn': True, u'executable': None, u'_uses_shell': False, u'strip_empty_ends': True, u'_raw_params': u'whoami', u'removes': None, u'argv': None, u'creates': None, u'chdir': None, u'stdin_add_newline': True, u'stdin': None}}, 'stdout_lines': [u'root'], 'ansible_facts': {u'discovered_interpreter_python': u'/usr/bin/python'}}}})
```

## API 参数

列出常用的参数

### servers

主机列表的示例

```
api = Api(['web.example.org', 'db.example.org'])
api = Api('web.example.org')
api = Api('web.example.org db.example.org')
api = Api({'web.example.org': {'ansible_host': '10.10.5.1'}})
api = Api(['example.org:2222', 'example.org:2223'])
```

### sudo

用于提权

```bash
Api('example.org', become=True, become_user='root', become_method='sudo 'become_pass=‘123456’)
```

### environment

设置环境变量

```bash
api = Api('example.org', environment={
                    'PGPORT': '5432'
                })
```

### extra_vars

设置额外变量，这些变量是全局变量

```python
api = Api('example.org', extra_vars={
                    'ansible_python_interpreter': '/path/to/interpreter'
                })
```

### 其他参数

```
ignore_unreachable
ignore_errors
host_key_checking
sudo
dry_run
strategy
forks
private_key_file
ssh_common_args
ssh_extra_args
sftp_extra_args
scp_extra_args
extra_vars
diff
verbosity
check
```

更多详细信息可以查看 [项目文档](http://suitable.readthedocs.org)。