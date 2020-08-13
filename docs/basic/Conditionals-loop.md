# 13. 条件判断与循环

## 条件判断

ansible 使用`when`语句后的表达式来判断该步骤是否执行。 

### When 语句

在when 后面使用没有`{{ }}` 的 `Jinja2` 表达式，结果为True则执行任务。

>  不需要使用 {{}} 来在条件语句中使用变量

```yaml
#  若操作系统是 Debian 时就执行关机操作
tasks:
    - name: "shut down Debian flavored systems"
      command: /sbin/shutdown -t now
      when: ansible_os_family == "Debian"
```

>  ansible_os_family  是 facts 或 vars 的变量

您还可以使用括号对条件进行分组

```YAML
tasks:
  - name: "shut down CentOS 6 and Debian 7 systems"
    command: /sbin/shutdown -t now
    when: (ansible_facts['distribution'] == "CentOS" and ansible_facts['distribution_major_version'] == "6") or
          (ansible_facts['distribution'] == "Debian" and ansible_facts['distribution_major_version'] == "7")
```

可以使用列表形式来表示条件为 **and** 的关系

```yaml
tasks:
  - name: "shut down CentOS 6 systems"
    command: /sbin/shutdown -t now
    when:
      - ansible_facts['distribution'] == "CentOS"
      - ansible_facts['distribution_major_version'] == "6"
```

许多Jinja2测试和过滤器也可以用于when语句，其中一些是唯一的，由Ansible提供。

```yaml
tasks:
  - command: /bin/false
    register: result
    ignore_errors: True

  - command: /bin/something
    when: result is failed

  # 忽略一个语句的错误，然后决定基于成功或失败有条件地做一些事情。
  - command: /bin/something_else
    when: result is succeeded

  - command: /bin/still/something_else
    when: result is skipped
```

 字符串转换为数字型再去比较

```yaml
tasks:
  - shell: echo "only on Red Hat 6, derivatives, and later"
    when: ansible_facts['os_family'] == "RedHat" and ansible_facts['lsb']['major_release']|int >= 6
```

也可以使用定义的变量，注意字符串(类似:"yes", "on", "1","true")需要用`|bool` 转成布尔值。

```yaml
- hosts: node
  vars:
    epic: true
    monumental: "yes"
  tasks:
    - shell: echo "This certainly is epic!"
      when: epic or monumental | bool
    - shell: echo "This certainly isn't epic!"
      when: not epic
```

如果未设置所需的变量，则可以使用 Jinja2 定义的测试跳过或失败。例如:

```yaml
tasks:
    - shell: echo "I've got '{{ foo }}' and am not afraid to use it!"
      when: foo is defined

    - fail: msg="Bailing out. this play requires 'bar'"
      when: bar is undefined
```

### 与循环一起使用

依次遍历列表，当列表里得数字大于5时执行任务

```yaml
tasks:
    - command: echo {{ item }}
      loop: [ 0, 2, 4, 6, 8, 10 ]
      when: item > 5
```

 当变量不存在时，直接跳过

```yaml
- command: echo {{ item }}
  loop: "{{ mylist | default([]) }}"
  when: item > 5
```

如果变量是字典

```yaml
- command: echo {{ item.key }}
  loop: "{{ query('dict', mydict|default({})) }}"
  when: item.value > 5
```

### 使用自定义的facts值做判断

你可以开发一个模块来设置facts数据，并将其作为变量结果返回，后续的任务就可以使用这个变量了。

```yaml
tasks:
    - name: gather site specific fact data
      action: site_facts
    - command: /usr/bin/thingy
      when: my_custom_fact_just_retrieved_from_the_remote_system == '1234'
```

 

###　角色包含使使用when

 如果您有多个任务都共享同一个条件语句，则可以将该条件附加到task include语句上，如下：

```yaml
- import_tasks: tasks/sometasks.yml
  when: "'reticulating splines' in output"
```

使用在角色上

```yaml
- hosts: webservers
  roles:
     - role: debian_stock_config
       when: ansible_facts['os_family'] == 'Debian'
```

>  当条件句与`include*`任务一起使用时，它仅应用于包含任务本身，而不应用于包含文件中的任何其他任务。 

### 有条件的导入

 有时你会想要根据特定的标准在剧本中做一些不同的事情 。拥有一个适用于多个平台和操作系统版本的剧本就是一个很好的例子。 

 例如，Apache包的名称在CentOS和Debian之间不同，但是在Ansible Playbook中， 你可以用最简洁的语法来处理这个

```yaml
---
# for vars/RedHat.yml
apache: httpd
somethingelse: 42
---
# for vars/Debian.yml
apache: apache2
somethingelse: 42

---
# for playbook.yml
- hosts: all
  remote_user: root
  vars_files:
    - "vars/common.yml"
    - [ "vars/{{ ansible_facts['os_family'] }}.yml", "vars/os_defaults.yml" ]
  tasks:
  - name: make sure apache is started
    service: name={{ apache }} state=started
```

> ansible_facts['os_family'] 来确定执行的主机系统

### 基于变量选择文件和模板

```yaml
- name: template a file
  template:
      src: "{{ item }}"
      dest: /etc/myapp/foo.conf
  loop: "{{ query('first_found', { 'files': myfiles, 'paths': mypaths}) }}"
  vars:
    myfiles:
      - "{{ansible_facts['distribution']}}.conf"
      -  default.conf
    mypaths: ['search_location_one/somedir/', '/opt/other_location/somedir/']
```

 

### 使用注册变量判断

 将给定命令的结果存储在变量中， 并在后续的任务中使用。

```yaml
- name: test play
  hosts: all

  tasks:

      - shell: cat /etc/motd
        register: motd_contents

      - shell: echo "motd contains the word hi"
        when: motd_contents.stdout.find('hi') != -1
```

 如果注册的结果被转换为列表(或者已经是列表)，则可以在任务的循环中使用 。

```yaml
- name: registered variable usage as a loop list
  hosts: all
  tasks:

    - name: retrieve the list of home directories
      command: ls /home
      register: home_dirs

    - name: add home dirs to the backup spooler
      file:
        path: /mnt/bkspool/{{ item }}
        src: /home/{{ item }}
        state: link
      loop: "{{ home_dirs.stdout_lines }}"
      # same as loop: "{{ home_dirs.stdout.split() }}"### 
```

### failed_when

满足给定的条件时，使任务失败

```yaml
tasks:
    - command: echo faild.
      register: command_result
      failed_when: "'faild' in command_result.stdout"
    
    - debug: msg="echo test"
```

还可以写成这样

```yaml
tasks:
    - command: echo faild.
      register: command_result
      ignore_errors: True

    - name: fail the echo
      fail: msg="the command failed"
      when: "'faild' in command_result.stdout"

    - debug: msg="echo test"
```

> fail 模块是产生一个错误信息

### changed_when

如果说一个命令没有更改任何事物，就可以为其设置为没有更改状态

```yaml
tasks:
    - name: Install dependencies via Composer.
      command: "/usr/local/bin/composer global require phpunit/phpunit --prefer-dist"
      register: composer
      changed_when: "'Nothing to install or update' not in composer.stdout"
```

## 循环

有时你想要重复一个任务多次。在计算机编程中，这叫做循环， Ansible提供了两个用于创建循环的关键字：`loop`和`with_<lookup>`。 

-  我们在Ansible 2.5中添加了`loop`。它还不是`with_<lookup>`的完整替代品，但是我们建议在大多数用例中使用它。 
- 我们并没有反对使用`with_<lookup>`—在可预见的将来，该语法仍然有效。
- 我们一直在改进`loop`语法，请注意修改日志。

### 比较`loop` 和 `with_*`

- `with_<lookup>`关键字依赖于`Lookup`插件
- `loop`关键字相当于`with_list`，是简单循环的最佳选择。
- `loop`关键字不会接受字符串作为输入 
- 一般来说, 所有`with_*`的使用，都可以使用`loop`替代
- 使用` with_items `时要注意， 因为`with_items`会执行隐式单级展平。 您可能需要使用带有循环的flatten(1)来匹配确切的结果。

```
with_items:
  - 1
  - [2,3]
  - 4
```

使用loop表达

```yaml
loop: "{{ [1, [2,3] ,4] | flatten(1) }}"
```

- 在使用查找的功能时, 都不应该将`with_*`转换成`loop`

```yaml
loop: "{{ lookup('fileglob', '*.txt', wantlist=True) }}"
```

使用`with_*`可以很简洁的表达

```yaml
with_fileglob: '*.txt'
```

 

### 标准循环

#### 遍历列表

添加多个用户

```yaml
- name: add several users
  user:
    name: "{{ item }}"
    state: present
    groups: "wheel"
  loop:
     - testuser1
     - testuser2
```

也可以直接引用变量列表

```yaml
loop: "{{ somelist }}"
```

这两个例子等价于

```yaml
- name: add user testuser1
  user:
    name: "testuser1"
    state: present
    groups: "wheel"

- name: add user testuser2
  user:
    name: "testuser2"
    state: present
    groups: "wheel"
```

有时，如果模块可以接受列表的话，就不需要使用循环来传递。例如yum包管理的

```yaml
- name: optimal yum
  yum:
    name: "{{  list_of_packages  }}"
    state: present

- name: non-optimal yum, slower and may cause issues with interdependencies
  yum:
    name: "{{  item  }}"
    state: present
  loop: "{{  list_of_packages  }}"
```

####  遍历散列列表

如果你有一个散列列表，可以在循环中引用子键。

```yaml
- name: add several users
  user:
    name: "{{ item.name }}"
    state: present
    groups: "{{ item.groups }}"
  loop:
    - { name: 'testuser1', groups: 'wheel' }
    - { name: 'testuser2', groups: 'root' }
```

> 添加多个用户，并将用户加入不同的组内。

#### 遍历字典

要遍历字典，请使用`dict2items`过滤器将字典转换成散列：

```yaml
- name: create a tag dictionary of non-empty tags
  set_fact:
    tags_dict: "{{ (tags_dict|default({}))|combine({item.key: item.value}) }}"
  loop: "{{ tags|dict2items }}"
  vars:
    tags:
      Environment: dev
      Application: payment
      Another: "{{ doesnotexist | default() }}"
  when: item.value != ""
```

> default() 可以在变量未定义的时候为其设置一个默认值。

####  循环中注册变量 

```yaml
- shell: "echo {{ item }}"
  loop:
    - "one"
    - "two"
  register: echo
```

当您在循环中使用register时，放在变量中的数据结构将包含一个results属性，该属性是来自模块的所有执行的列表。这与不使用循环使用register时返回的数据结构不同

```json
{
    "changed": true, 
    "msg": "All items completed", 
    "results": [
        {
            "ansible_loop_var": "item", 
            "changed": true, 
            "cmd": "echo one", 
            "delta": "0:00:00.003978", 
            "end": "2020-03-30 21:13:24.329114", 
            "failed": false, 
            "invocation": {
                "module_args": {
                    "_raw_params": "echo one", 
                    "_uses_shell": true, 
                    "argv": null, 
                    "chdir": null, 
                    "creates": null, 
                    "executable": null, 
                    "removes": null, 
                    "stdin": null, 
                    "stdin_add_newline": true, 
                    "strip_empty_ends": true, 
                    "warn": true
                }
            }, 
            "item": "one", 
            "rc": 0, 
            "start": "2020-03-30 21:13:24.325136", 
            "stderr": "", 
            "stderr_lines": [], 
            "stdout": "one", 
            "stdout_lines": [
                "one"
            ]
        }, 
        {
            "ansible_loop_var": "item", 
            "changed": true, 
            "cmd": "echo two", 
            "delta": "0:00:00.003879", 
            "end": "2020-03-30 21:13:24.621379", 
            "failed": false, 
            "invocation": {
                "module_args": {
                    "_raw_params": "echo two", 
                    "_uses_shell": true, 
                    "argv": null, 
                    "chdir": null, 
                    "creates": null, 
                    "executable": null, 
                    "removes": null, 
                    "stdin": null, 
                    "stdin_add_newline": true, 
                    "strip_empty_ends": true, 
                    "warn": true
                }
            }, 
            "item": "two", 
            "rc": 0, 
            "start": "2020-03-30 21:13:24.613500", 
            "stderr": "", 
            "stderr_lines": [], 
            "stdout": "two", 
            "stdout_lines": [
                "two"
            ]
        }
    ]
}
```

后续使用注册变量来检查命令执行情况

```yaml
- name: Fail if return code is not 0
  fail:
    msg: "The command ({{ item.cmd }}) did not have a 0 return code"
  when: item.rc != 0
  loop: "{{ echo.results }}"
```

在循环过程中，也可以使用当前的模块结果

```yaml
- shell: echo "{{ item }}"
  loop:
    - one
    - two
  register: echo
  changed_when: echo.stdout != "one"
```



### 复杂循环

#### 遍历嵌套列表

您可以使用Jinja2表达式迭代复杂的列表。例如， 分别给用户授予3个数据库的所有权限

```yaml
- name: give users access to multiple databases
  mysql_user:
    name: "{{ item[0] }}"
    priv: "{{ item[1] }}.*:ALL"
    append_privs: yes
    password: "foo"
  loop: "{{ ['alice', 'bob'] | product(['clientdb', 'employeedb', 'providerdb'])|list }}"
```

#### 在满足条件之前重试任务

 可以使用`until`关键字重试任务，直到满足特定条件。 

```yaml
- shell: /usr/bin/foo
  register: result
  until: result.stdout.find("all systems go") != -1
  retries: 5
  delay: 10
```

> 此任务最多运行5次，每次尝试之间的延迟为10秒。如果标准输出中有`all systems go`字符串，则任务成功。重试的默认值是3，延迟是5。 

#### 循环主机清单

```yaml
# 输出所有主机信息
- debug:
    msg: "{{ item }}"
  loop: "{{ groups['all'] }}"

# 输出当前play运行的主机信息
- debug:
    msg: "{{ item }}"
  loop: "{{ ansible_play_batch }}"
  
# 显示清单中的所有主机
- debug:
    msg: "{{ item }}"
  loop: "{{ query('inventory_hostnames', 'all') }}"

# 除组www外的所有主机
- debug:
    msg: "{{ item }}"
  loop: "{{ query('inventory_hostnames', 'all:!www') }}"
```

#### 使用`query`还是`lookup`

loop关键字需要一个列表作为输入，默认情况下，`lookup`关键字返回一个逗号分隔的值字符串 ,而`query`返回的是一个列表。

如果使用`lookup`返回列表，则可以添加` wantlist=True  `强制返回列表。

```yaml
loop: "{{ query('inventory_hostnames', 'all') }}"

loop: "{{ lookup('inventory_hostnames', 'all', wantlist=True) }}"
```

#### 循环控制

使用`loop_control`关键字来管理循环。

##### 使用`label`限制loop的输出

```yaml
- name: create servers
  digital_ocean:
    name: "{{ item.name }}"
    state: present
  loop:
    - name: server1
      disks: 3gb
      ram: 15Gb
      network:
        nic01: 100Gb
        nic02: 10Gb
        ...
  loop_control:
    label: "{{ item.name }}"
```

 这个任务的输出将只显示每个项目的名称字段，而不是多行`{{item}}`变量的整个内容。 

> 这是为了使控制台输出更具可读性，而不是为了保护敏感数据。如果循环中有敏感数据，则设置`no_log: yes`，以防止泄漏。 

##### 循环间隔时间

使用`pause`指令控制循环中每个项执行之间的时间(以秒为单位)

```yaml
- name: create servers, pause 3s before creating next
  digital_ocean:
    name: "{{ item }}"
    state: present
  loop:
    - server1
    - server2
  loop_control:
    pause: 3
```

##### 循环索引

使用` index_var` 指令来跟踪当前循环的索引

```yaml
- name: count our fruit
  debug:
    msg: "{{ item }} with index {{ my_idx }}"
  loop:
    - apple
    - banana
    - pear
  loop_control:
    index_var: my_idx
```

##### 更改循环的变量名称

循环的默认变量名称为`item`,可以通过`loop_var`来修改此项,从而避免覆盖`include_tasks`任务里的循环变量

```yaml
# main.yml
- include_tasks: inner.yml
  loop:
    - 1
    - 2
    - 3
  loop_control:
    loop_var: outer_item

# inner.yml
- debug:
    msg: "outer item={{ outer_item }} inner item={{ item }}"
  loop:
    - a
    - b
    - c
```

##### 扩展变量

从Ansible 2.8开始，你可以使用扩展选项来获取扩展循环信息。此选项将公开以下信息。

| 变量                     | 描述                                           |
| ------------------------ | ---------------------------------------------- |
| `ansible_loop.allitems`  | 循环中所有项的列表                             |
| `ansible_loop.index`     | 循环的当前迭代次数。(从1开始)                  |
| `ansible_loop.index0`    | 循环的当前迭代次数。(从0开始)                  |
| `ansible_loop.revindex`  | 循环结束后的迭代次数。(从1开始)                |
| `ansible_loop.revindex0` | 循环结束后的迭代次数。(从0开始)                |
| `ansible_loop.first`     | 如果是第一次迭代，返回`True`                   |
| `ansible_loop.last`      | 如果是最后一次迭代，返回`True`                 |
| `ansible_loop.length`    | 循环中的项数                                   |
| `ansible_loop.previtem`  | 循环前一次迭代的项。在第一次迭代中未定义。     |
| `ansible_loop.nextitem`  | 循环的后续迭代中的项。在最后一次迭代中未定义。 |

```
loop_control:
  extended: yes
```

#### 获取`loop_var`的名称

从ansible2.8开始，你可以通过` ansible_loop_var` 来获取 ` loop_control.loop_var `的值

```yaml
"{{ lookup('vars', ansible_loop_var) }}"
```

### 从with_*迁移到loop

随着Ansible 2.5的发布，执行循环的推荐方法是使用`loop`关键字，而不是`with_*`样式的循环。 

在许多情况下，`loop`语法使用过滤器更好地表达，而不是使用更复杂的`query`或`lookup`。 

下面的示例将展示如何将许多常见的`with_`样式循环转换为`loop`。

#### with_list

遍历列表

```yaml
- name: with_list
  debug:
    msg: "{{ item }}"
  with_list:
    - one
    - two

- name: with_list -> loop
  debug:
    msg: "{{ item }}"
  loop:
    - one
    - two
```

#### with_items

遍历列表

```yaml
- name: with_items
  debug:
    msg: "{{ item }}"
  with_items: "{{ items }}"

- name: with_items -> loop
  debug:
    msg: "{{ item }}"
  loop: "{{ items | flatten(levels=1) }}"
  

- name: with_items with muliti lists within a list
  debug: msg={{ item }}
  with_items: 
    - "{{ foo }}"
    - "{{ bar }}"
        
- name: loop with a list within lists of list  ( {{ list | union(list) }} )
  debug: msg={{ item }}
  loop: "{{ foo | union(bar) }}"

- name: loop with a list within lists of list  ( {{ list + list }} )
  debug: msg={{ item }}
  loop: "{{ foo + bar }}"
```

#### with_indexed_items

遍历列表和索引

```yaml
- name: with_indexed_items
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  with_indexed_items: "{{ items }}"

- name: with_indexed_items -> loop
  debug:
    msg: "{{ index }} - {{ item }}"
  loop: "{{ items | flatten(levels=1) }}"
  loop_control:
    index_var: index
```

#### with_flattened

合并列表

```yaml
- name: with_flattened
  debug:
    msg: "{{ item }}"
  with_flattened: "{{ items }}"

- name: with_flattened -> loop
  debug:
    msg: "{{ item }}"
  loop: "{{ items | flatten }}"
```

#### with_together

并行遍历列表

```yaml
- name: with_together
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  with_together:
    - "{{ list_one }}"
    - "{{ list_two }}"

- name: with_together -> loop
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  loop: "{{ list_one|zip(list_two)|list }}"
```

#### with_dict

遍历字典

```yaml
- name: with_dict
  debug:
    msg: "{{ item.key }} - {{ item.value }}"
  with_dict: "{{ dictionary }}"

- name: with_dict -> loop (option 1)
  debug:
    msg: "{{ item.key }} - {{ item.value }}"
  loop: "{{ dictionary|dict2items }}"

- name: with_dict -> loop (option 2)
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  loop: "{{ dictionary|dictsort }}"
  
- name: with_dict lookup
  debug:
    msg: "with_dict_lookup: item.key is '{{ item.key }}' and item.value is '{{ item.value }}'"
  loop: "{{ lookup('dict', dictionary) }}"

- name: with_dict query
  debug:
    msg: "with_dict_query: item.key is '{{ item.key }}' and item.value is '{{ item.value }}'"
  loop: "{{ query('dict', dictionary) }}"
```

#### with_sequence

以递增的数字顺序生成项序列

```yaml
- name: with_sequence
  debug:
    msg: "{{ item }}"
  with_sequence: start=0 end=4 stride=2 format=testuser%02x

- name: with_sequence -> loop
  debug:
    msg: "{{ 'testuser%02x' | format(item) }}"
  # range is exclusive of the end point
  loop: "{{ range(0, 4 + 1, 2)|list }}"
  
- name: with sequence loop and lookup
  debug:
    msg: "sequence_lookup: item is '{{ item }}'"
  # end is inclusive of the end point
  loop: "{{ lookup('sequence', 'start=0 end=4 stride=2 format=testuser%02x', wantlist=True) }}"

- name: with sequence loop and query
  debug:
    msg: "sequence_query: item is '{{ item }}'"
  # end is inclusive of the end point
  loop: "{{ query('sequence', 'start=0 end=4 stride=2 format=testuser%02x') }}"
```

#### with_subelements

遍历子元素

```yaml
- name: with_nested
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  with_nested:
    - "{{ list_one }}"
    - "{{ list_two }}"

- name: with_nested -> loop
  debug:
    msg: "{{ item.0 }} - {{ item.1 }}"
  loop: "{{ list_one|product(list_two)|list }}"
```

#### with_random_choice

随机选择列表中得一个值

```yaml
- name: with_random_choice
  debug:
    msg: "{{ item }}"
  with_random_choice: "{{ my_list }}"

- name: with_random_choice -> loop (No loop is needed here)
  debug:
    msg: "{{ my_list|random }}"
  tags: random
```
