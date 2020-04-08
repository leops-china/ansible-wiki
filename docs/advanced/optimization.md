# Ansible 优化

Ansible 默认情况下，没有做任何的优化。通过下列的几种方式，可以在执行效率，时间上做进一步的优化。

## Profile_tasks

开启Ansible任务的执行时间, 可有助于我们了解playbook中的task任务执行时间，以便于后续优化。

在 `ansible.cfg` 中配置

```ini
[defaults]
callback_whitelist = timer, profile_tasks
```

## Fork

Ansible 默认情况下，并行执行的数量是`5`，对于较多的节点，就需要扩大这个并行数量。

> Fork 数量越大对控制节点的cpu消耗越高。

在 `ansible.cfg` 中配置

```ini
[defaults]
forks = 20
```

## Poll_interval

降低轮询间隔时间，有助于加快获取任务结果。

在 `ansible.cfg` 中配置

```ini
[defaults]
poll_interval  = 1
internal_poll_interval = 0.001
```

## Fact cache

将 Facts 信息第一次收集后缓存到memory或者redis或者文件中，从而为后续执行减少收集时间。

在 `ansible.cfg` 中配置

```ini
[defaults]
fact_caching            = jsonfile
fact_caching_connection = /tmp/.ansible_fact_cache
```

## Gather_subset

可选择性的收集network,hardware等信息，而不是全部

在 `ansible.cfg` 中配置

```ini
# 在配置文件中,排除收集
[defaults]
gather_subset=!hardware
```

也可以在在play中定义

```yaml
# 不收集数据
- hosts: whatever
  gather_facts: no

# 只收集minimal
- hosts: all
  gather_facts: False
  pre_tasks:
   - setup:
      gather_subset:
       - '!all'
```

## SSH 连接参数

增加control_path的使用时间

在 `ansible.cfg` 中配置

```ini
[ssh_connection]
ssh_args = -o ControlMaster=auto -o ControlPersist=1800s
```

默认ssh的认证方式会有 `-o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey`, 如果只有publickey一种方式认证，可以只指定publickey `-o PreferredAuthentications=publickey`

## Control_path
开启ssh socket持久化，复用ssh连接。

在 `ansible.cfg` 中配置

``` ini
[ssh_connection]
control_path = %(directory)s/ansible-ssh-%%h-%%p-%%r
```

## Pipelinling
开启ssh pipelining,客户端从管道中读取执行渲染后的脚本，而不是在客户端创建临时文件。

在 `ansible.cfg` 中配置

```ini
[ssh_connection]
pipelining = True
```

## Serial
 
将play_hosts中主机再分批执行,降低控制机的cpu使用

```yaml  
- hosts: whatever
  serial：50%
```

## Strategy

默认linear,每个主机的单个task执行完成会等待其他都完成后再执行下个任务，设置free可不等待其他主机。
```yaml
- hosts: web-servers
  strategy: linear
```

## mitogen strategy 插件

提高ansible的执行效率，比原生执行速度提高1.25x-7x，CPU减少2倍的使用。

下载
```bash
wget https://networkgenomics.com/try/mitogen-0.2.9.tar.gz
tar zxf mitogen-0.2.9.tar.gz /path/to/
```

在 `ansible.cfg` 中配置
```ini
[defaults]
strategy_plugins = /path/to/mitogen-0.2.9/ansible_mitogen/plugins/strategy
strategy = mitogen_linear
```

也可在play中设置

```yaml
- hosts: web-servers
  strategy: mitogen_linear
```

执行

```bash
ANSIBLE_STRATEGY_PLUGINS=/path/to/mitogen-0.2.9/ansible_mitogen/plugins/strategy ansible-playbook test.yaml
```


更多内容见[mitogen介绍](https://mitogen.networkgenomics.com/ansible_detailed.html)

