# 9. 变量

虽然自动化的存在是为了让事情更容易重复，但并非所有的系统都是完全相同的;有些可能需要的配置与其他的稍有不同。在某些情况下，所观察到的一个系统的行为或状态可能会影响您配置其他系统的方式。例如，您可能需要找到一个系统的IP地址，并将其用作另一个系统上的配置值。

Ansible使用 **变量(*variables* )** 来帮助处理系统之间的差异。



### 创建有效的变量名

在使用变量之前，你要先知道什么是 **有效** 的变量名称, 以下是变量名的遵循规则

- 变量名称应为 **字母**，**数字** 和 **下划线**。 

- 变量应始终 **以字母开头**。

- 变量名不应与python属性和方法名冲突。

 YAML还支持将键映射到值的字典

```yaml
foo:
  field1: one
  field2: two
```

然后，您可以使用方括号符号或点符号来引用字典中的特定字段

```yaml
foo['field1']
foo.field2
```

!!! note
	如果选择使用点表示法，请注意某些键可能会引起问题，因为它们与python词典的属性和方法冲突。 如果您使用以两个下划线开头和结尾的键（这些键在python中保留了特殊含义）或为任何已知的公共属性，则应使用方括号而不是点符号。add`, `append`, `as_integer_ratio`, `bit_length`, `capitalize`, `center`, `clear`, `conjugate`, `copy`, `count`, `decode`, `denominator`, `difference`, `difference_update`, `discard`, `encode`, `endswith`, `expandtabs`, `extend`, `find`, `format`, `fromhex`, `fromkeys`, `get`, `has_key`, `hex`, `imag`, `index`, `insert`, `intersection`, `intersection_update`, `isalnum`, `isalpha`, `isdecimal`, `isdigit`, `isdisjoint`, `is_integer`, `islower`, `isnumeric`, `isspace`, `issubset`, `issuperset`, `istitle`, `isupper`, `items`, `iteritems`, `iterkeys`, `itervalues`, `join`, `keys`, `ljust`, `lower`, `lstrip`, `numerator`, `partition`, `pop`, `popitem`, `real`, `remove`, `replace`, `reverse`, `rfind`, `rindex`, `rjust`, `rpartition`, `rsplit`, `rstrip`, `setdefault`, `sort`, `split`, `splitlines`, `startswith`, `strip`, `swapcase`, `symmetric_difference`, `symmetric_difference_update`, `title`, `translate`, `union`, `update`, `upper`, `values`, `viewitems`, `viewkeys`, `viewvalues`, `zfill

 

### 变量使用

#### 通过命令行传递变量(extra vars)

通过`--extra-vars`或`-e`选项来传递`key=value`变量

```bash
ansible-playbook release.yml -e "user=starbuck"
```

当然，也可以传递字典

```bash
ansible-playbook arcade.yml -e '{"pacman":"mrs","ghosts":["inky","pinky","clyde","sue"]}'
```

变量文件的话，也是可以的

```bash
ansible-playbook test.yml -e @variables.yaml
```

yaml格式的变量，也是可以传递的

```bash
ansible-playbook arcade.yml --extra-vars '
pacman: mrs
ghosts:
  - inky
  - pinky
  - clyde
  - sue'
```

#### 在inventory 中定义变量（inventory vars)

通常，您需要为单个主机或清单中的一组主机设置变量。

```ini
host3 http_port=80                        # 定义主机变量
[webservers:vars]                        # 定义组的变量
ntp_server= ntp.example.com
```

#### 在play中定义变量（play vars）

你可以通过`play`的`vars` 关键字来定义变量

```yaml
- hosts: webservers
  vars:
    http_port: 80
```

#### 在角色和文件包含中定义变量(play include_vars)

通过在playbook中定义`include_vars` 模块，来包含变量文件

```yaml
- hosts: webservers
  tasks:
    include_vars: myvars.yml
```

#### 在play中包含变量文件(play vars_files)

你可以通过`play`的`vars_files` 关键字来定义变量的文件

```yaml
- hosts: webservers
  vars_files:
    - /vars/external_vars.yml
```

#### 定义角色默认变量（role defaults vars）

在角色目录中添加一个`defaults/main.yml`文件。文件里存储着`yaml`或`json`格式的数据。

```yaml
# file: roles/x/defaults/main.yml
http_port: 80

```

#### 定义角色变量（role  vars）

在角色目录中添加一个`vars/main.yml`文件。文件里存储着`yaml`或`json`格式的数据。

```yaml
# file: roles/x/vars/main.yml
http_port: 80
```

#### 以交互方式获取变量值( play vars_prompt)

```yaml
---
- hosts: server
  vars_prompt:
    - name: web
      prompt: 'Please input the web server:'
      private: no
```

#### 定义角色变量（role and include vars)

在引入角色的时候，可以像角色传递一些变量

```yaml
roles:
  - { role: app_user, name: Ian    }
```

> `name` 就是传递给角色的变量

#### 注册变量（registered vars）

变量的另一个主要用途是运行命令并将该命令的结果注册为变量。当您执行一个任务并将返回值保存在一个变量中供以后的任务使用时，您将创建一个已注册的变量。

```yaml
---
- hosts: all 
  tasks:

    - shell: uptime
      register: result

    - name: show uptime
      debug: var=result
```

> 此选项将任务的结果存储在变量中，结果参数可以用在模版中。名称为result，使用debug来输出result的信息。也可以使用 `{{ hostvars[inventory_hostname].result.stdout }}` 可以获得注册变量的

结果因模块而异。 每个模块的文档都包含一个`RETURN`部分，描述该模块的返回值。 要查看特定任务的值，请使用`-v`运行您的剧本。

注册变量仅存储在内存中, 当您用循环在任务中注册一个变量时，已注册的变量包含循环中每个项的值。在循环期间放置在变量中的数据结构将包含一个results属性，它是来自模块的所有响应的列表。



以下是一些重要的注册变量的组件：

- changed: 显示是否已更改
- cmd:  执行的命令
- rc: 命令的返回码
- stdout:命令的输出
- stdout_lines: 逐行输出
- stderr: 如果有错误，则输出错误的信息
- stderr_lines: 逐行输出错误信息


#### 动态创建fact变量

使用`set_fact` 在运行中设置 facts 变量

```yaml
tasks:
  - command: whoami
    register: result
  - set_fact: w={{result.stdout}}
  - debug: var=w
```



### 变量优先级

上面列出了大部分的变量定义位置，这些不同位置的变量都是有优先级的，在不同位置上同时设置时，高优先级的会覆盖掉低优先级的变量，

下面是优先级从最小到最大的顺序(最后列出的变量是最高优先级)

1. command line values (eg “-u user”)  
2. role defaults 
3. inventory file or script group vars
4. inventory group_vars/all
5. playbook group_vars/all
6. inventory group_vars/*
7. playbook group_vars/* 
8. inventory file or script host vars
9. inventory host_vars/* 
10. playbook host_vars/* 
11. host facts / cached set_facts 
12. play vars
13. play vars_prompt
14. play vars_files
15. role vars (defined in role/vars/main.yml)
16. block vars (only for tasks in block)
17. task vars (only for the task)
18. include_vars
19. set_facts / registered vars
20. role (and include_role) params
21. include params
22. extra vars (always win precedence) 命令行变量

 

!!! note
	上述描述的是默认规则变量覆盖`hash_behaviour=replace`, 使用`merge` 可以更改为合并。



### 变量范围

您可以根据希望的范围来决定在何处设置变量。Ansible有三个主要的范围 

- 全局：这是由config，环境变量和命令行设置的

- play：每个play和包含的结构，vars条目(vars; vars_files; vars_prompt)，角色默认变量和vars。

- 主机：直接与主机相关联的变量，像inventory, include_vars, facts or registered 

 

### 使用变量

#### 在jinja2中使用

一旦定义了变量，就可以在使用Jinja2模板系统的剧本中使用它们。这是一个简单的Jinja2模板

```jinja2
My amp goes to {{ max_amp_value }}
```

这个表达式提供了最基本的变量替换形式。

您可以在剧本中使用相同的语法。例如

```yaml
template: src=foo.cfg.j2 dest={{ remote_install_path }}/foo.cfg
```

#### 使用Jinja2过滤器转换变量

Jinja2过滤器允许您在模板表达式中转换变量的值。例如，`capitalize`过滤器将传递给它的任何值都大写;`to_yaml`和`to_json`过滤器会更改变量值的格式。



YAML语法要求，如果您以`{{foo}}`开始一个值，则必须 **用引号包裹整行**，因为它希望确保您没有试图启动YAML字典。YAML语法文档对此进行了介绍。

下面这个时错误的写法

```yaml
- hosts: app_servers
  vars:
      app_path: {{ base_path }}/22
```

这样写，才是对的。

```yaml
- hosts: app_servers
  vars:
       app_path: "{{ base_path }}/22"
```

#### 从系统中发现变量:Facts

还有其他地方可以使用变量，但是这些是被发现的变量类型，不是由用户设置的。

`Facts`是通过与远程系统对话而获得的信息。数据存储在`ansible_facts`变量中，你可以通过下列示例来获取变量中的信息

```yaml
- debug: var=ansible_facts
```

或者使用`setup`模块

```bash
ansible hostname -m setup
```

#### 访问复杂变量数据

使用嵌套数据结构访问变量

```jinja2
{{ ansible_facts["eth0"]["ipv4"]["address"] }}
```

或者使用`.`符号

```jinja2
{{ ansible_facts.eth0.ipv4.address }}
```

类似地，这是我们访问数组的第一个元素的方式

```jinja2
{{ foo[0] }}
```

#### 使用内置变量

ansible 提供了许多内置变量，来帮助大家获取当前运行的诸多信息，通过内置变量，我们可以做更多的事情，比如获取主机的自定义fact，获取当前运行的主机等等。

##### 魔术变量

| 变量名称                                   | 说明                                                         | 使用                                                         |
| ------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ansible_check_mode                         | 是否处于检查模式，返回布尔值                                 | `{{ ansible_check_mode }}`                                   |
| ansible_dependent_role_names               | 当前剧本依赖的角色名称                                       | `{{ ansible_dependent_role_names}}`                          |
| ansible_diff_mode                          | 是否处于对比模式，返回布尔值                                 | `{{ ansible_diff_mode }}`                                    |
| ansible_forks                              | 返回最大并行运行的数量                                       | `{{ ansible_forks }}`                                        |
| ansible_inventory_sources                  | 用作主机清单的资源列表                                       | `{{ ansible_inventory_sources }}`                            |
| ansible_limit                              | CLI选项`--limit`的内容                                       | `{{ ansible_limit }}`                                        |
| ansible_loop                               | 通过`loop_control.extended`启用时，包含扩展循环信息的字典/映射 | `{{ ansible_loop }}`                                         |
| ansible_loop_var                           | 提供给`loop_control.loop_var`的值的名称                      | `{{ ansible_loop_var }}`                                     |
| ansible_index_var                          | 提供给`loop_control.index_var`的值的名称                     | `{{ ansible_index_var }}`                                    |
| ansible_parent_role_paths                  | 当通过`include_role`或`import_role`操作执行当前角色时，此变量包含所有父角色的列表，而最新角色（即包含/导入该角色的角色）是列表中的第一项。 | `{{ ansible_parent_role_paths }}`                            |
| ansible_play_hosts<br />ansible_play_batch | 包含当前运行的主机列表，受serial参数影响                     | ``{{ ansible_play_hosts }}`<br />{{ ansible_play_batch }}`   |
| ansible_play_hosts_all                     | 所有执行主机的列表                                           | `{{ ansible_play_hosts_all }}`                               |
| ansible_play_role_names                    | 当前导入到当前剧本中的角色的名称                             | `{{ ansible_play_role_names }}`                              |
| ansible_playbook_python                    | 控制器上Ansible使用的python解释器的路径                      | `{{ ansible_playbook_python }}`                              |
| ansible_role_names                         | 当前导入角色的名称                                           | `{{ ansible_role_names }}`                                   |
| ansible_run_tags                           | `--tags` CLI选项的内容，该选项指定当前运行将包括哪些标签。   | `{{ ansible_run_tags}}`                                      |
| ansible_search_path                        | `action`插件`lookups`的当前搜索路径                          | `{{ ansible_search_path}}`                                   |
| ansible_skip_tags                          | `--skip`标记CLI选项的内容，该选项指定在当前运行中将跳过哪些标记。 | `{{ ansible_skip_tags}}`                                     |
| ansible_verbosity                          | Ansible的详细版本信息                                        | `{{ ansible_verbosity }}`                                    |
| ansible_version                            | ansible版本信息                                              | `{{ ansible_version }}`                                      |
| ansible_playbook_python                    | ansible的python可执行路径                                    | `{{ ansible_playbook_python }}`                              |
| groups_name                                | 当前主机所在组的主机列表                                     | `{% if   'webserver' in group_names %}      # some part of a configuration file that   only applies to webservers   {% endif   %}` |
| groups                                     | 包含设备清单组内的所有主机                                   | `{% for  host in groups[‘db_servers’] %}   {{ host   }}   {% endfor   %}` |
| hostvars                                   | 包含运行的所有变量信息                                       | `{{   hostvars['db.example.com'].ansible_eth0.ipv4.address }}` |
| inventory_hostname                         | 当前运行主机的库存配置名称                                   | `{{ inventory_hostname }}`<br />`{{ hostvars[inventory_hostname] }}` |
| inventory_hostname_short                   | `inventory_hostname`的简短版本                               | `{{ inventory_hostname_short }}`                             |
| inventory_dir                              | 存放主机清单的目录                                           | `{{ inventory_dir }}`                                        |
| inventory_file                             | 主机清单的文件名                                             | `{{ inventory_file }}`                                       |
| omit                                       | 允许您忽略某个选项的特殊变量                                 | `- user: name=bob home={{ bobs_home`                         |
| ansible_play_name                          | 当前正在执行的`play` name                                    | `{{ ansible_play_name }}`                                    |
| playbook_dir                               | playbook的路径                                               | `{{ playbook_dir }}`                                         |
| role_name                                  | 当前正在执行的角色名称。                                     | `{{ role_name }}`                                            |
| role_path                                  | 返回的当前角色路径，只在role中起作用                         | `{{ role_path }}`                                            |

##### Facts 变量

| 变量名称      | 说明                                          | 使用                  |
| ------------- | --------------------------------------------- | --------------------- |
| ansible_facts | 包含所有运行的主机收集数据                    | `{{ ansible_facts }}` |
| ansible_local | `inventory_hostname` 主机自定义的本地fact变量 | `{{ ansible_local }}` |

##### 连接变量

| 变量名称                   | 说明                              | 使用                               |
| -------------------------- | --------------------------------- | ---------------------------------- |
| ansible_become_user        | 权限提升的用户                    | `{{ ansible_become_user }}`        |
| ansible_connection         | 使用的连接插件                    | `{{ ansible_connection }}`         |
| ansible_host               | 当前使用的远端主机的`ip/name`名称 | `{{ ansible_host }}`               |
| ansible_python_interpreter | ansible在远端的python可执行路径   | `{{ ansible_python_interpreter }}` |
| ansible_user               | 使用ansible登录远端的用户         | `{{ ansible_user }}`               |

