# 15. Playbook 高级特性 

## 权限提升

Ansible使用现有的权限升级系统来执行具有`root`权限或其他用户权限的任务。因为这个特性允许您成为另一个用户，与登录到机器的用户(远程用户)不同，所以我们将其称为`become`。`become`关键字利用现有的权限升级工具，如`sudo`、`su`、`pfexec`、`doas`、`pbrun`、`dzdo`、`ksu`、`runas`、`machinectl`等。 

### 使用become

你可以在 `play`或 `task` 上使用`become`，同时使用时，优先级规则会决定哪个生效。



#### become 指令

- become  设置`yes`即开启提升权限
- become_user  指定提升权限的用户
- become_method  指定提升权限的方式，有sudo，su，runas等。
- become_flags 传给可执行文件的参数

例如，启动服务需要`root`权限

```yaml
- name: Ensure the httpd service is running
  service:
    name: httpd
    state: started
  become: yes
```

以apache用户身份运行命令

```yaml
- name: Run a command as the apache user
  command: somecommand
  become: yes
  become_user: apache
```

当shell为nologin时，作为nobody用户执行某些操作

```yaml
- name: Run a command as nobody
  command: somecommand
  become: yes
  become_method: su
  become_user: nobody
  become_flags: '-s /bin/sh'
```

#### become 变量

在主机清单中可以为节点定义不同的`become`选项，使用下列变量

- ansible_become 开启提升权限
- ansible_become_method  提升权限的方式，有sudo，su，runas等。
- ansible_become_user  提升权限的用户
- ansible_become_pass 提升权限的用户密码

例如，如果您希望在一个名为webserver的服务器上以root身份运行所有任务，但是您只能作为manager用户连接，那么您可以使用类似这样的库存条目 

```ini
webserver ansible_user=manager ansible_become=yes
```

#### become 命令行选项

- --become，-b
- --ask-become-pass, -K  告诉程序提升权限的用户密码
- --become-method  提升权限的方式，有sudo，su，runas等。
- --become-user  提升权限的用户


```bash
ansible -i hosts node1 -m shell -a "whoami" --become  --become-method=su --become-user=root --ask-become-pass

ansible-playbook -i hosts test.yml --become  --become-method=su --become-user=root --ask-become-pass
```

#### become的一些限制和风险

- 成为无特权用户的风险
- 不是所有的连接插件都支持特权升级
- 每个主机只能启用一个特权升级模式(su,sudo...)
- 特权升级不能限制某些命令能升级，这样会导致ansible执行时出现错误。
- 不能访问由` pam_systemd `填充的环境变量

### 网络模块使用become

从2.6版开始，Ansible在所有支持enable模式的网络设备上进行特权升级(进入enable模式或特权EXEC模式) 

你必须将连接类型设置为`connection: network_cli`或`connection: httpapi`，才能在网络设备上使用`become`进行权限升级。 



若要设置特定任务的`enable`模式，请在任务级别上添加`become`

```yaml
- name: Gather facts (eos)
  eos_facts:
    gather_subset:
      - "!hardware"
  become: yes
  become_method: enable
```

若要为单个play中的所有任务设置`enable`模式，请在play级别上添加`become `

```yaml
- hosts: eos-switches
  become: yes
  become_method: enable
  tasks:
    - name: Gather facts (eos)
      eos_facts:
        gather_subset:
          - "!hardware"
```

#### 设置所有任务的`enable`模式

通常，您希望所有play中的所有任务都使用特权模式运行，这最好通过使用组变量来实现

```yaml
ansible_connection: network_cli
ansible_network_os: eos
ansible_user: myuser
ansible_become: yes
ansible_become_method: enable
```

####  enable模式的密码

如果需要密码才能进入`enable`模式，可以通过以下两种方式之一进行指定

- 提供 `--ask-become-pass`命令行选项 
- 设置` ansible_become_password ` 连接变量 

#### authorize 和 auth_pass

ansible 依然支持 ` connection: local ` 连接下的`enable`模式

```yaml
- hosts: eos-switches
  ansible_connection: local
  tasks:
    - name: Gather facts (eos)
      eos_facts:
        gather_subset:
          - "!hardware"
      provider:
        authorize: yes
        auth_pass: " {{ secret_auth_pass }}"
```



### windows 使用become

从Ansible 2.3开始，可以通过`runas`方法在Windows主机上使用`become`。在Windows上的Become使用与在非Windows主机上相同的库存设置和调用参数，因此设置和变量名与本文档中定义的相同。 

Windows中的许多任务需要管理权限才能完成。当使用runas become方法时，Ansible将尝试使用远程用户可用的全部特权运行模块。如果未能提升用户令牌，则在执行期间将继续使用有限的令牌。 



用户必须具有`SeDebugPrivilege`才能运行具有提升特权的成为进程。这个特权默认分配给管理员。如果调试特权不可用，则become进程将使用一组有限的特权和组运行。 

```yaml
- win_whoami:
  become: yes
```

在返回的`label.account_name`中体现了是否获取特权

- `Medium`: Ansible未能得到提升的令牌，并运行在一个有限的令牌。 

- `High`: 获得了提升的令牌，并在任务中使用

- ` System`:  `NT AUTHORITY\System`帐户被使用，并且具有最高级别的可用特权。

  

如果在大于2.5的Ansible版本上运行或正常的runas升级过程失败，可以通过 

- 将`become_user`设置为`System` 以便拥有最高权限

- 为WinRM连接用户授予`SeTcbPrivilege`权限， `SeTcbPrivilege`是一种高级特权，它授予对操作系统的完全控制。您可以使用下面的任务在Windows主机上设置此特权

 ```yaml
  - name: grant the ansible user the SeTcbPrivilege right
    win_user_right:
      name: SeTcbPrivilege
      users: '{{ansible_user}}'
      action: add
 ```

-  关闭主机上的UAC并重启主机, UAC是一种安全协议，它被设计为使用最少特权原则运行帐户。您可以通过运行以下任务来关闭UAC 

 ```yaml
  - name: turn UAC off
    win_regedit:
      path: HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system
      name: EnableLUA
      data: 0
      type: dword
      state: present
    register: uac_result
  
  - name: reboot after disabling UAC
    win_reboot:
    when: uac_result is changed
 ```

> 授予`SeTcbPrivilege`或关闭UAC可能会导致Windows安全漏洞，如果采取了这些步骤，应该谨慎对待。 


#### LocalService账号

在Ansible 2.5版本之前，become只能在本地或域用户帐户的Windows上工作。在这些旧版本中，像`System`或`NetworkService`这样的本地服务帐户不能用作用户。自Ansible 2.5发布以来，这一限制已经解除。可以在成为用户下面设置的三个服务帐户是 

- System
- NetworkService
- LocalService

由于本地服务帐户没有密码，所以`ansible_become_password`参数不是必需的，如果指定了该参数也会被被忽略。

#### 无需为become设置密码

从Ansible 2.8开始，become可以被用来成为一个Windows本地或域帐户，而不需要该帐户的密码。要使此方法工作，必须满足以下要求



- 该连接用户拥有` SeDebugPrivilege`权限

- 该连接用户属于` BUILTIN\Administrators `组

- 该连接用户拥有`SeBatchLogonRight`或`SeNetworkLogonRight`用户权限

  

通过两种不同的方法之一可以使用使用无密码方式：

- 复制现有的登录会话令牌(如果帐户已经登录)

- 使用S4U生成仅在远程主机上有效的登录令牌


#### 没有密码的帐户

Ansible可以使用一个没有密码的Windows帐户(像Guest帐户)。要成为一个没有密码的帐户，必须设置` ansible_become_password: '' `。

要想实现无密码登录，还需要将本地策略帐户:将本地帐户使用空白密码限制为仅用于控制台登录禁用。这可以通过组策略对象(GPO)完成，也可以通过这个可能的任务完成 

```yaml
- name: allow blank password on become
  win_regedit:
    path: HKLM:\SYSTEM\CurrentControlSet\Control\Lsa
    name: LimitBlankPasswordUse
    data: 0
    type: dword
    state: present
```

#### become的参数

windows支持的`ansible_become_flags`有两个` logon_type` ,  ` logon_flags `

` logon_type`  是指定登录操作类型，有以下可选项:

-  interactive:  默认登录类型。该流程将在与本地运行流程相同的上下文中运行。这绕过了所有的WinRM限制，是推荐使用的方法。 

-  batch: 在类似于设置了密码的调度任务的批处理上下文中运行该进程。

-  new_credentials:  在与调用用户相同的凭据下运行

-  network:  在没有任何缓存凭据的网络上下文中运行进程。

-  network_cleartext: 与网络登录类型类似，但缓存凭据以便它可以访问网络资源。

` logon_flags `指定在创建新进程时，Windows将如何记录用户的登录。 有以下可选项:

-  with_profile：  默认值。 该过程会将HKEY_USERS注册表项中的用户个人资料加载到HKEY_CURRENT_USER。 
-  netcredentials_only：  该过程将使用与调用方相同的令牌，但是在访问远程资源时将使用begin_user和begin_password。 

一些例子

```yaml
- name: copy a file from a fileshare with custom credentials
  win_copy:
    src: \\server\share\data\file.txt
    dest: C:\temp\file.txt
    remote_src: yes
  vars:
    ansible_become: yes
    ansible_become_method: runas
    ansible_become_user: DOMAIN\user
    ansible_become_password: Password01
    ansible_become_flags: logon_type=new_credentials logon_flags=netcredentials_only

- name: run a command under a batch logon
  win_whoami:
  become: yes
  become_flags: logon_type=batch

- name: run a command and not load the user profile
  win_whomai:
  become: yes
  become_flags: logon_flags=
```

#### 限制

- 仅当使用Ansible 2.7或更高版本时，`async`和`become`任务才能在Windows Server 2008、2008 R2和Windows 7上运行。

-  默认情况下，` become`用户使用交互式会话登录，因此它必须有权在Windows主机上进行登录。 如果它不继承SeAllowLogOnLocally特权或继承SeDenyLogOnLocally特权，则提权过程将失败。 添加特权或设置logon_type标志以更改使用的登录类型。 

- 在Ansible version 2.3之前，只有当 `ansible_winrm_transport`是basic或credssp时，become才能工作。这个限制已经被解除，自从2.4版的Ansible为所有主机除了Windows Server 2008(非R2版本)。

- 二级登录服务` seclogon `必须运行才能使用` ansible_become_method: runas `

  

## 异步操作和轮询

默认情况下playbook中的任务执行时会一直保持连接,直到该任务在每个节点都执行完毕.有时这是不必要的,比如有些操作运行时间比SSH超时时间还要长.解决该问题最简单的方式是异步执行它们,然后轮询直到任务执行完毕.

你也可以对执行时间非常长（有可能遭遇超时）的操作使用异步模式.

为了异步启动一个任务,可以指定其最大超时时间以及轮询其状态的频率.如果你没有为  poll 指定值,那么默认的轮询频率是15秒钟。

例如下面的palybook

```yaml
---
- hosts: 192.168.77.131

  tasks:
    - shell: sleep 100 && hostname
      async: 100
      poll: 0
      register: result
      
    - debug: var=result

    - async_status: jid={{  result.ansible_job_id }}
      register: job_result
      until: job_result.finished
      retries: 30
```

> poll指定任务的轮训值，poll=0时，任务执行后，会立即执行下一条任务。poll>0时，会阻塞任务，直到任务执行完毕或超时。没有设置的时候，取默认值`DEFAULT_POLL_INTERVAL`

- 第一个任务，指定shell任务为异步执行，100秒后任务失败。
- 第二个任务，获取异步任务的返回值，其目的是获取jid。
- 第三个任务，检查jid异步任务的状态，当异步任务的finished不为0时，异步任务执行成功。检查次数为30次，间隔5秒。

运行playbook的结果信息
```bash
# ansible-playbook  asynctest.yml -vv
ansible-playbook 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible-playbook
  python version = 2.7.5 (default, Aug  4 2017, 00:39:18) [GCC 4.8.5 20150623 (Red Hat 4.8.5-16)]
Using /etc/ansible/ansible.cfg as config file

PLAYBOOK: asynctest.yaml ******************************************************************************************************************
1 plays in asynctest.yaml

PLAY [192.168.77.131] *********************************************************************************************************************

TASK [Gathering Facts] ********************************************************************************************************************
task path: /etc/ansible/asynctest.yaml:2
ok: [192.168.77.131]
META: ran handlers

TASK [shell] ******************************************************************************************************************************
task path: /etc/ansible/asynctest.yaml:5
changed: [192.168.77.131] => {"ansible_job_id": "965275577324.14846", "changed": true, "finished": 0, "results_file": "/root/.ansible_async/965275577324.14846", "started": 1}

TASK [debug] ******************************************************************************************************************************
task path: /etc/ansible/asynctest.yaml:9
ok: [192.168.77.131] => {
    "result": {
        "ansible_job_id": "965275577324.14846", 
        "changed": true, 
        "failed": false, 
        "finished": 0, 
        "results_file": "/root/.ansible_async/965275577324.14846", 
        "started": 1
    }
}

TASK [async_status] ***********************************************************************************************************************
task path: /etc/ansible/asynctest.yaml:11
FAILED - RETRYING: async_status (30 retries left).
FAILED - RETRYING: async_status (29 retries left).
FAILED - RETRYING: async_status (28 retries left).
FAILED - RETRYING: async_status (27 retries left).
FAILED - RETRYING: async_status (26 retries left).
FAILED - RETRYING: async_status (25 retries left).
FAILED - RETRYING: async_status (24 retries left).
FAILED - RETRYING: async_status (23 retries left).
FAILED - RETRYING: async_status (22 retries left).
FAILED - RETRYING: async_status (21 retries left).
FAILED - RETRYING: async_status (20 retries left).
FAILED - RETRYING: async_status (19 retries left).
FAILED - RETRYING: async_status (18 retries left).
FAILED - RETRYING: async_status (17 retries left).
FAILED - RETRYING: async_status (16 retries left).
FAILED - RETRYING: async_status (15 retries left).
FAILED - RETRYING: async_status (14 retries left).
FAILED - RETRYING: async_status (13 retries left).
FAILED - RETRYING: async_status (12 retries left).
FAILED - RETRYING: async_status (11 retries left).
changed: [192.168.77.131] => {"ansible_job_id": "965275577324.14846", "attempts": 21, "changed": true, "cmd": "sleep 100 && hostname", "delta": "0:01:40.069235", "end": "2020-04-03 21:59:52.442879", "finished": 1, "rc": 0, "start": "2020-04-03 21:58:12.373644", "stderr": "", "stderr_lines": [], "stdout": "node131", "stdout_lines": ["node131"]}
META: ran handlers
META: ran handlers

PLAY RECAP ********************************************************************************************************************************
192.168.77.131             : ok=4    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```

使用ansible来执行异步

```bash
# ansible 192.168.77.131 -B 3600 -P 0 -o -m shell -a "sleep 30" -vv
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Aug  4 2017, 00:39:18) [GCC 4.8.5 20150623 (Red Hat 4.8.5-16)]
Using /etc/ansible/ansible.cfg as config file
META: ran handlers
192.168.77.131 | CHANGED => {"ansible_facts": {"discovered_interpreter_python": "/usr/bin/python"}, "ansible_job_id": "71761724165.16525", "changed": true, "finished": 0, "results_file": "/root/.ansible_async/71761724165.16525", "started": 1}
META: ran handlers
META: ran handlers

```
 使用`async_status`来获取异步状态信息
```bash
# ansible 192.168.77.131 -m  async_status -a "jid=71761724165.16525"
192.168.77.131 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "ansible_job_id": "71761724165.16525", 
    "changed": false, 
    "finished": 0, 
    "started": 1
}

# .... 等待任务执行完成

# ansible 192.168.77.131 -m  async_status -a "jid=71761724165.16525"
192.168.77.131 | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "ansible_job_id": "71761724165.16525", 
    "changed": true, 
    "cmd": "sleep 30", 
    "delta": "0:00:30.059717", 
    "end": "2020-04-03 22:09:37.777453", 
    "finished": 1, 
    "rc": 0, 
    "start": "2020-04-03 22:09:07.717736", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "", 
    "stdout_lines": []
}
```

- 注意：在使用'command',  'win_command', 'shell', 'win_shell', 'raw'模块时，是不会返回信息的。



限制并发运行的任务数量的同时运行多个异步任务

```yaml
#####################
# main.yml
#####################
- name: Run items asynchronously in batch of two items
  vars:
    sleep_durations:
      - 1
      - 2
      - 3
      - 4
      - 5
    durations: "{{ item }}"
  include_tasks: execute_batch.yml
  loop: "{{ sleep_durations | batch(2) | list }}"

#####################
# execute_batch.yml
#####################
- name: Async sleeping for batched_items
  command: sleep {{ async_item }}
  async: 45
  poll: 0
  loop: "{{ durations }}"
  loop_control:
    loop_var: "async_item"
  register: async_results

- name: Check sync status
  async_status:
    jid: "{{ async_result_item.ansible_job_id }}"
  loop: "{{ async_results.results }}"
  loop_control:
    loop_var: "async_result_item"
  register: async_poll_results
  until: async_poll_results.finished
  retries: 30
```





### 异步任务的状态文件

异步任务的状态文件以jid命名的方式存放在远端主机的用户目录下的.ansible_async目录，本次使用的是root连接远端，所以目录是/root/.ansible_async。

查看状态文件

```bash
# cat /root/.ansible_async/71761724165.16525
{"started": 1, "finished": 0, "ansible_job_id": "71761724165.16525"}

# 任务结束后

# cat /root/.ansible_async/71761724165.16525
{"changed": true, "end": "2020-04-03 22:09:37.777453", "stdout": "", "cmd": "sleep 30", "start": "2020-04-03 22:09:07.717736", "delta": "0:00:30.059717", "stderr": "", "rc": 0, "invocation": {"module_args": {"warn": true, "executable": null, "_uses_shell": true, "strip_empty_ends": true, "_raw_params": "sleep 30", "removes": null, "argv": null, "creates": null, "chdir": null, "stdin_add_newline": true, "stdin": null}}}
```



### 异步任务的返回值

```json
{
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "ansible_job_id": "662217446295.16055",
    "changed": true,
    "finished": 0,
    "results_file": "/root/.ansible_async/662217446295.16055",
    "started": 1
}
```

> ansible_job_id 异步任务id， results_file异步任务的状态文件



### 异步任务状态的返回值

可通过 async_status 获取，async_status 是读取远端的异步任务状态文件来获得任务状态，如果async设置的时间太短，可能会导致获取不到状态文件，因为还没生成这个文件。



执行中的返回值

```bash
{
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "ansible_job_id": "71761724165.16525", 
    "changed": false, 
    "finished": 0, 
    "started": 1
}
```

执行完成后的返回值

```bash
{
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "ansible_job_id": "71761724165.16525", 
    "changed": true, 
    "cmd": "sleep 30", 
    "delta": "0:00:30.059717", 
    "end": "2020-04-03 22:09:37.777453", 
    "finished": 1, 
    "rc": 0, 
    "start": "2020-04-03 22:09:07.717736", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "", 
    "stdout_lines": []
}
```



## 检查模式

当ansible-playbook执行时加上`--check`选项时，它不会对远程系统做任何更改。支持检查模式的模块将报告它们将进行的更改，而不是进行更改。不支持检查模式的其他模块也将不采取任何操作，只是不报告它们可能做了哪些更改。

执行例子

```bash
ansible-playbook foo.yml --check 
```

也可以在任务中使用检查模式

```yaml
tasks:
  - name: this task will make changes to the system even in check mode
    command: /something/to/run --even-in-check-mode
    check_mode: no

  - name: this task will always run under checkmode and not change the system
    lineinfile:
        line: "important config"
        dest: /path/to/myconfig.conf
        state: present
    check_mode: yes
```

`ansible_check_mode`变量是用来存储当前是否是检查模式的布尔类型

```yaml
tasks:

  - name: this task will be skipped in check mode
    git:
      repo: ssh://git@github.com/mylogin/hello.git
      dest: /home/mylogin/hello
    when: not ansible_check_mode

  - name: this task will ignore errors in check mode
    git:
      repo: ssh://git@github.com/mylogin/hello.git
      dest: /home/mylogin/hello
    ignore_errors: "{{ ansible_check_mode }}"
```

diff模块

ansible-playbook的`--diff`选项可与`--check`配合使用（如上详述），但也可以单独使用。 提供此标志且模块支持此标志时，Ansible将报告所做的更改，或者如果与`--check`一起使用，则将报告所做的更改。

```yaml
- hosts: localhost
  tasks:
  - name: debug.
    debug: msg=123
    check_mode: no
  - name: add hosts.
    lineinfile:
      line: "127.0.0.2 localhost"
      dest: /etc/hosts
      state: present
      check_mode: yes
  - name: add hosts.
    lineinfile:
      line: "127.0.0.2 localhost"
      dest: /etc/hosts
      state: present
      diff: no
```

> diff:  no 禁止对比

检查并对比更改

```bash
ansible-playbook  foo.yml --check --diff
```



## debug 功能

Ansible把一个`debugger `作为`strategy `插件的一部分。此调试器使您能够作为任务进行调试，这个过程是阻塞运行的。但使用`debug`模块也可以调试变量或表达式，而不必阻塞playbook。

有多种使用调试器的方法。

### 使用 debugger 关键字

debugger提供几个值

| 可选值       | 说明  |
| -------------- | -------------------------------- |
| always         | 总是调用调试器，而不管结果如何   |
| never          | 不管结果如何，都不要调用调试器   |
| on_failed      | 只有在任务失败时才调用调试器     |
| on_unreachable | 只有在主机无法访问时才调用调试器 |
| on_skipped     | 只有在任务被跳过时才调用调试器   |

在play中使用

```yaml
- name: Play
  hosts: all
  debugger: on_skipped
  tasks:
    - name: Execute a command
      command: true
      when: False
```

在task中使用

```yaml
- name: Execute a command
  command: false
  debugger: on_failed
```

当play和task同时使用`debugger`时，task的生效

```yaml
- name: Play
  hosts: all
  debugger: never
  tasks:
    - name: Execute a command
      command: false
      debugger: on_failed
```

### 配置或环境变量

在`ansible.cfg`上配置

```ini
[defaults]
enable_task_debugger = True
```

或者设置环境变量

```bash
ANSIBLE_ENABLE_TASK_DEBUGGER=True ansible-playbook -i hosts site.yml
```

### 使用 strategy 插件

使用 `strategy` 插件`debug`

```yaml
- hosts: test
  strategy: debug
  tasks:
  ...
```

或者修改配置和环境变量

```ini
[defaults]
strategy = debug
```

环境变量

```bash
ANSIBLE_STRATEGY=debug
```



### 调试 debugger

使用以下例子

```yaml
- hosts: 192.168.77.131
  debugger: on_failed
  gather_facts: no
  vars:
    var1: value1
  tasks:
    - name: wrong variable
      ping: data={{ wrong_var }}
```

以上playbook，在执行到错误的任务时，会进入debug模式下

```bash
# ansible-playbook debuger.yaml

PLAY [192.168.77.131] *****************************************************************************************

TASK [wrong variable] *****************************************************************************************
fatal: [192.168.77.131]: FAILED! => {"msg": "The task includes an option with an undefined variable. The error was: 'wrong_var' is undefined\n\nThe error appears to be in '/etc/ansible/debuger.yaml': line 7, column 7, but may\nbe elsewhere in the file depending on the exact syntax problem.\n\nThe offending line appears to be:\n\n  tasks:\n    - name: wrong variable\n      ^ here\n"}
[192.168.77.131] TASK: wrong variable (debug)> p result._result
{'_ansible_no_log': False,
 'failed': True,
 'msg': u"The task includes an option with an undefined variable. The error was: 'wrong_var' is undefined\n\nThe error appears to be in '/etc/ansible/debuger.yaml': line 7, column 7, but may\nbe elsewhere in the file depending on the exact syntax problem.\n\nThe offending line appears to be:\n\n  tasks:\n    - name: wrong variable\n      ^ here\n"}
[192.168.77.131] TASK: wrong variable (debug)> p task.args
{u'data': u'{{ wrong_var }}'}
[192.168.77.131] TASK: wrong variable (debug)> task.args['data'] = '{{ var1 }}'
[192.168.77.131] TASK: wrong variable (debug)> p task.args
{u'data': '{{ var1 }}'}
[192.168.77.131] TASK: wrong variable (debug)> redo
ok: [192.168.77.131]

PLAY RECAP *****************************************************************************************
192.168.77.131             : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

通过调试，我们使playbook以成功运行完毕。

`debugger`模式下的可用指令


| 指令                         | 说明     |
| ------------------------- | ---------------------- |
| p                         | 显示此次失败的原因     |
| p task                    | 显示此次任务的名称     |
| p task.args            | 显示模块的参数         |
| p task_vars            | 显示任务的可用变量     |
| p host                    | 显示执行此次任务的主机 |
| p result                  | 显示此次任务的结果     |
| p vars                    | 显示当前的变量         |
| vars[key] = value         | 更新vars中的值         |
| task.args[key] =    value | 更新模块的参数。       |
| u(pdate_task) | 从原始任务数据结构和带有更新的task_vars的模板中重新创建任务 |
| r(edo)                    | 再次执行此任务         |
| c(ontinue)           | 继续执行               |
| q(uit)                  | 退出debug模式          |

### 与`free`策略一起使用

当`debugger`与`free`策略一起使用时，在调试器处于活动状态时，不会导致其他任务排队或执行。但使用`redo`时，可能回导致当前任务在其他任务之后执行

### 使用 debug 模块

在执行期间打印语句，使用`debug`模块可以调试变量或表达式，而不必阻塞playbook。

打印自定义的信息

```yaml
tasks:
  - debug: msg="System {{ inventory_hostname }} has uuid {{ ansible_product_uuid  }}"
```

调试变量

```yaml
tasks:
  - debug: var=result  verbosity=2
```



## 滚动执行

默认情况下，Ansible会并行地管理一个剧本中引用的所有机器。对于滚动更新用例，可以使用`serial`关键字定义Ansible并行执行多少台主机

```yaml
---
- name: test play
  hosts: webservers
  serial: 3
  gather_facts: False

  tasks:
    - name: task one
      command: hostname
    - name: task two
      command: hostname
```

在上面的例子中，如果我们有100个主机，组“webservers”中的3个主机将完成playbook，然后再移动到接下来的3个主机。

还可以使用百分比

```yaml
serial: "30%"
```

从Ansible 2.2开始，可以指定一个列表作为批量执行的依据

```yaml
---
- name: test play
  hosts: webservers
  serial:
    - 1
    - 5
    - 10
```

在上面的例子中，第一批执行将包含一个主机，下一批将包含5个主机，并且(如果还剩下任何主机)，接下来的每一批将包含10个主机，直到所有可用的主机都被使用。

可以在列表中使用百分比

```yaml
---
- name: test play
  hosts: webservers
  serial:
    - "10%"
    - "20%"
    - "100%"
```

也可以混合使用

```yaml
---
- name: test play
  hosts: webservers
  serial:
    - 1
    - 5
    - "20%"
```



## 指定最大失败数目

默认情况下，只要组中有尚未失败的主机，Ansible将继续执行操作。  在一些情况下，例如利用上述滚动更新，可能希望在达到失败的特定阈值时中止任务。

```yaml
---
- hosts: webservers
  max_fail_percentage: 30
  serial: 10
```

在上面的示例中，如果组中的10台服务器中有3台以上发生故障，则将终止其余的操作。



## 委托

在任务上使用`delegate_to`关键字,可以将任务委托给指定主机去执行。

```yaml
---
- hosts: webservers
  serial: 5

  tasks:
    - name: take out of load balancer pool
      command: /usr/bin/take_out_of_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1

    - name: actual steps would go here
      yum:
        name: acme-web-stack
        state: latest

    - name: add back to load balancer pool
      command: /usr/bin/add_back_to_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1
```

` delegate_to: 127.0.0.1` 是将任务委派到ansible本地去执行，你可以使用简写的`local_action` 去执行

```yaml
---
# ...

  tasks:
    - name: take out of load balancer pool
      local_action: command /usr/bin/take_out_of_pool {{ inventory_hostname }}

# ...

    - name: add back to load balancer pool
      local_action: command /usr/bin/add_back_to_pool {{ inventory_hostname }}
```

一个例子

```yaml
- hosts: db_servers
  tasks:
  -  name: ifconfig
     command: fconfig
     delegate_to: 127.0.0.1
     
  -  name: ifconfig
     local_action: command ifconfig

- hosts: app_servers
  tasks:
  - name: gather facts from db servers
    setup:
    delegate_to: "{{item}}"
    delegate_facts: True
    with_items:  "{{groups['dbservers']}}"
```

> delegate_facts 指定收集委托主机的facts数据

以上将为`dbservers`组中的机器收集`facts`，并将`facts`分配给这些机器，而不是`app_servers`。



## 任务只运行一次

通过在任务上配置`run_once`来实现当前任务在`play`中只执行一次

```yaml
- tasks:
  - command: ifconfig
    run_once: true
```

上面的例子，将只会在第一个执行主机上执行，其余的主机则不执行。

有点类似于使用when条件判断

```yaml
- command: /opt/application/upgrade_db.py
  when: inventory_hostname == webservers[0]
```



## 本地执行

为playbook指定`connection=local`将会使任务在本地执行，而不是使用ssh连接远端。

执行playbook

```bash
ansible-playbook  playbook.yml --connection=local
```

在play中指定

```yaml
---
- hosts: 127.0.0.1
  connection: local
```


## 设置环境变量

为运行程序指定环境变量，需指定`environment`关键字

```yaml
- tasks:
  - apt:  name=cobbler state=installed
    environment:
      http_proxy: http://proxy.example.com:8080
      PATH: /var/local/nvm/versions/node/v4.2.1/bin:{{  ansible_env.PATH }}
```

也可以在play级别使用

```yaml
- hosts: testhost
  roles:
    - php
    - nginx
  environment:
    http_proxy: http://proxy.example.com:8080
```

## 错误处理

### 忽略错误

`ignore_errors` 模块可以在任务执行错误时，忽略错误并继续执行任务。

```yaml
- tasks:
  - command: /bin/false
    ignore_errors: true

  - debug: msg="false"
```

### 重置无法访问的主机

连接远端主机失败时，ansible会将主机设置为不可到达，这将从运行的活动主机列表中删除它们。要从这些问题中恢复，需执行下列动作恢复主机。

```yaml
-  meta: clear_host_errors
```



### 即使任务失败，handlers也执行

以下3中方法均可使用


- 命令行加上` --force-handlers` 参数
- 配置文件加上 `force_handlers = True`
- playbook里设置  `force_handlers: True`



### 控制任务失败

使用`failed_when`选项时，当条件为真时，可使当前任务以失败返回

您可以通过在命令的输出中搜索一个单词或短语来检查是否命令执行是否失败

```yaml
- name: Fail task when the command error output prints FAILED
  command: /usr/bin/example-command -x -y -z
  register: command_result
  failed_when: "'FAILED' in command_result.stderr"
```

或者根据返回值

```yaml
- name: Fail task when both files are identical
  raw: diff foo/file1 bar/file2
  register: diff_cmd
  failed_when: diff_cmd.rc == 0 or diff_cmd.rc >= 2
```

在以前的版本中，可以使用以下完成上述操作

```yaml
- name: this command prints FAILED when it fails
  command: /usr/bin/example-command -x -y -z
  register: command_result
  ignore_errors: True

- name: fail the play if the previous command did not succeed
  fail:
    msg: "the command failed"
  when: "'FAILED' in command_result.stderr"
```

可以使用多个并行条件，这些条件之间是`and`关系

```yaml
- name: Check if a file exists in temp and fail task if it does
  command: ls /tmp/this_should_not_be_here
  register: result
  failed_when:
    - result.rc == 0
    - '"No such" not in result.stdout'
```

使用`or`条件

```yaml
failed_when: result.rc == 0 or "No such" not in result.stdout
```

如果一行写不下，可以使用多行表示

```yaml
- name: example of many failed_when conditions with OR
  shell: "./myBinary"
  register: ret
  failed_when: >
    ("No such file or directory" in ret.stdout) or
    (ret.stderr != '') or
    (ret.rc == 10)
```

### 更改任务changed状态

指定`changed_when` 条件时，当条件为真，任务的`changed`为真，即表示当前任务做了更改。

```yaml
tasks:

  - shell: /usr/bin/billybass --mode="take me to the river"
    register: bass_result
    changed_when: "bass_result.rc != 2"

  # this will never report 'changed' status
  - shell: wall 'beep'
    changed_when: False
```

使用多个条件

```yaml
- command: /bin/fake_command
  register: result
  ignore_errors: True
  changed_when:
    - '"ERROR" in result.stderr'
    - result.rc == 2
```

### 出现错误时立即中断执行

使用`any_errors_fatal`选项时，只要playbook中出现一个错误任务,ansible立即停止运行。已保证所有任务的正确运行。

```yaml
---
- hosts: load_balancers_dc_a
  any_errors_fatal: True

  tasks:
    - name: 'shutting down datacenter [ A ]'
      command: /usr/bin/disable-dc

- hosts: frontends_dc_a

  tasks:
    - name: 'stopping service'
      command: /usr/bin/stop-software
    - name: 'updating software'
      command: /usr/bin/upgrade-software

- hosts: load_balancers_dc_a

  tasks:
    - name: 'Starting datacenter [ A ]'
      command: /usr/bin/enable-dc
```

### 使用blocks

使用`blocks`的`rescue`来实现对错误任务的处理

```yaml
tasks:
- name: Handle the error
  block:
    - debug:
        msg: 'I execute normally'
    - name: i force a failure
      command: /bin/false
    - debug:
        msg: 'I never execute, due to the above task failing, :-('
  rescue:
    - debug:
        msg: 'I caught an error, can do stuff here to fix it, :-)'
```

## YAML 语法

YAML 语法见[详细介绍](/basic/Reference/Yaml/)


## Prompts： **运行时，提示输入内容**

在运行playbook时，您可能希望提示用户输入某些内容，可以通过`vars_prompt`实现这一点。

```yaml
- hosts: test
  gather_facts: no
  vars_prompt:
    - name: "name"
      prompt: "what is your name?"
      default: "user"
      private: yes
      confirm: yes

  tasks:
    - debug: msg={{ name }}
```

`vars_prompt`的参数


- name: 定义变量名称，即输入的内容赋值给此变量
- prompt：输入得提示信息
- default： 输入的默认值，没有输入任何内容的时候，把此值赋值给变量
- private：是否隐藏输入得内容
- confirm：是否要再次确认输入
- unsafe:  不校验输入的字符串，如果输入特殊字符，可开启此选项

如果安装了`Passlib`, `vars_prompt`还可以对输入的值进行加密

```yaml
- hosts: test
  gather_facts: no
  vars_prompt:
    - name: "pass"
      prompt: "Enter password2"
      private: yes
      encrypt: "sha512_crypt"
      confirm: yes
      salt_size: 7
      
  tasks:
    - debug: msg={{ pass }}
```

可以使用的加密方案

- *des_crypt* - DES Crypt
- *bsdi_crypt* - BSDi Crypt
- *bigcrypt* - BigCrypt
- *crypt16* - Crypt16
- *md5_crypt* - MD5 Crypt
- *bcrypt* - BCrypt
- *sha1_crypt* - SHA-1 Crypt
- *sun_md5_crypt* - Sun MD5 Crypt
- *sha256_crypt* - SHA-256 Crypt
- *sha512_crypt* - SHA-512 Crypt
- *apr_md5_crypt* - Apache’s MD5-Crypt variant
- *phpass* - PHPass’ Portable Hash
- *pbkdf2_digest* - Generic PBKDF2 Hashes
- *cta_pbkdf2_sha1* - Cryptacular’s PBKDF2 hash
- *dlitz_pbkdf2_sha1* - Dwayne Litzenberger’s PBKDF2 hash
- *scram* - SCRAM Hash
- *bsd_nthash* - FreeBSD’s MCF-compatible nthash encoding

## 标记

如果你有一个大型剧本，但你只希望运行它的一个特定的部分，而不是运行剧本中的所有任务。这时候，你可以为运行的任务指定一个共同的`tags`

### 标记任务

```yaml
tasks:
- yum:
    name:
    - httpd
    - memcached
    state: present
  tags:
  - packages

- template:
    src: templates/src.j2
    dest: /etc/foo.conf
  tags:
  - configuration
```

> 标签名称可以重名

显示playbook中的所有标记任务

```bash
ansible-playbook  example.yml --list-tags
```

执行所有标记名称为packages和configuration的任务

```bash
ansible-playbook  example.yml --tags "configuration,packages"
```

跳过所有标记名称为configuration的任务

```bash
ansible-playbook  example.yml --skip-tags "configuration"
```

### 标记playbook

```yaml
- hosts: all
  tags:
    - bar
  tasks:
   ...

- hosts: all
  tags: ['foo']
  tasks:
  ...
```

> play里的所有tasks将会继承play的tags

### 标记role

```yaml
- roles:
  - { role: webserver, port: 5000, tags: [  'web', 'foo' ] }
```

> role里的tasks将会继承role的tags

### 标记包含

```yaml
- import_role:
    name: myrole
  tags: [ web, foo ]

- import_tasks: foo.yml
  tags: [ web, foo ]
```

> 包含的role和tasks中的任务将会继承tags，动态包含则不继承tag

### 特殊标记

使用`always`标签可以始终运行标记的任务

```yaml
tasks:
- debug:
    msg: "Always runs"
  tags:
  - always

- debug:
    msg: "runs when you use tag1"
  tags:
  - tag1
```

还有另外4个特殊关键字用于标签，

- `never` 阻止任务运行
- `tagged` 仅运行已标记
- `untagged` 运行只有未标记
- `all`运行所有任务

默认情况下ansible运行就像指定了`-tags all`

## Vault 加密

Vault 加密使用方法见[详细介绍](/basic/Reference/Vaults/)



## 从某个任务开始执行

为ansible-playbook指定`--start-at-task`，就可以从这个任务开始执行

```bash
ansible-playbook  playbook.yml --start-at-task="install packages"
```

## 一步一步的执行

ansible也可以一步一步交互的执行，执行每一步都需要确认是否继续

```bash
ansible-playbook  playbook.yml --step
```

## 模块默认值

你可以为多个相同的模块指定默认值,而不必重复填写。

```yaml
- hosts: localhost
  module_defaults:
    file:
      owner: root
      group: root
      mode: 0755
  tasks:
    - file:
        state: touch
        path: /tmp/file1
    - file:
        state: touch
        path: /tmp/file2
    - file:
        state: touch
        path: /tmp/file3
```

可以在play、block和task级别使用module_defaults属性。

```yaml
- block:
    - debug:
        msg: "a different message"
  module_defaults:
    debug:
      msg: "a default message"
      
- file:
    state: touch
    path: /tmp/file1
  module_defaults:
    file: {}
```

在playbook中，您可以为整个模块组设置模块默认值，例如设置一个公共AWS区域。

```yaml
# example_play.yml
- hosts: localhost
  module_defaults:
    group/aws:
      region: us-west-2
  tasks:
  - aws_s3_bucket_info:
  # now the region is shared between both info modules
  - ec2_ami_info:
      filters:
        name: 'RHEL*7.5*'
```

可用于group的模块

| Group | Purpose               | Ansible Version |
| ----- | --------------------- | --------------- |
| aws   | Amazon Web Services   | 2.7             |
| azure | Azure                 | 2.7             |
| gcp   | Google Cloud Platform | 2.7             |
| k8s   | Kubernetes            | 2.8             |
| os    | OpenStack             | 2.8             |



## 等待

使用`wait_for`模块，可以等待任务执行完毕后，才可继续执行后续的任务。

等待端口可用,才能继续执行任务

```yaml
- wait_for: port=8000 delay=10
```

等待直到锁定文件被删除

```yaml
wait_for: path=/var/lock/file.lock state=absent
```

## Playbook 关键字

Playbook 可用的关键字见[详细列表](basic/Reference/Keywords/)

## lookup 插件

`lookup`插件允许访问外部数据源。与所有模板一样，这些插件是在Ansible control节点上执行的。

### 使用 `file` 获取文件内容

```yaml
---

- hosts: all
  vars:
     contents: "{{ lookup('file',  '/etc/foo.txt') }}"

  tasks:
    - debug: msg="the value of foo.txt is {{  contents }}"
```

### 使用 `env` 获取变量

```yaml
---

- hosts: all
  vars:
    local_home: "{{ lookup('env','HOME')  }}"
  tasks:
    - debug: var=local_home
```

### 使用 `password` 生成密码字符串


```yaml
---
- hosts: all

  tasks:
    #  使用只有ascii字母且长度为8的随机密码创建一个mysql用户:
    - mysql_user: name={{ client  }}
                  password="{{  lookup('password', '/tmp/passwordfile chars=ascii_letters length=8') }}"
                  priv={{ client }}_{{  tier }}_{{ role }}.*:ALL

    # 使用只有数字的随机密码创建一个mysql用户:
    - mysql_user: name={{ client  }}
                  password="{{  lookup('password', '/tmp/passwordfile chars=digits') }}"
                  priv={{ client }}_{{  tier }}_{{ role }}.*:ALL

    # 使用许多不同的字符集使用随机密码创建一个mysql用户：
    - mysql_user: name={{ client  }}
                  password="{{  lookup('password', '/tmp/passwordfile  chars=ascii_letters,digits,hexdigits,punctuation') }}"
                  priv={{ client }}_{{  tier }}_{{ role }}.*:ALL
```


如果文件已存在，则不会向其写入任何数据。  如果文件有内容，那些内容将作为密码读入。 空文件导致密码以空字符串返回。

 

### 使用 `csvfile` 读取csv文件


```
# f.csv 

Symbol,Atomic  Number,Atomic Mass
H,1,1.008
He,2,4.0026
Li,3,6.94
Be,4,9.012
B,5,10.81
```

```yaml
- debug:  msg="The atomic number of Lithium is {{ lookup('csvfile', 'Li  file=elements.csv delimiter=,') }}"
- debug:  msg="The atomic mass of Lithium is {{ lookup('csvfile', 'Li  file=elements.csv delimiter=, col=2') }}"
```

参数描述


| 参数      | 默认值          | 描述                                                   |
| --------- | --------------- | ------------------------------------------------------ |
| file      | ansible.csv     | 要加载的文件名称                                       |
| col       | 1               | 要输出的列，索引从0开始                                |
| delimiter | TAB             | 文件的分隔符                                           |
| default   | empty    string | 如果key不在csv文件中，则为默认返回值                   |
| encoding  | utf-8           | 使用的CSV文件的编码（字符集）(added    in version 2.1) |

 

### 使用 `ini`  读取ini文件

在section下查找以key1  = value1的格式来读取文件的内容。


```ini
# users.ini

[production]
# My production information
user=robert
pass=somerandompassword

[integration]
# My  integration information
user=gertrude
pass=anotherpassword
```



```yaml
tasks:
  - debug: msg="User in integration is {{  lookup('ini', 'user section=integration file=users.ini') }}"

  - debug: msg="User in production  is {{ lookup('ini', 'pass section=production  file=users.ini')  }}"
```


ini 参数格式
```yaml
lookup('ini',  'key [type=<properties|ini>] [section=section] [file=file.ini] [re=true]  [default=<defaultvalue>]')
```


第一个值必须是ini文件里的key

参数描述

| 字段    | 默认值          | 描述                                                         |
| ------- | --------------- | ------------------------------------------------------------ |
| type    | ini             | 文件类型。    可以是ini或properties （对于javaproperties ）。 |
| file    | ansible.ini     | 要加载的文件名称                                             |
| section | global          | 在哪里查找key                                                |
| re      | False           | 开启正则匹配                                                 |
| default | empty    string | 如果key不在文件中，则为默认返回值                            |

### 使用 `dig` dns查询

此模块依赖 `dnspython`  库


```yaml
tasks:
  - debug:  msg="The IPv4 address for example.com. is {{ lookup('dig',  'example.com.')}}"

  - debug:  msg="The TXT record for example.org. is {{ lookup('dig', 'example.org.',  'qtype=TXT') }}"

  - debug:  msg="The TXT record for example.org. is {{ lookup('dig',  'example.org./TXT') }}"
```


其他插件
```yaml
tasks:

- debug: msg="{{ lookup('env','HOME') }} is an  environment variable"

- debug: msg="{{ lookup('pipe','date') }} is the  raw result of running this command"

# redis_kv lookup requires the  Python redis package
- debug: msg="{{  lookup('redis_kv', 'redis://localhost:6379,somekey') }} is value in Redis for  somekey"

# dnstxt lookup requires the Python  dnspython package
- debug: msg="{{  lookup('dnstxt', 'example.com') }} is a DNS TXT record for example.com"

- debug: msg="{{ lookup('template',  './some_template.j2') }} is a value from evaluation of this template"

# loading a json file from a  template as a string
- debug: msg="{{  lookup('template', './some_json.json.j2', convert_data=False) }} is a value  from evaluation of this template"

- debug: msg="{{ lookup('etcd', 'foo') }} is a  value from a locally running etcd"

# shelvefile lookup retrieves a  string value corresponding to a key inside a Python shelve file
- debug: msg="{{  lookup('shelvefile', 'file=path_to_some_shelve_file.db key=key_to_retrieve')  }}
```

