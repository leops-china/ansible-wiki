# 8. 包含和角色

虽然可以在一个非常大的文件中编写 playbook (您可能以这种方式开始学习 palybook)，但最终您将希望重用文件并开始组织工作。在Ansible中，有三种方法可以做到这一点: `includes`, `imports`, and`roles`。

`includes` 和`imports`（在Ansible 2.4版中添加）允许用户将大型playbook拆分成较小的文件，这些文件可以在多个父级playbook中使用，甚至可以在同一Playbook中多次使用。



## 动态和静态

对于可重用的内容，Ansible有两种操作模式: **动态** 和 **静态** 。

在Ansible 2.0中，引入了动态包含的概念。由于以这种方式实现`all include`的一些限制，Ansible 2.1中引入了将`force include`设置为静态的能力。因为`include`任务被重载，包含了静态和动态语法，而且由于`include`的默认行为可能会根据任务上设置的其他选项而更改，所以Ansible 2.4引入了`include`与`import`的概念。



### 静态导入

- 使用`import_tasks`模块来导入`tasks`文件

- 使用`import_role`模块来导入`role`

```yaml
tasks:
  - import_tasks: tasks/foo.yml
  - import_role:
      name: example
```

`import_tasks`还允许 传递变量

```yaml
- import_tasks: wordpress.yml wp_user=timmy

- import_tasks: wordpress.yml
  vars:
    wp_user: timmy
    ssh_keys:
      - keys/one.txt
      - keys/two.txt
```

### 动态包含

- 使用`include_tasks`模块来包含`tasks`文件

- 使用`include_role`模块来包含`role`

 动态包含可以用作循环引用

```yaml
- include_tasks: foo.yml param={{item}}
  with_items: # 循环引用3次
   - 1
   - 2
   - 3
- include_role:
    name: example
```

还可以使用变量引入task文件

```yaml
- include_tasks: "{{inventory_hostname}}.yml"
```

**变量包含**

`include_vars` 在 **task** 中动态加载 **yaml** 或 **json** 文件类型中的变量

 ```yaml
- include_vars: myvars.yml
 ```

根据操作系统类型加载变量文件，如果找不到，则为默认值。

```yaml
- include_vars: "{{ item }}"
  with_first_found:
    - "{{ ansible_distribution }}.yml"
    - "{{ ansible_os_family }}.yml"
    - "default.yml"
```



### 动态与静态两者的区别

- Ansible在Playbook解析时间预处理所有 **静态导入** 。在执行前导入配置文件，出现错误会立即停止
- **动态包含** 是在运行期间遇到该任务时处理的。在执行时导入配置文件，出现错误不会立即停止

当涉及Ansible任务选项时，例如`tags`和条件语句`when`：

- 对于 **动态包含**，任务选项将仅在评估动态任务时应用于该任务，而不会复制到子任务。
- 对于 **静态导入**，父任务选项将被复制到导入中包含的所有子任务。

使用`include*` vs.` import*`有一些优点，也有一些缺点，用户在选择使用它们时应该加以考虑

使用`include*`语句的主要优点是 **循环**。 当 **循环与包含** 一起使用时，将对循环中的 **每个项目执行一次包含的task或role** 。



**与静态导入相比，动态包含的一些限制**

- 您不能使用`notify`来触发来自动态包含的处理程序名称。
- 您不能使用`--start-at-task`在动态包含内的任务开始执行。
- 仅存在于动态包含内的标记不会显示在`-list-tags`输出中。
- 只存在于动态包含内的任务将不会显示在`-list-tasks`输出中。



**与动态包含相比, 静态导入的一些限制**

- 静态导入 **不能用循环**

- 当使用目标文件或角色名称的变量时，不能使用主机清单中的 **变量**
- **handlers** 使用 `import` 导入的处理程序在被其名称通知时不会被触发，因为`import`会用导入的任务列表覆盖 **handler’s**  的指定任务。

 

##  角色ROLE

角色是基于已知文件结构自动加载某些`vars_files`，`tasks`和`handlers`的方法。 按角色分组的内容还允许与其他用户轻松共享角色。

### 角色目录结构

文件结构如下

```bash
webservers.yml
fooservers.yml

group_vars/
   all.yml
   group1.yml
   group2.yml
host_vars/
   hostname1.yml
   hostname2.yml

library/
module_utils/
filter_plugins/

roles/
    common/
        tasks/
        handlers/
        files/
        templates/
        vars/
        defaults/
        meta/
    webservers/
        tasks/
        defaults/
        meta/ 
```

角色必须包含至少一个这样的目录，但是完全可以排除任何没有使用的目录。在使用时，每个目录必须包含一个`main.yml`文件，其中包含相关内容:

- `tasks` - 包含角色要执行的主要任务列表。
- `handlers` - 包含处理程序，可以由此角色使用，甚至可以在此角色以外的任何地方使用。
- `defaults`- 角色的默认变量（有关更多信息，请参阅变量）。
- `vars`- 角色的其他变量（有关更多信息，请参阅变量）。
- `files` - 包含可以通过此角色部署的文件。
- `templates` - 包含可以通过此角色部署的模板。
- `meta` - 为这个角色定义了一些元数据。
- `library`- 如果有任何自定义模块，将其放在这里（可选）
- `filter_plugins` -  如果有任何自定义过滤器插件，将其放在这里（可选）
- `group_var/all` - 如果`group_var/all`存在，其中列出的变量将被添加到所有的主机组中
- `group_var/groupname1` - 如果`group_var/groupname1`存在，其中列出的变量将被添加到groupname1主机组中
- `host_vars/hostname1` - 如果`host_vars/hostname1`存在，其中列出的变量将被添加到hostname1主机组中



除了特定的文件和目录外，也可以包含自定义的文件和目录，比如下面的为每个操作系统设置一个文件

```yaml
# roles/example/tasks/main.yml
- name: added in 2.4, previously you used 'include'
  import_tasks: redhat.yml
  when: ansible_facts['os_family']|lower == 'redhat'
- import_tasks: debian.yml
  when: ansible_facts['os_family']|lower == 'debian'

# roles/example/tasks/redhat.yml
- yum:
    name: "httpd"
    state: present

# roles/example/tasks/debian.yml
- apt:
    name: "apache2"
    state: present
```

### 角色使用

在`play`中使用`roles:` 来定义使用哪些role

```yaml
---
- hosts: webservers
  roles:
    - common
    - webservers
```

这个 playbook 为一个角色 ‘x’ 指定了如下的行为

- 如果 `roles/x/tasks/main.yml` 存在, 其中列出的 tasks 将被添加到 play 中

- 如果 `roles/x/handlers/main.yml` 存在, 其中列出的 handlers 将被添加到 play 中

- 如果 `roles/x/vars/main.yml` 存在, 其中列出的 变量将被添加到 play 中

- 如果  `roles/ x/defaults/main.yml`存在，其中列出的角色默认变量将被添加到play 中

- 如果 `roles/x/meta/main.yml` 存在, 其中列出的 “角色依赖” 将被添加到 roles 列表中

- 所有 `copy` tasks 可以引用 `roles/x/files/` 中的文件，不需要指明文件的全路径。

- 所有 `script` tasks 可以引用 `roles/x/files/ `中的脚本，不需要指明文件的全路径。

- 所有 `template` tasks 可以引用 `roles/x/templates/` 中的文件，不需要指明文件的全路径。

- 所有 `include` tasks 可以引用 `roles/x/tasks/` 中的文件，不需要指明文件的全路径。如果 roles 目录下有文件不存在，这些文件将被忽略。

当以这种方式使用时，playbook 的执行顺序如下:

- `pre_tasks` 定义的所有任务
- 到目前触发的`handlers`任务
- `roles`中列出的每个角色将依次执行。 角色`meta/main.yml`中定义的任何角色依赖关系都将首先运行，但要遵循标签过滤和条件。
- `tasks` 定义的所有任务
- 到目前触发的`handlers`任务
- `post_tasks` 定义的所有任务
- 到目前触发的`handlers`任务



从Ansible 2.4开始，您现在可以使用`import role`或`include role`将角色内联到任何其他任务中

```yaml
---
- hosts: webservers
  tasks:
    - debug:
        msg: "before we run our role"
    - import_role:
        name: example
    - include_role:
        name: example
    - debug:
        msg: "after we ran our role"
```

使用角色可以用简单的名称，也可以使用绝对路径引入

```yaml
- hosts: webservers
  roles:
    - role: '/path/to/my/roles/common'
```

`roles` 也可以接受其他关键字

```yaml
---
- hosts: webservers
  roles:
    - common
    - role: foo_app_instance
      vars:
        dir: '/opt/a'
        app_port: 5000
    - role: foo_app_instance
      vars:
        dir: '/opt/b'
        app_port: 5001
```

也可以换种语法书写

```yaml
---
- hosts: webservers
  tasks:
    - include_role:
        name: foo_app_instance
      vars:
        dir: '/opt/a'
        app_port: 5000
  ...
```

可以有条件的导入role

```yaml
---
- hosts: webservers
  tasks:
    - include_role:
        name: some_role
      when: "ansible_facts['os_family'] == 'RedHat'"
```

也可以为角色内的任务分配标签

```yaml
---
- hosts: webservers
  roles:
    - role: foo
      tags:
        - bar
        - baz
    # using YAML shorthand, this is equivalent to the above:
    - { role: foo, tags: ["bar", "baz"] }
```

换一种语法书写

```yaml
---
- hosts: webservers
  tasks:
    - import_role:
        name: foo
      tags:
        - bar
        - baz
```

如果你想只给这个角色本身打上标记

```yaml
---
- hosts: webservers
  tasks:
    - include_role:
        name: bar
      tags:
        - foo
```

> 本例中的标记不会被添加到include角色中的任务中

### 角色重复执行

 Ansible只允许一个角色执行一次，即使定义了多次，如果角色上定义的参数对于每个定义都是相同的。例如

```yaml
---
- hosts: webservers
  roles:
    - foo
    - foo
```

鉴于以上所述，角色foo将只运行一次。

要使角色多次运行，有两种选择：

- 在每个角色定义中传递不同的参数。

  ```yaml
  ---
  - hosts: webservers
    roles:
      - role: foo
        vars:
          message: "first"
      - { role: foo, vars: { message: "second" } }
  ```

- 在角色的 `meta/main.yml` 文件中添加 `allow_duplicates：true`。

  ```yaml
  # playbook.yml
  ---
  - hosts: webservers
    roles:
      - foo
      - foo
  
  # roles/foo/meta/main.yml
  ---
  allow_duplicates: true
  ```


### 角色默认变量

定义角色默认变量，只需在角色目录中添加一个`defaults/main.yml`文件。角色默认变量优先级最低,很容易被其他变量覆盖掉。

 

### 角色依赖

角色依赖性使您可以在使用角色时 **自动导入** 其他角色。 角色相关性存储在角色目录中包含的`meta/main.yml`文件中，如上所述。 该文件应包含要在指定角色之前插入的角色和参数的列表，例如在`role/myapp/meta/main.yml`示例中的以下内容：

```yaml
---
dependencies:
  - role: common
    vars:
      some_parameter: 3
  - role: apache
    vars:
      apache_port: 80
  - role: postgres
    vars:
      dbname: blarg
      other_parameter: 12
```

> 角色依赖项必须使用经典的角色定义样式。

角色依赖项始终在包含它们的角色之前执行，并且可能是递归的。 依赖性也遵循上面指定的复制规则。 如果另一个角色也将其列为依赖项，则不会根据上述相同规则再次运行它。

> 永远记住，当使用`allow_duplicates：true`时，它必须位于从属角色的`meta/main.yml`中，而不是父角色中。

例如，一个名为car的角色依赖于一个名为wheel的角色，如下所示

```yaml
---
dependencies:
  - role: wheel
    vars:
      n: 1
  - role: wheel
    vars:
      n: 2
  - role: wheel
    vars:
      n: 3
  - role: wheel
    vars:
      n: 4
```

`wheel`角色又依赖两个角色：`tire`和`brake`。 wheel的`meta/main.yml`包含以下内容：

```yaml
---
dependencies:
  - role: tire
  - role: brake
```

`tire`和`brake`的`meta/main.yml`将包含以下内容：

```yaml
---
allow_duplicates: true
```

产生的执行顺序如下：

```yaml
tire(n=1)
brake(n=1)
wheel(n=1)
tire(n=2)
brake(n=2)
wheel(n=2)
...
car
```

> 注意，我们在wheel可以不必使用`allow duplicate: true` ，因为car定义的每个role使用不同的参数值。

### 嵌入模块和插件

如果您编写了自定义模块或插件，您可能希望将其作为角色的一部分进行分享。

除了角色的`tasks`和`handlers`结构之外，还要添加一个名为`library`的目录。在这个库目录中，然后将模块直接包含在其中。

比如下面这样

```yaml
roles/
    my_custom_modules/
        library/
            module1
            module2
```

该自定义的模块在角色本身以及在此角色之后调用的任何角色中都是可用的

```yaml
---
- hosts: webservers
  roles:
    - my_custom_modules
    - some_other_role_using_my_custom_modules
    - yet_another_role_using_my_custom_modules
```

相同的情况，如果开发自定义的插件，需要放在`filter_plugins`目录中，角色就可以使用了

```
roles/
    my_custom_filter/
        filter_plugins
            filter1
            filter2
```

如果说模块和插件需要给多个role使用，那就可以放置在ansible的插件目录中，这样，任何role都可以使用了。

```
/etc/ansible/roles/
    filter_plugins
        filter1
    library/
        module1
    my_custom_filter/
    my_custom_modules/
```

### 角色搜索路径

- 位于playbook目录下的`roles/`目录
- 默认情况下的`/etc/ansible/roles`目录

在Ansible 1.4和更高版本中，您可以配置其他`role_path`来搜索角色。 使用此功能可以将所有常见角色签到一个位置，并在多个剧本项目之间轻松共享它们。 有关如何在`ansible.cfg`中进行设置的详细信息，请参见配置Ansible。

### Ansible Galaxy

Ansible Galaxy是一个免费的网站，可以找到，下载，评级，并审查各种社区开发的Ansible角色，可以是一个伟大的方式来启动你的自动化项目。

可以使用`ansible-galaxy` 初始化一个角色基础目录结构

```bash
# ansible-galaxy init demo
- Role demo was created successfully
# tree demo
demo
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── README.md
├── tasks
│   └── main.yml
├── templates
├── tests
│   ├── inventory
│   └── test.yml
└── vars
    └── main.yml

8 directories, 8 files
```



### 角色示例参考

https://galaxy.ansible.com/

https://github.com/ansible/ansible-examples 

https://github.com/lework/Ansible-roles

https://github.com/geerlingguy

https://github.com/debops