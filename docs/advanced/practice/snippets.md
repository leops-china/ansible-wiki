# Ansible Task 片段

## 怎么为任务设置环境变量

```yaml
- name: set environment
  shell: echo $PATH $SOME >> /tmp/a.txt
  environment:
    PATH: '{{ ansible_env.PATH }}:/thingy/bin'
    SOME: value
```

## 不同的用户登录不同的主机

```
在主机清单里设置
[webservers]
asdf.example.com  ansible_port=5000   ansible_user=alice  ansible_pass=123456
jkl.example.com   ansible_port=5001   ansible_user=bob   ansible_pass=654321

也可以指定连接类型
[testcluster]
localhost           ansible_connection=local
/path/to/chroot1    ansible_connection=chroot
foo.example.com
bar.example.com
```

## 通过跳转主机访问无法访问的主机

```
# ansible 免密登录跳板机
ansible_ssh_common_args: '-o ProxyCommand="ssh -W %h:%p -q user@gateway.example.com"'
ansible_ssh_common_args: '-o ProxyCommand="sshpass -f /etc/tpasswd ssh xx@10.10.10.1 -p 66677 nc %h %p"'

ansible_ssh_common_args="-o ProxyCommand='ssh -W %h:%p -q -p 20343 root@11.11.11.11'"
ansible_ssh_common_args="-o ProxyCommand=\"ssh -qay -p 20343 root@11.11.11.11 'nc %h %p'\""
ansible_ssh_common_args="-o ProxyCommand=\"sshpass -p '123456' ssh -qay -p 20343 root@11.11.11.11 'nc %h %p'\""


# 跳板机sshd配置
MaxStartups 1000
LoginGraceTime 0

# ansible.cfg
timeout = 60
ssh_args=-C -o ControlMaster=auto -o ControlPersist=5m -F /etc/ansible/prod/ssh_config
retries = 1

#　ssh_config
Host 47.111.162.118
    User root
    Hostname 47.111.162.118
    ProxyCommand none
    BatchMode yes
Host 172.16.99.*
    User root
    ServerAliveInterval 60
    TCPKeepAlive        yes
    ProxyCommand        ssh -qaY -p 20343 root@47.111.162.118 nc %h %p
    ForwardAgent        yes
```

## 关闭 cowsay 功能

```
export ANSIBLE_NOCOWS=1
```

## 关闭 ssh 在首次连接时出现检查 keys 的提示

```
export ANSIBLE_HOST_KEY_CHECKING=False
```

## 查看主机名的所有清单变量

```
ansible -m debug -a "var=hostvars['hostname']" localhost
```

## 通过拼接字符串，来获取接口 ip 地址

```
{{ hostvars[inventory_hostname]['ansible_' + which_interface]['ipv4']['address'] }}
```

## 获取组中第一个主机的 ip 地址

```
{{ hostvars[groups['webservers'][0]]['ansible_eth0']['ipv4']['address'] }}
```

## 在任务中设置变量

```
- set_fact: headnode={{ groups[['webservers'][0]] }}
- debug: msg={{ headnode}}
```

## 如何获取 shell 变量

```
vars:
    local_home: "{{ lookup('env','HOME') }}"
tasks:
  - debug: var=local_home

在ansible1.4版本以上，可以使用以下方式获取
- debug: var=ansible_env.HOME
```

## 在模板中如何遍历某一组内的所有主机？

```
	{% for host in groups['db_servers'] %}
	    {{ host }}
	{% endfor %}
```

## 获取 ip 地址

```
	{% for host in groups['db_servers'] %}
	   {{ hostvars[host]['ansible_eth0']['ipv4']['address'] }}
	{% endfor %}

	{{ ansible_default_ipv4 }}
```

## service 模块启动服务没效果？

```
首先检查下service httpd status的信息，是不是有 httpd is stopped
这种字符，没有的话，在服务启动脚本里，在case语句里添加以下方法

  status)
        status -p ${pidfile} $httpd
  RETVAL=$?
  ;;

# bash变量
httpd=${HTTPD-/usr/sbin/httpd}
pidfile=${PIDFILE-/var/run/httpd/httpd.pid}

从而达到service http status有stopped的字样。
```

## 递归目录中的模版文件

```
- name: Copying the templated jinja2 files
  template: src={{item}} dest={{RUN_TIME}}/{{ item | regex_replace(role_path+'/templates','') | regex_replace('\.j2', '') }}
  with_items: "{{ lookup('pipe','find {{role_path}}/templates -type f').split('\n') }}"
```

## 指定 python 版本

```
- hosts: servers
  vars:
    - ansible_python_interpreter: /usr/bin/python2.6.6
```

## 远程遍历拷贝文件。

```
- name    : get files in /path/
  shell   : ls /path/*
  register: path_files

- name: fetch these back to the local Ansible host for backup purposes
  fetch:
    src : /path/"{{item}}"
    dest: /path/to/backups/
  with_items: "{{ path_files.stdout_lines }}"
```

## 使用系统其他用户执行命令

```
ansible node1 -m shell -a "touch /tmp/12345" --become-user=hadoop --become

- command: touch /tmp/1234567
  become: true
  become_user: hadoop
```

## 获取主机清单中组的 ip 地址

```
- shell: "ping -c 1 {{item}} | grep icmp_seq | gawk -F'[()]'  '{print $2}'"
  with_inventory_hostnames: test2
  register: testip

- debug: "msg={{ item.stdout }}"
  with_items: "{{ testip.results }}"
```

## 保留 ansbile 远程执行的模块文件，并调试模块

```
  添加ANSIBLE_KEEP_REMOTE_FILES=环境变量
$ ANSIBLE_KEEP_REMOTE_FILES=1 ansible localhost -m ping -a 'data=debugging_session' -vvv
  sing module file /usr/lib/python2.6/site-packages/ansible/modules/core/system/ping.py
  <localhost> ESTABLISH LOCAL CONNECTION FOR USER: root
  <localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo ~/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932 `" && echo ansible-tmp-1489477306.61-275734926719932="` echo ~/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932 `" ) && sleep 0'
  <localhost> PUT /tmp/tmpv4EenK TO /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py
  <localhost> EXEC /bin/sh -c 'chmod u+x /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py && sleep 0'
  <localhost> EXEC /bin/sh -c '/usr/bin/python /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py && sleep 0'
  localhost | SUCCESS => {
      "changed": false,
      "invocation": {
          "module_args": {
              "data": "debugging_session"
          },
          "module_name": "ping"
      },
      "ping": "debugging_session"
}

模块文件是由base64编码的字符串文件，可使用explode将字符串转换成可执行的python文件
  $ python /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py explode
Module expanded into:
/root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/debug_dir
  $ tree  /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/debug_dir/
/root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/debug_dir/
├── ansible
│   ├── __init__.py
│   └── module_utils
│       ├── basic.py
│       ├── __init__.py
│       ├── pycompat24.py
│       ├── six.py
│       └── _text.py
├── ansible_module_ping.py
└── args

ansible_module_ping.py 是模块本身的代码。
args文件包含一个JSON字符串。 该字符串是一个包含模块参数和其他变量的字典。
ansible目录包含由ansible_module_ping模块使用的ansible.module_utils的代码文件。

如果修改了`debug_dir`文件中的代码之后，需要使用execute执行代码
$ python /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py execute
{"invocation": {"module_args": {"data": "debugging_session"}}, "changed": false, "ping": "debugging_session"}

18. 如果想使所有的notfiy任务在某一位置执行。只需增加一个
- meta: flush_handlers
列如
- hosts: localhost
  gather_facts: no

  tasks:
    - command: echo 123
      notify: test1
    - meta: flush_handlers
    - debug: msg="789"
  handlers:
    - name: test1
      debug: msg="456"

此任务的返回状态必须为changed状态，才会执行handlers里的任务。
```

## 提升权限

```
Ansible ad-hoc命令
ansible -i hosts node1 -m shell -a "whoami" --become  --become-method=su --become-user=root --ask-su-pass
SU password:
192.168.77.130 | SUCCESS | rc=0 >>
root

Ansible-playbook命令
cat test.yml
---
- hosts: node1
  gather_facts: no
  tasks:
  - name: I'm become to root.
    shell: whoami
    register: w
    become: true
    become_user: "root"
    become_method: "su"
  - debug: var=w.stdout

[root@base ~]# ansible-playbook -i hosts test.yml --ask-su-pass
SUDO password:

PLAY [node1] ****************************************************************************************************************************************

TASK [I'm become to root.] **************************************************************************************************************************
changed: [192.168.77.130]

TASK [debug] ****************************************************************************************************************************************
ok: [192.168.77.130] => {
    "w.stdout": "root"
}

PLAY RECAP ******************************************************************************************************************************************
192.168.77.130             : ok=2    changed=1    unreachable=0    failed=0


如果不想在执行过程中输入提升用户的密码，可以在hosts文件中配置ansible_become_pass变量设置密码。
# cat hosts
[node1]
192.168.77.130 ansible_ssh_user=test ansible_ssh_pass=123456 ansible_become_pass=123456

参数解释
become 开启提升权限
become-method  提升权限的方式，有sudo，su，runas等。
become-user  提升权限的用户
ansible_become_pass 提升权限的用户密码
ask-su-pass  告诉程序提升权限的用户密码
```

## 变量嵌套

在动态取变量的时候，我们第一时间就会写出"`{{ t_var[{{n}}]}}`"的引用命令，但这类引用在 jinja2 的语法中是错误的，可以使用下列方式解决此引用问题。

```
	- hosts: localhost
	  gather_facts: no
	  vars:
	   - t_var: ['1','2']
	   - n: "1"

	  tasks:
	   - shell: "echo {% if n %} {% set number = n | int %} {{ t_var[number]}} {% endif %}"
```

另外一个

```
- hosts: dev
  remote_user: root
  gather_facts: false
  tasks:
    - name: get dir path and port info
      shell: cat /data/info.txt
      register: info

    - name: get the last num
      shell: cat /data/num
      register: num

    - name: test
      shell: echo {{ info.stdout.split(',')[num.stdout|int].split(':')[0] }} >/tmp/test.txt
```

## 环境变量找不到的问题

```
我们在ansible直接执行命令，不带有绝对路径，就会报出找不到命令的提示信息：

ansible node2 -m shell -a "openresty -v"
192.168.77.130 | FAILED | rc=127 >>
/bin/sh: openresty: 未找到命令


此时我们应该使用下列命令避免。
ansible node2 -m shell -a "source /etc/profile; openresty -v"
192.168.77.130 | SUCCESS | rc=0 >>
nginx version: openresty/1.11.2.3

ansible 的ssh登陆属于交互式的非登陆shell
```

## 获取 redis 的 info 信息

```
- hosts: localhost
  gather_facts: false
  tasks:
  - name: "query redis info"
    expect:
      command: "telnet 106.14.183.68 6379"
      responses:
        "Escape":
           - "auth test\ninfo\nquit\n"
    ignore_errors: true
    register: result
  - name: "show the variable"
    debug:
      var: result
```

## 判断文件是否存在

```
- name: install | Check if Mysql file is already configured.
  stat: path=/tmp/123
  register: file_result

- name: install | Create software files path.
  file: path=/tmp/123 state=directory
  when: not file_result.stat.exists
```

## 不显示失败内容

在执行 task 时，有些时候不希望模块报出`fatal`的错误信息，这时候我们可以使用`failed_when`关键字使 task 永不失败,在使用`register`关键字记录模块的信息，便于后续任务使用. `changed_when` 是永不改变，`no_log` 是不记录日志。

```yaml
- name: 检查主机连接状态
  wait_for_connection:
    connect_timeout: 1
    timeout: 3
  register: host_status
  failed_when: false
  changed_when: false
  no_log: true

- name: 结束运行连接失败的主机
  meta: end_host
  when: host_status.msg is defined and host_status.msg is search('SSH Error')
```

## 实现 try catch 功能

block 中的任务正常执行，如果有任何错误，则该 rescue 部分将执行。always 无论 block 和 rescue 部分中以前发生过或没有发生过什么错误，该部分都将运行。

```yaml
- name: 捕捉错误
  block:
    - debug:
        msg: '正常执行'
    - name: 强行错误
      command: /bin/false
    - debug:
        msg: '由于上述任务失败，从不执行'
  rescue:
    - debug:
        msg: '发现一个错误'
    - name: 在恢复过程中强行失败
      command: /bin/false
    - debug:
        msg: '恢复过程中发生错误时,也从不执行'
  always:
    - debug:
        msg: "总是执行"

# 使用handlers
 tasks:
   - name: 尝试并优雅地回滚
     block:
       - debug:
           msg: '正常执行'
         changed_when: yes
         notify: 即使发生错误时也执行
       - command: /bin/false
     rescue:
       - name: 确保所有task都运行
         meta: flush_handlers
 handlers:
    - name:  即使发生错误时也执行
      debug:
        msg: '该task在错误时运行'
```

## 循环字典中 key 的 value 值

> 使用 dict2items 将字典变成 list, 然后使用 subelements 获取 vlaue 子元素

```yaml
- hosts: localhost
  gather_facts: no
  vars:
    test:
      host1:
        - cmd1
        - cmd2
      host2:
        - cmd1
        - cmd2
        - cmd3
  tasks:
    - name: test
      debug:
        msg: 'Key={{ item.0.key }} value={{ item.1 }}'
      loop: "{{ test | dict2items | subelements('value') }}"
```

## 将字典中存在的 key 那一项的其他 key 的 value 拼接成字符串

> selectattr()通过对每个对象的指定属性应用测试来过滤对象序列。map()过滤器返回在前一步中记录的所有对象的 name 属性,list 将前一步的结果变成列表,join 将前一步的列表拼接成字符串

```yaml
---
- hosts: test
  gather_facts: false
  vars:
    - test:
        - { 'name': 'test1' }
        - { 'name': 'test2', 'hello': 'world' }
        - { 'name': 'test3' }
        - { 'name': 'test4', 'hello': 'world' }
        - { 'name': 'test5', 'hello': 'world' }
        - { 'name': 'test6' }

  tasks:
    - debug: var=test
    - debug: msg={{ test | selectattr("hello",'defined') | map(attribute='name') | list | join(',') }}
```

比较复杂的,拼接列表中的数据

```yaml
- hosts: 192.168.77.132
  gather_facts: false
  vars:
    - test:
        - { 'name': 'test0', 'facts': { 'vars': {} } }
        - { 'name': 'test1', 'facts': { 'vars': { 'name': ['1', '2'] } } }
        - { 'name': 'test2', 'facts': { 'vars': { 'name': ['3'] } } }
        - { 'name': 'test3' }
        - { 'name': 'test4', 'facts': { 'vars': { 'name': ['4'] } } }
        - { 'name': 'test5', 'facts': { 'vars': { 'name': ['5', '6'] } } }
        - { 'name': 'test6', 'facts': {} }
        - { 'name': 'test7', 'facts': { 'vars': {} } }
        - { 'name': 'test8', 'facts': { 'vars': {} } }
        - { 'name': 'test9' }

  tasks:
    - debug: var=test
    - debug:
        msg: |-
          {%- for t in test | selectattr('facts.vars.name','defined') | map(attribute='facts.vars.name') | reject('equalto', [])-%}
            {%- for i in t -%}
              {{i}}
              {%-if not loop.last-%},{%-endif-%}
            {%-endfor-%}
            {%-if not loop.last-%},{%-endif-%}
          {%-endfor-%}
    # 不使用for循环
    - debug: msg={{ test | selectattr('facts.vars.name','defined') | map(attribute='facts.vars.name') | list | flatten }}
```


## 按顺序执行命令

有时，我们在集群中需要按顺序执行某些命令，不能并行执行，这时可以使用delegate_to和循环控制来配合使用达到目的，下列案例是每次循环到主机执行命令，循环间隔时间为2秒一次。

```
---
- hosts: 192.168.77.130 192.168.77.131 192.168.77.132
  tasks:
   - name: test
     shell: date
     delegate_to: "{{ item }}"
     run_once: true
     with_items:
       - "{{ play_hosts }}"
     loop_control:
       pause: 2
```


> 下列是 `本末` 提供的

## 在 shell 模块中使用脚本写法与 jinja2

```yaml
#  我们知道，任何能写变量的地方都能嵌套 jinja2 表达式
#  而 shell 模块中的内容到客户端渲染后也是一个可执行脚本
#  所以我们可以在 shell 内编写比平时更复杂的脚本

---
- name: Run shell
shell: |-
{% if foo is defined %}
mkdir -p /tmp/{{ foo }}
{% else %}
if [[ ! ${foo} ]];then
mkdir -p /var/lib/{{ bar }}
echo 'success'
else
echo 'falure'
fi
{% endif %}
```

## 展开 jinja2 中的一行的表达式

```yaml
## #  在使用 jiaja2 if 判断一个变量的时候，为了防止空格跟换行，我们经常会写在一行判断，但是展示却不太友好

- set_fact:
    GET_REPO: "{% if ENV == 'UAT' %}git@192.168.1.24:xnph-devops/conf-test.git{% else %}git@192.168.1.24:xnph-devops/conf.git{% endif %}"

#  一行冗长的表达式看着很不直观，我们可以借助 jinja2 的‘-’实现换行写，并忽略换行符
#  其中：
# |-  为块标签忽略换行
# {%- -%}  为忽略换行

---

- set_fact:
    GIT_REPO: |-
      {%- if ENV == 'UAT' -%}
      git@192.168.1.24:xnph-devops/conf-test.git
      {%- else -%}
      git@192.168.1.24:xnph-devops/conf.git
      {%- endif -%}
```

## 简易的 jinja2 'if else'表达式

```yaml
#  我们在编写 jinja2 if else 的表达式时，通常都是像这样的：
#  下面例子，索引 ID 小于 3 的都分配为 master

---

- set_fact:
      role: >-
        {%- if ansible_play_hosts.index(inventory_hostname) < 3 -%}
          master
        {%- else -%}
          slave
        {%- endif -%}

## #  我们利用 python 特性，可以简写如下：

- set_fact:
      role: "{{ ['slave','master'][ansible_play_hosts.index(inventory_hostname) < 3] }}"
#  即，先判断 ansible_play_hosts.index(inventory_hostname) < 3 是否成立，
#  如果成立，即 true，失败为 false
#  而 python 中 true==>1,false==>0
#  再取['slave','master']列表索引
#  其中 ansible_play_hosts 为当前任务执行的所有主机
```

## 获取当前时间

```yaml
#  在 setup 中其实有时间字段，但是被拆分，或者格式问题不好处理，我们通过内置方法能更便捷的获取
# 2019-07-02:11
#  格式可以自定义
- set_fact:
    datetime: "{{ '%Y-%d-%m:%H' | strftime() }}"

#  但是这样取的时间在客户端时间出现不一致的时候可能会出现问题，所以，我们通过另外一个办法
#  即：通过 lookup 插件(lookup 插件工作在控制端本机)，统一获取本机时间
- set_fact:
    datetime: "{{ lookup('pipe','date +%Y-%d-%m:%H') }}"
```

## 单独变量嵌套

```yaml
## #  假设我们有如下 playbook:

- hosts: group_a
  vars:
    foo_var: foo
    bar_var: bar
  tasks:
  - debug: msg="I like the {{ {{ key }}\_var }}"

#  以上执行必然是回报错的，
#  其中{{ key }}是我们想通过动态传入 foo 或者 bar 来获取 foo_var 或者 bar_var 的值
#  为此我们可以通过 lookup 的 vars 插件来查到目的,改造如下：

---

- hosts: group_a
  vars:
    foo_var: foo
    bar_var: bar
  tasks:
  - debug: msg="I like the {{ lookup('vars', key + '_var') }}"

#  执行传入 key=foo
ansible-playbook test.yml -e 'key=foo'
```

## 字典变量嵌套

```yaml
## #  假设我们有如下 playbook

- hosts: group_a
  vars:
    project:
      foo: foo_value
      bar: bar_value

tasks:
    - debug: msg="I like the {{ project.{{ key }} }}"

#  当然，以上执行是会报错的，
#  其中{{ key }}即为我想通过动态传入 foo 或者 bar 来获取 project 下的键值
#  为此我们可以这么写：

---

- hosts: group_a
  vars:
    project:
      foo: foo_value
      bar: bar_value

tasks:
    - debug: msg="I like the {{ project[key] }}"

#  执行传入 key=foo
ansible-playbook test.yml -e 'key=foo'
```

## 限制必须指定至少一个 tags 才能运行任务

```yaml
#  我们对多个任务做了 tags,而我们运行任务而不指定-t 时，默认会运行所有的任务
#  有时候这并不是我们所期望的，所以想当不指定 tags 时候不运行后面的任务

---

- hosts: localhost
  gather_facts: false
  tasks:
  - fail:
      msg: "你必须指定一个 tags[-t]"
    when: "ansible_run_tags == ['all']"
    run_once: true
  - debug: msg='hello {{ ansible_run_tags }}'
    tags:
    - abc

#  即，只要 ansible_run_tags 默认值为['all']时，任务就直接失败
\$ ansible-playbook abc.yml

PLAY [localhost] ******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******

TASK [fail] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
fatal: [localhost]: FAILED! => {"changed": false, "msg": "你必须指定一个 tags[-t]"}

PLAY RECAP ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
localhost                  : ok=0    changed=0    unreachable=0    failed=1

#  其中：
# ansible_run_tags 为 ansible 内置变量，默认值为['all']

9.访问其他主机的变量

## # A 主机有变量 foo=archive,B 主机想使用 A 主机的{{ foo }}怎么办呢？

- hosts: A:B
  tasks:

- debug: msg={{ hostvars['A']['foo'] }}

#  大部分的变量对象都存放在 hostvars 中
```

## 计算不同主机中相同变量的和

```yaml
#  什么意思呢，即，有 N 主机，有相同的变量 score,但是值是不一样的，现在想计算它们的 score 和
#  假定 inventory 如下：
\$ cat inventory.ini
[public]
10.18.12.213 score=77
10.18.16.166 score=100
10.18.16.167 score=81
10.18.16.168 score=56

#  计算 score 的和

- hosts: localhost
  tasks:
  - debug: msg={{ ansible_play_hosts_all | map('extract',hostvars,'score') | sum }}

#  执行结果
\$ ansible-playbook -i inventory.ini score_sum.yml

PLAY [public] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********

TASK [Gathering Facts] ******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******
ok: [10.18.16.167]
ok: [10.18.16.166]
ok: [10.18.16.168]
ok: [10.18.12.213]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213] => {
    "msg": "314"
}
ok: [10.18.16.166] => {
    "msg": "314"
}
ok: [10.18.16.167] => {
    "msg": "314"
}
ok: [10.18.16.168] => {
    "msg": "314"
}

PLAY RECAP ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
10.18.12.213               : ok=2    changed=0    unreachable=0    failed=0   
10.18.16.166               : ok=2    changed=0    unreachable=0    failed=0   
10.18.16.167               : ok=2    changed=0    unreachable=0    failed=0   
10.18.16.168               : ok=2    changed=0    unreachable=0    failed=0

#  其他例子：
#  获取所有主机的序列号，并以','连接
- debug: msg={{ ansible_play_hosts_all | map('extract',hostvars,'ansible_product_serial') | join(',') }}

#  获取所有主机内存的总和
- debug: msg={{ ansible_play_hosts_all | map('extract',hostvars,'ansible_memtotal_mb') | sum }}

#  其中：
# ansible_play_hosts_all 为当前任务执行的所有主机
# map 方法参考 python map
# sum 为计算 list 的和
```

## 使用本地命令的值作为循环参数

```yaml
#  使用 ls /tmp 的输出作为 loop 循环的值
#  其中：q == query
# query 与 lookup 都工作在本机

---
- hosts: localhost
  gather_facts:
  tasks:
  - debug: msg={{ item }}
    loop: "{{ q('lines','ls /tmp/') }}"
```

## 嵌套两个列表的循环任务

```yaml
#  假定有 2 个列表
#  a_list: [1,2]
#  b_list: ['jack', 'green', 'apple']
#  需要嵌套循环输出：
# jack-1,,green-1,apple-1,jack-2,green-2...

---

- hosts: localhost
  vars:
    a_list: [1,2]
    b_list: ['jack', 'green', 'apple']
  gather_facts: false
  tasks:
  - debug: msg="{{ item[1] }}-{{ item[0] }}"
    loop: "{{ a_list | product(b_list) | list }}"

\$ ansible-playbook loops.yml

PLAY [localhost] ******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [localhost] => (item=[1, u'jack']) => {
    "msg": "jack-1"
}
ok: [localhost] => (item=[1, u'green']) => {
    "msg": "green-1"
}
ok: [localhost] => (item=[1, u'apple']) => {
    "msg": "apple-1"
}
ok: [localhost] => (item=[2, u'jack']) => {
    "msg": "jack-2"
}
ok: [localhost] => (item=[2, u'green']) => {
    "msg": "green-2"
}
ok: [localhost] => (item=[2, u'apple']) => {
    "msg": "apple-2"
}

PLAY RECAP ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
localhost                  : ok=1    changed=0    unreachable=0    failed=0
```

## 全局任务滚动执行

```yaml
#  对于全局任务滚动执行
#  设置 serial 为 1，或者其他的数值，会按这个数量的主机去滚动执行任务
#  每个任务结尾会停顿 5s,再下一个主机
- hosts: public
  serial: 1
  gather_facts: false
  tasks:
    - name: I\'m the first task
      debug: msg="hello {{ inventory_hostname }}"
    - name: Sleep task
      wait_for:
        delay: 5
      when: (ansible_play_hosts_all.index[-1] != inventory_hostname)
#  对于最后一台主机，是不需要执行 wait_for 任务的，所以判断最后一台主机跳过 wait_for
#  其中：
# serial 为滚动执行的关键字，可以是数值或者百分比(%)
# ansible_play_hosts_all 为当前任务执行的所有主机
# inventory_hostname 为各个主机自己
```

## 部分任务滚动执行

```yaml
#  把需要滚动执行的任务放入 include_tasks 中，
#  利用 loop 循环所有当前执行的主机(ansible_play_hosts_all),即:
#  只有放入 other.yml 的任务会一台一台执行
#  设置 run_once 避免每个主机都多次重复执行

---

- hosts: public
  tasks:
  - debug: msg="I'm the Top public task"

- include_tasks: other.yml
    loop: "{{ ansible_play_hosts_all }}"
    loop_control:
      loop_var: target_host
    run_once: true

## # other.yml

- block:
  - shell: hostname -I
    register: res
  - debug: msg="I'm {{ res.stdout }}"
  delegate_to: "{{ target_host }}"

#  其中:
# ansible_play_hosts_all 为前期执行的所有 host
# loop_control 的 loop_var 把 item 赋值给 target_host,即，target_host==item,防止 other 里其他任务调用 loop，item 变量冲突
# run_once:每个循环对象只允许一次，不设置的话，会重复运行
# delegate_to 委派任务
#  另外，该方法有个缺点是由于委派者都是第一台主机，对应的 facts 变量都是该委派者的，所以没法使用其他主机的内置变量
#  故案例中也是使用 register+shell 来获取的主机名，而不是{{ inventory_hostname }}

#  执行结果：
\$ ansible-playbook rolling.yml

PLAY [public] ******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******

TASK [Gathering Facts] ******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******
ok: [10.18.16.167]
ok: [10.18.16.166]
ok: [10.18.16.168]
ok: [10.18.12.213]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213] => {
    "msg": "I'm the Top public task"
}
ok: [10.18.16.167] => {
    "msg": "I'm the Top public task"
}
ok: [10.18.16.166] => {
    "msg": "I'm the Top public task"
}
ok: [10.18.16.168] => {
    "msg": "I'm the Top public task"
}

TASK [include_tasks] ******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******\*\*******\*\*\*\*******\*\*\*\*******\*\*\*\*******
included: /tmp/other.yml for 10.18.12.213
included: /tmp/other.yml for 10.18.12.213
included: /tmp/other.yml for 10.18.12.213
included: /tmp/other.yml for 10.18.12.213

TASK [shell] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
changed: [10.18.12.213 -> 10.18.12.213]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213 -> 10.18.12.213] => {
    "msg": "I'm 10.18.12.213 "
}

TASK [shell] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
changed: [10.18.12.213 -> 10.18.16.166]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213 -> 10.18.16.166] => {
    "msg": "I'm 10.18.16.166 "
}

TASK [shell] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
changed: [10.18.12.213 -> 10.18.16.167]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213 -> 10.18.16.167] => {
    "msg": "I'm 10.18.16.167 "
}

TASK [shell] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
changed: [10.18.12.213 -> 10.18.16.168]

TASK [debug] ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
ok: [10.18.12.213 -> 10.18.16.168] => {
    "msg": "I'm 10.18.16.168 "
}

PLAY RECAP ********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********\*\*********
10.18.12.213               : ok=14   changed=4    unreachable=0    failed=0   
10.18.16.166               : ok=2    changed=0    unreachable=0    failed=0   
10.18.16.167               : ok=2    changed=0    unreachable=0    failed=0   
10.18.16.168               : ok=2    changed=0    unreachable=0    failed=0
```

## 在 when 里使用 jinja2 表达式

```yaml
#  在 when 里是可以使用 jinja2 表达式的，只要格式规范即可。
#  一行表达式：

---

- hosts: target_host
  tasks:
  - name: Show debug
    debug: msg='条件满足你就会看到我。'
    when: '{% if def_a_var|d("abc") == "abc" %}{{ foo | d("true") }}{% endif %}'

## #  等价的展开表达式

- hosts: target_host
  tasks:
  - name: Show debug
    debug: msg='条件满足你就会看到我。'
    when: |-
      {%- if def_a_var|d("abc") == "abc" -%}
      {{ foo | d("true") }}
      {%- endif -%}

#  执行（会有警告提示）:
ansible-playbook test.yml

PLAY [localhost] ********************************\*\*\*\*********************************\*\*\*\*********************************\*\*\*\*********************************

TASK [Gathering Facts] ********************************\*\*********************************\*\*********************************\*\*********************************
ok: [localhost]

TASK [Show debug] ********************************\*\*\*\*********************************\*\*\*********************************\*\*\*\*********************************
 [WARNING]: when statements should not include jinja2 templating delimiters such as {{ }} or {% %}. Found: {% if def_a_var|d("abc") == "abc" %}{{ foo | d("true") }}{% endif %}

ok: [localhost] => {
    "msg": "条件满足你就会看到我。"
}

PLAY RECAP **********************************\*\*\*\***********************************\*\***********************************\*\*\*\***********************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0
```

## 变量使用锚定和别名

```yaml
#  通常我们在定义多个类似变量时，不同变量有定义相同的内容
#  比如：

---

- hosts: localhost
  vars:
    project_1:
      port: 8080
      jvm: '-Xms1G -Xmx1G'
      run_user: devops
      root: /data/project_1
    project_2:
      port: 8080
      jvm: '-Xms1G -Xmx1G'
      run_user: devops
      root: /data/project_2
  tasks:
  - debug: var=project_1
  - debug: var=project_2

#  可以看到`project_2`中的很多键值都跟`project_1`中是一样的，
#  那么我们有什么办法简化呢？
#  对此，yaml 中提供了'&'来描定一个变量，并给描定的变量设置一个别名，
#  其他变量要引用锚定变量的值，需要再使用'<<'来引用并用\*指向设置的别名
#  另外，具有相同键的变量会被后者覆盖
#  即：project_2 的 root 会覆盖引用 project_1 的 root
#  修改如下：

---

- hosts: localhost
  vars:
    project_1: &conf_anchor
      port: 8080
      jvm: '-Xms1G -Xmx1G'
      run_user: devops
      root: /data/project_1
    project_2:
      <<: \*conf_anchor
      root: /data/project_2

 tasks:
 - debug: var=project_1
 - debug: var=project_2
#  其中：
# &  为锚定标识
# conf_anchor 为设置的别名
# <<  为合并键
# \*  为引用符
#  执行如下（变量覆盖会有警告）：
\$ ansible-playbook anchor.yml 
 [WARNING]: While constructing a mapping from /tmp/anchor.yml, line 10, column 7, found a duplicate dict key (root). Using last defined value only.

PLAY [localhost] ********************************************************************\*\*\*\*********************************************************************

TASK [Gathering Facts] ******************************************************************\*\*******************************************************************
ok: [localhost]

TASK [debug] **********************************************************************\*\*\*\***********************************************************************
ok: [localhost] => {
    "project_1": {
        "jvm": "-Xms1G -Xmx1G", 
        "port": 8080, 
        "root": "/data/project_1", 
        "run_user": "devops"
    }
}

TASK [debug] **********************************************************************\*\*\*\***********************************************************************
ok: [localhost] => {
    "project_2": {
        "jvm": "-Xms1G -Xmx1G", 
        "port": 8080, 
        "root": "/data/project_2", 
        "run_user": "devops"
    }
}

PLAY RECAP ************************************************************************\*\*************************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0
```

## 引用锚定变量

```yaml
- hosts: localhost
  vars:
    app:
      version: &my_version 1.1.1
      name:
        - "app_name"
        - \*my_version
  tasks:
    debug:
      msg: app version is "{{ app.name | join('-') }}".
#  执行
\$ ansible-playbook app.yml

PLAY [localhost] ********************************************************************\*\*\*********************************************************************

TASK [Gathering Facts] ******************************************************************\*******************************************************************
ok: [localhost]

TASK [debug] **********************************************************************\*\*\***********************************************************************
ok: [localhost] => {
    "msg": "app version is \"app_name-1.1.1\"."
}

PLAY RECAP ************************************************************************\*************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0
```

## 合并多个字典

```yaml
- hosts: localhost
  vars:
    center: &C
      x: 1
      y: 2
    round: &R
      r: 3.1415
    big:
      <<: [*C,*R]
      g: 3x10e
  tasks:
  - debug: var=big

#  执行：
ansible-playbook muti.yml

PLAY [localhost] ********************************************************************\*\*\*********************************************************************

TASK [Gathering Facts] ******************************************************************\*******************************************************************
ok: [localhost]

TASK [debug] **********************************************************************\*\*\***********************************************************************
ok: [localhost] => {
    "big": {
        "g": "3x10e", 
        "r": 3.1415, 
        "x": 1, 
        "y": 2
    }
}

PLAY RECAP ************************************************************************\*************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0
```

## 定义带空格的 key

```yaml
# yaml 是直接可以定义带空格的变量的
#  或者你可以用?:的方式
#  两者完全等价的。
- hosts: localhost
  vars:
    my_vars:
    #  直接定义
      'this is a key1': 'this is a value1'
    #  或者使用?:的方式
      ? 'this is a key2'
      : 'this is a value2'
  tasks:
  - debug: var=my_vars

#  执行  
\$ ansible-playbook space_var.yml

PLAY [localhost] ******************************************************************************\*\*******************************************************************************

TASK [Gathering Facts] **************************************************************************\*\*\*\***************************************************************************
ok: [localhost]

TASK [debug] ********************************************************************************\*\*********************************************************************************
ok: [localhost] => {
    "my_vars": {
        "this is a key1": "this is a value1", 
        "this is a key2": "this is a value2"
    }
}

PLAY RECAP ********************************************************************************\*\*\*\*********************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0
```

## 定义变量时，设置类型

```yaml
#  其实在定义变量时，我们是可以设置类型的。
#  当然，你在加引号与不加引号时就能解决大多的定义问题
- hosts: localhost
  vars:
    type_vars:
      is_str: !!str 9111
      is_int: !!int '8081'
      is_float: !!float 2019
      is_bool: !!bool 'yes'
  tasks:
  - debug: var=type_vars

#  执行：
\$ ansible-playbook type_vars.yml

PLAY [localhost] ******************************************************************************\*\*******************************************************************************

TASK [Gathering Facts] **************************************************************************\*\*\*\***************************************************************************
ok: [localhost]

TASK [debug] ********************************************************************************\*\*********************************************************************************
ok: [localhost] => {
    "type_vars": {
        "is_bool": true, 
        "is_float": 2019.0, 
        "is_int": 8081, 
        "is_str": "9111"
    }
}

PLAY RECAP ********************************************************************************\*\*\*\*********************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0
```

## 数字精度

```yaml
#  利用 format 可以保留精度
\$ ansible localhost -m debug -a "msg={{ '%0.2f -- %0.3f -- %d'| format(123,2.7,4.44) }}"
localhost | SUCCESS => {
"msg": "123.00 -- 2.700 -- 4"
}
```

## 循环(多实例)任务触发 handlers 重启任务

```yaml
# 我们在使用ansible部署多实例任务时
# 多个实例完成后需要触发handler任务来重启各个实例（实例名称通常是动态/不固定的），
# 而通常实例的服务名称是有区别的，而且是按需重启(满足状态变化)，逐个重启
# 我们可以借助json_query的filter特性来获取changed状态满足条件的实例来循环重启
# 如，实例变量如下:
---
  vars:
    redis_ins_port:
      - 6379
      - 6380
      - 6381
# 我们要循环复制实例模板到客户端，触发handler后只重启发生变化的实例
# 复制模板并将任务状态注册到变量
- name: 
  template: src=redis.conf.j2 dest=/etc/redis/redis_{{ server_port }}.conf"
  loop_control:
    loop_var: server_port
  loop: "{{ redis_ins_port }}"
  register: task_status
  notify:
  - Restart redis
  
# handler任务
# 其中，json_query为查询task_status中changed的状态为true的所有server_port
---
- name: Restart redis
  systemd: name=redis_{{ item }} state=restarted" 
  loop: "{{ task_status | json_query('results[?changed].server_port') }}
```

## 修改列表内的所有字段值，生成新的列表

```yaml
# 我们在创建例如mongodb replicasets时，使用模块示例如下：
# Create a replicaset called 'rs0' with the 3 provided members
- name: Ensure replicaset rs0 exists
  mongodb_replicaset:
  login_host: localhost
  login_user: admin
  login_password: admin
  replica_set: rs0
  members:
  - mongodb1:27017
  - mongodb2:27017
  - mongodb3:27017
  when:ansible_play_hosts.index(inventory_hostname) == 0
# 对于其中的member如何能不固定通过方法自动创建呢？
# 试想，我们已经有了执行的主机列表ansible_play_hosts
# (虽然里面的值可能是别名,即：inventory_hostname)
# 但是这个列表么有对应的端口，即我们需要修改列表里的每一项，添加一个端口即可
# 像这样：['10.18.1.190:27017','10.18.1.191:27017','10.18.1.192:27017']
# 改动如下：
- name: Ensure replicaset rs0 exists
  mongodb_replicaset:
  login_host: localhost
  login_user: admin
  login_password: admin
  replica_set: rs0
  members: >-
  {{ anible_play_hosts | map('extract', hostvars, 'ansible_default_ipv4') | list | json_query('[*].address') |map('regex_replace','(.*)','\\1:' + '27017' | list }}
  when: ansible_play_hosts.index(inventory_hostname) == 0
# 其中:
# ansible_play_hosts为当前执行的所有主机列表
# 第一个map extract为提取hostvars中每个ansible_play_hosts的值作为键，并取ansible_default_ipv4,就像：hostvars[inventory_hostname]['ansible_default_ipv4']
# list把map对象转换成列表
# json_query把列表内每个address提取出来变成新的列表,到此是为了提取IP地址列表，当然，你ansible_play_hosts是IP地址的话可以不用这么麻烦
# 第二个map regex_replace把每个IP地址变成IP+:27017，
# 最后再把我们的map对象转成list，得到我们想要的：['10.18.1.190:27017','10.18.1.191:27017','10.18.1.192:27017']
```

## 给集群主机自动分配 ID/角色

> 使用主机变量

```yaml
[cluster]
node01 ansible_host=10.18.1.190 id=1 role=master
node02 ansible_host=10.18.1.191 id=2 role=slave
node03 ansible_host=10.18.1.192 id=3 role=slave
```

> 使用执行主机列表的索引定义 ID, 需要同时执行集群主机

```yaml
# hosts
[cluster]
node01 ansible_host=10.18.1.190
node02 ansible_host=10.18.1.191
node03 ansible_host=10.18.1.192

# tasks
---
- hosts: cluster
  gather_facts: false
  tasks:
  # ansible_play_hosts_all是当前执行的所有主机列表，类型为有序list,
  # inventory_hostname为各自执行主机的名字
  # 即：在list中找出各自名字的索引做为ID值
  - set_fact: id={{ ansible_play_hosts_all.index(inventory_hostname) }}

  # 使用id时候请转换成整型，set_fact不会帮你转换数据类型
  - debug: msg="{{ inventory_hostname }} --> ID --> {{ id | int }}"

  # 递增10
  - set_fact: id={{ ansible_play_hosts_all.index(inventory_hostname) * 10 }}

  # 递减5
  - set_fact: id={{ 100 - ansible_play_hosts_all.index(inventory_hostname) * 5 }}
```

**定义角色**

```yaml
---
- hosts: cluster
  gather_facts: false
  tasks:
    # 这里为了更好的展示，使用了>换行语句
    - set_fact:
        role: >-
          {# 即，索引ID小于3的都分配为master #}
          {%- if ansible_play_hosts_all.index(inventory_hostname) < 3 -%}
            master
          {%- else -%}
            slave
          {%- endif -%}

    - debug: msg="{{ inventory_hostname }} --> role --> {{ role }}"
```

**既分配 id 又分配角色**

```yaml
---
- hosts: cluster
  gather_facts: false
  tasks:
    - set_fact: id={{ ansible_play_hosts_all.index(inventory_hostname) }}

    # id小于3的都视为master,记得要转换为整形，set_fact不会帮你处理数据类型
    # PS: 这里用了python的小技巧，用jinja2的if去判断也是一样的
    - set_fact:
        role: "{{ ['slave','master'][id|int<3] }}"

    - debug: msg="ID--> {{ id | int }}, role --> {{ role }}"
```
