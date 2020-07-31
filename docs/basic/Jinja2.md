# 12. Jinja2 模板语法

Ansible使用 [Jinja2](https://jinja.palletsprojects.com/) 模板来启用动态表达式和对变量的访问。

!!! note
    Jinja2 是一个 Python 的功能齐全的模板引擎。它有完整的 unicode 支持，一个可选 的集成沙箱执行环境，被广泛使用，以 BSD 许可证授权。
    
    
## jinja2 模版中的一些语法

> 关于 Jinja2 完整的中文说明 请移步：http://docs.jinkan.org/docs/jinja2/

### 变量

可以使用点`.`来访问变量的属性，作为替代，也可以使用下标语法`[] `, 下面2种方式效果是一样的

```jinja2
{{ foo.bar }}

{{ foo['bar'] }}
```

如果变量或属性不存在，会返回一个未定义值。

### 注释

要把模板中一行的部分注释掉，默认使用 `{# ... #} `注释语法。

### 转义

简单的使用单引号进行转义

对于较大的段落，使用raw进行转义
```jinja2
{% raw %}
     <ul>
     {% for item in seq %}
         <li>{{ item }}</li>
     {% endfor %}
     </ul>
 {% endraw %}
```


包含 > 、 < 、 & 或 " 字符的变量，必须要手动转义, 使用`e` 顾虑器可以转义这些。

```
{{ user.username | e }} 
```

### 空白控制

在开始或结束放置一个减号（ `-` ），可以移除块前或块后的空白。

```jinja2 
{% for item in seq -%}
    {{ item }}
{%- endfor %}

{%- if foo -%}...{% endif %}
```

### 控制结构

控制结构指的是所有的那些可以控制程序流的东西 —— 条件（比如 if/elif/ekse ）、 for 循环、以及宏和块之类的东西。控制结构在默认语法中以 {% .. %} 块的形式 出现。

#### For

遍历序列
```jinja2
{% for user in users %}
  <li>{{ user.username|e }}</li>
{% endfor %}
```


迭代字典
```jinja2
{% for key, value in my_dict.iteritems() %}
    <dt>{{ key|e }}</dt>
    <dd>{{ value|e }}</dd>
{% endfor %}
```


循环 10 次迭代之后会终止处理
```jinja2
{% for user in users %}

    {%- if loop.index >= 10 %}{% break %}{% endif %}

{%- endfor %}
```


条件过滤
```jinja2
{% for dir in data_dirs if dir != "/" %}
data_dir = {{ dir }}
{% else %}
# no data dirs found
{% endfor %}

```

在一个 for 循环块中你可以访问这些特殊的变量:

| 变量               | 描述                                               |
| :----------------- | :------------------------------------------------- |
| loop.index         | 当前循环迭代的次数（从 1 开始）                    |
| loop.index0        | 当前循环迭代的次数（从 0 开始）                    |
| loop.revindex      | 到循环结束需要迭代的次数（从 1 开始）              |
| loop.revindex0     | 到循环结束需要迭代的次数（从 0 开始）              |
| loop.first         | 如果是第一次迭代，为 True 。                       |
| loop.last          | 如果是最后一次迭代，为 True 。                     |
| loop.length        | 序列中的项目数。                                   |
| loop.cycle         | 在一串序列间期取值的辅助函数                       |
| loop.depth         | 指示当前渲染在递归循环中的深度。 从1开始           |
| loop.depth0        | 指示当前渲染在递归循环中的深度。 从0开始           |
| loop.previtem      | 循环的上一个迭代中的项目。 在第一次迭代中未定义。  |
| loop.nextitem      | 循环的以下迭代中的项目。 在上一次迭代期间未定义。  |
| loop.changed(*val) | 如果以前使用其他值调用（或根本未调用），则为true。 |

#### if 语句

Jinja 中的 if 语句可比 Python 中的 if 语句。
```jinja2
{% if kenny.sick %}
     Kenny is sick.
 {% elif kenny.dead %}
     You killed Kenny!  You bastard!!!
 {% else %}
     Kenny looks okay --- so far
 {% endif %}
```

#### 过滤器

变量可以通过 过滤器 修改。过滤器与变量用管道符号（ `|` ）分割，并且也 可以用圆括号传递可选参数。多个过滤器可以链式调用，前一个过滤器的输出会被作为 后一个过滤器的输入。

```jinj2
{{ name | striptags | title }} 
```

过滤器段允许你在一块模板数据上应用常规 Jinja2 过滤器。只需要把代码用 filter 节包裹起来:

```jinja2
{% filter upper %}
    This text becomes uppercase
{% endfilter %}
```

#### 赋值

在代码块中，你也可以为变量赋值。在顶层的（块、宏、循环之外）赋值是可导出的，即 可以从别的模板中导入。

赋值使用 set 标签，并且可以为多个变量赋值:


```jinja2
{% set navigation = [('index.html', 'Index'), ('about.html', 'About')] %}

{% set key, value = call_something() %}
```

### 表达式

`{% ... %}`   用于执行诸如 for 循环 或赋值的语句

`{{ ... }}`   把表达式的结果打印到模板上


**if 表达式**

一般的语法是` <do something> if <something is true> else <do something else> `。

```jinja2
{{ '[%s]' % page.title if page.title is defined else 'undefined' }}
```

### 字面量

表达式最简单的形式就是字面量。字面量表示诸如字符串和数值的 Python 对象。下面 的字面量是可用的:

| 值                                       | 说明                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| "Hello World"                            | 双引号或单引号中间的一切都是字符串。无论何时你需要在模板中使用一个字   符串（比如函数调用、过滤器或只是包含或继承一个模板的参数），它们都是 有用的。 |
| 42/42.23                                 | 直接写下数值就可以创建整数和浮点数。如果有小数点，则为浮点数，否则为   整数。记住在 Python 里， 42 和 42.0 是不一样的。 |
| ['list','of','objects']                  | 一对中括号括起来的东西是一个列表。列表用于存储和迭代序列化的数据。 |
| ('tuple','of','values')                  | 元组与列表类似，只是你不能修改元组。如果元组中只有一个项，你需要以逗号   结尾它。元组通常用于表示两个或更多元素的项。更多细节见上面的例子。 |
| {dict':'of','key':'and','value':'pairs'} | Python   中的字典是一种关联键和值的结构。键必须是唯一的，并且键必须只有一个 值。字典在模板中很少使用，罕用于诸如 [xmlattr()](http://docs.jinkan.org/docs/jinja2/templates.html#xmlattr) 过滤器之类。 |
| true/false                               | true 永远是 true ，而   false 始终是 false 。                |

!!! note 提示

​	特殊常量 true 、 false 和 none 实际上是小写的。因为这在过去会导致 混淆，过去 True扩展为一个被认为false 的未定义的变量。所有的这三个 常量也可以被写成首字母大写（ True 、 False 和 None ）。尽管如此， 为了一致性（所有的 Jinja 标识符是小写的），你应该使用小写的版本。

 

### 算术

Jinja 允许你用计算值。这在模板中很少用到，但是为了完整性允许其存在。支持下面的 运算符:

| 运算符 | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| +      | 把两个对象加到一起。通常对象是素质，但是如果两者是字符串或列表，你可以用这   种方式来衔接它们。无论如何这不是首选的连接字符串的方式！连接字符串见 ~ 运算符。 {{ 1 + 1 }} 等于 2 。 |
| -      | 用第一个数减去第二个数。 {{ 3 - 2 }} 等于 1 。               |
| /      | 对两个数做除法。返回值会是一个浮点数。 {{ 1 / 2 }} 等于 {{ 0.5 }} 。 |
| //     | 对两个数做除法，返回整数商。 {{ 20 // 7 }} 等于 2 。         |
| %      | 计算整数除法的余数。 {{ 11 % 7 }} 等于 4 。                  |
| *      | 用右边的数乘左边的操作数。 {{ 2 * 2 }} 会返回 4 。也可以用于重   复一个字符串多次。 {{ ‘=’ * 80 }} 会打印 80 个等号的横条。 |
| **     | 取左操作数的右操作数次幂。 {{ 2**3 }} 会返回 8 。            |

**比较运算符**  

| 运算符 | 说明                               |
| ------ | ---------------------------------- |
| ==     | 比较两个对象是否相等。             |
| !=     | 比较两个对象是否不等。             |
| >      | 如果左边大于右边，返回 true 。     |
| >=     | 如果左边大于等于右边，返回 true 。 |
| <      | 如果左边小于右边，返回 true 。     |
| <=     | 如果左边小于等于右边，返回 true 。 |

**逻辑运算符**

对于 if 语句，在 for 过滤或 if 表达式中，它可以用于联合多个表达式:

| 运算符 | 说明                                             |
| ------ | ------------------------------------------------ |
| and    | 如果左操作数和右操作数同为真，返回   true 。     |
| or     | 如果左操作数和右操作数有一个为真，返回   true 。 |
| not    | 对一个表达式取反（见下）。                       |
| (expr) | 表达式组。                                       |

!!! note 提示
    is 和 in 运算符同样支持使用中缀记法: foo is not bar 和 foo not in bar 而不是 not foo is bar 和 not foo in bar 。所有的 其它表达式需要前缀记法 not (foo and bar) 。

 **其它运算符**

下面的运算符非常有用，但不适用于其它的两个分类:

| 运算符 | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| in     | 运行序列/映射包含检查。如果左操作数包含于右操作数，返回   true 。比如 {{ 1 in[1,2,3] }} 会返回 true 。 |
| is     | 运行一个 [测试](http://docs.jinkan.org/docs/jinja2/templates.html#tests) 。 |
| \|     | 应用一个 [过滤器](http://docs.jinkan.org/docs/jinja2/templates.html#filters) 。 |
| ~      | 把所有的操作数转换为字符串，并且连接它们。 {{ "Hello " ~ name ~ "!" }} 会返回（假设 name 值为 ''John' ） Hello John! 。 |
| ()     | 调用一个可调用量:{{ post.render() }} 。在圆括号中，你可以像在   python   中一样使用位置参数和关键字参数: {{ post.render(user, full=true) }} 。 |
| . / [] | 获取一个对象的属性。                                         |

 

###  Python对象方法

在模板中，也是可以使用python的对象方法

字符串方法

- endswith: 用于判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回True，否则返回False
- startswith: 用于检查字符串是否是以指定子字符串开头，如果是则返回 True，否则返回 False。
- split: 指定分隔符对字符串进行切片，默认为空格
- rsplit: 与split相同，但从字符串的末尾开始切片
- splitlines: 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表
- upper: 返回全部大写的字符串
- lower: 返回全部小写的字符串
- capitalize: 将字符串的第一个字母变成大写,其他字母变小写

 列表方法

- index 返回提供值的第一个索引位置

- count  统计某个元素在列表中出现的次数

**python 版本处理**

在python2中，使用`dict.keys()`, `dict.values()`, `dict.items()` 返回字典的列表形式。但是在python3中，这些方法则返回字典形式

```jinja2
# Only works with Python 2
{{ hosts.keys() }}
# Works with both Python 2 and Python 3
{{ hosts.keys() | list }}
```

在python2中，字典有`iterkeys()`, `itervalues()`, and `iteritems()`方法，但是在python3中这些方法被删除，python3则使用 `dict.keys()`, `dict.values()`,  `dict.items()` 

```jinja2
# Only works with Python 2
{{ hosts.iteritems() }}

# Works with both Python 2 and Python 3
{{ hosts.items() | list }}
```

## 在 ansible 中使用Jinja2

### 获取当前时间

使用 `now()` jinja2 函数可以获取当前的时间

```yaml
ansible localhost -m debug -a "msg={{ now(utc='True',fmt='%H-%m-%d %T') }}"
```

> utc 参数可以开启utc时间， fmt参数为时间的格式化输出。

> `{{ }}` 代表把表达式的结果打印到模板上


### 过滤器

Ansible中的过滤器来自`Jinja2`，用于在模板表达式中转换数据。

过滤器与变量用管道符号 `|` 分割

#### 格式化数据过滤器

更改数据格式，其结果是对应的字符串

```jinj2
{{ some_variable | to_json }} 

{{ some_variable | to_yaml }}
```

对于人类可读得输出

```jinja2
{{ some_variable | to_nice_json }} 

{{ some_variable | to_nice_yaml }}
```

 还可以增加参数( new in 2.2)

```jinja2
{{ some_variable | to_nice_json(indent=2) }}

{{ some_variable | to_nice_yaml(indent=8) }}

{{ some_variable | to_nice_yaml(indent=8, width=1337) }}
```

> indent 指定缩进字符数， width限制行数宽度



从json字符串读取，其结果为json类型

```jinja2
{{ some_variable | from_json }}
```

 从yaml字符串读取，其结果为yaml类型

```jinja2
{{ some_variable | from_yaml }}
```

示例：将json文件内容赋值给变量

```jinja2
tasks:
  - shell: cat /some/path/to/file.json
    register: result

  - set_fact:
      myvar: "{{ result.stdout | from_json }}"
```

使用`from_yaml_all 解析多段yaml字符串

```yaml
tasks:
  - shell: cat /some/path/to/multidoc-file.yaml
    register: result
  - debug:
      msg: '{{ item }}'
    loop: '{{ result.stdout | from_yaml_all | list }}'
```



#### 强制定义变量

如果变量未定义，则来自 **ansible** 和 **ansible.cfg** 的默认行为为失败，但您可以将其关闭。

```jinja2
{{ variable | mandatory }}
```

 

#### 未定义的变量默认值

```jinja2
{{ result.cmd|default(5) }}

{{ lookup('env', 'MY_USER') | default('admin', true) }}

{{ lookup('env', 'MY_USER') | default('admin', false) }}
```

如果变量未定义，则将默认值赋值给变量，如果希望变量值为空的时候也赋值，需将 **default** 第二个值为`true`



#### 省略参数

```yaml
- name: touch files with an optional mode
  file:
    dest: "{{ item.path }}"
    state: touch
    mode: "{{ item.mode | default(omit) }}"
  loop:
    - path: /tmp/foo
    - path: /tmp/bar
    - path: /tmp/baz
      mode: "0444"
```

对于列表中的前两个文件，默认mode将由系统的umask确定，因为 `mode=parameter` 不会发送到文件模块，而最后得文件将接收`mode=0444`选项。

 

#### 列表过滤

取最小的值
```jinja2
{{ list1 | min }}
```


取最大的值
```jinja2
{{ [3, 4, 2] | max }}
```


展平列表
```jinja2
{{ [3, [4, 2] ] | flatten }}

{{ [3, [4, [2]] ] | flatten(levels=1) }}  # 展平第一级
```

#### 数据集过滤

对列表唯一过滤
```jinja2
{{ list1 | unique }}
```


对两个列表去重合并
```jinja2
{{ list1 | union(list2) }}
```


对两个列表做交集
```jinja2
{{ list1 | intersect(list2) }}
```


找到两个列表差异部分(在list1 不在list2 的差异)
```jinja2
{{ list1 | difference(list2) }}
```


找到两个列表都互相不在对方列表的部分
```jinja2
{{ list1 | symmetric_difference(list2) }}
```

#### 字典过滤

将字典变为列表

```jinja2
{{ dict | dict2items }}
```

返回的列表

```yaml
- key: Application
  value: payment
- key: Environment
  value: dev
```

可指定列表`key/vaule`的名字

```jinja2
{{ files | dict2items(key_name='file', value_name='path') }}
```

将列表转换为字典

```jinja2
{{ tags | items2dict }}
```

返回的字典

```yaml
Application: payment
Environment: dev
```

可指定列表`key/vaule`的名字

```jinja2
{{ tags | items2dict(key_name='key', value_name='value') }}
```

#### zip 过滤

使用 `zip` 来合并其他列表

```yaml
- name: give me list combo of two lists
  debug:
   msg: "{{ [1,2,3,4,5] | zip(['a','b','c','d','e','f']) | list }}"

- name: give me shortest combo of two lists
  debug:
    msg: "{{ [1,2,3] | zip(['a','b','c','d','e','f']) | list }}"
```

使用 `zip_longest` 以元素最多为合并对象

```yaml
- name: give me longest combo of three lists , fill with X
  debug:
    msg: "{{ [1,2,3] | zip_longest(['a','b','c','d','e','f'], [21, 22, 23], fillvalue='X') | list }}"
```

zip 也可以用于构造字典

```jinja2
{{ dict(keys_list | zip(values_list)) }}
```

变量

```yaml
keys_list:
  - one
  - two
values_list:
  - apple
  - orange
```

转换后

```yaml
one: apple
two: orange
```

#### 子元素过滤器

使用`subelements` 过滤对象的子元素

```jinja2
{{ users | subelements('groups', skip_missing=True) }}
```

变量

```yaml
users:
- name: alice
  authorized:
  - /tmp/alice/onekey.pub
  - /tmp/alice/twokey.pub
  groups:
  - wheel
  - docker
- name: bob
  authorized:
  - /tmp/bob/id_rsa.pub
  groups:
  - docker
```

转换后

```yaml
-
  - name: alice
    groups:
    - wheel
    - docker
    authorized:
    - /tmp/alice/onekey.pub
    - /tmp/alice/twokey.pub
  - wheel
-
  - name: alice
    groups:
    - wheel
    - docker
    authorized:
    - /tmp/alice/onekey.pub
    - /tmp/alice/twokey.pub
  - docker
-
  - name: bob
    authorized:
    - /tmp/bob/id_rsa.pub
    groups:
    - docker
  - docker
```

一个在循环中使用的例子

```yaml
- name: Set authorized ssh key, extracting just that data from 'users'
  authorized_key:
    user: "{{ item.0.name }}"
    key: "{{ lookup('file', item.1) }}"
  loop: "{{ users | subelements('authorized') }}"
```



#### 随机Mac地址过滤器

从一个以`52:54:00`开头的字符串前缀中获取一个随机的MAC地址

```jinja2
"{{ '52:54:00' | random_mac }}"
# => '52:54:00:ef:1c:03'
```

使用因子，创建随机但幂等的MAC地址

```jinja2
"{{ '52:54:00' | random_mac(seed=inventory_hostname) }}"
```



#### 随机数过滤

从列表中随机获取元素
```jinja2
{{ ['a','b','c','d','e','f']|random }}
```


从0-59 的整数中随机获取一个数
```jinja2
{{ 59 | random}}
```


从0-100 中随机获取能被10 整除的数（可以理解为0 10 20 30 40 50 ...100 的随机数）
```jinja2
{{ 100 |random(step=10) }}
```

从0-100 中随机获取1 开始步长为10 的数（可以理解为1 11 21 31 41...91 的随机数）
```jinja2
{{ 100 |random(1, 10) }}

{{ 100 |random(start=1, step=10) }}
```

使用因子创建随机数

```jinj2
"{{ 60 | random(seed=inventory_hostname) }} * * * * root /script/from/cron"
```



#### 随机列表过滤

给已存在的列表随机排序
```jinja2
{{ ['a','b','c']|shuffle }} => ['c','a','b']

{{ ['a','b','c']|shuffle }} => ['b','c','a']
```

使用因子生成随机列表

```jinj2
{{ ['a','b','c'] | shuffle(seed=inventory_hostname) }}
# => ['b','a','c']
```



#### 数学

获取对数, 默认`e`
```jinja2
{{ myvar | log }}

{{ myvar | log(10) }}
```


获取n次幂
```jinja2
{{ myvar | pow(2) }}

{{ myvar | pow(5) }}
```


获取平方根
```jinja2
{{ myvar | root }}

{{ myvar | root(5) }}
```



#### JSON查询过滤

> 该过滤器基于jmespath构建 更多的示例 [jmespath examples](http://jmespath.org/examples.html).

json过滤器，可以对复杂的json数据体提取一部分数据。



json结构体


```json
{
    "domain_definition": {
        "domain": {
            "cluster": [
                {
                    "name": "cluster1"
                },
                {
                    "name": "cluster2"
                }
            ],
            "server": [
                {
                    "name": "server11",
                    "cluster": "cluster1",
                    "port": "8080"
                },
                {
                    "name": "server12",
                    "cluster": "cluster1",
                    "port": "8090"
                }
            ],
            "library": [
                {
                    "name": "lib1",
                    "target": "cluster1"
                },
                {
                    "name": "lib2",
                    "target": "cluster2"
                }
            ]
        }
    }
}
```

要从这个结构中提取所有`cluster`，可以使用以下查询

```yaml
- name: "Display all cluster names"
  debug:
    var: item
  loop: "{{ domain_definition | json_query('domain.cluster[*].name') }}"
```

提取所有`server` 的 `name`

```yaml
- name: "Display all server names"
  debug:
    var: item
  loop: "{{ domain_definition | json_query('domain.server[*].name') }}"
```

提取 `cluster1` 的 `port`

```yaml
- name: "Display all ports from cluster1"
  debug:
    var: item
  loop: "{{ domain_definition | json_query(server_name_cluster1_query) }}"
  vars:
    server_name_cluster1_query: "domain.server[?cluster=='cluster1'].port"
```

使用字符串来连接端口

```yaml
- name: "Display all ports from cluster1 as a string"
  debug:
    msg: "{{ domain_definition | json_query('domain.server[?cluster==`cluster1`].port') | join(', ') }}"
```

> 这里使用反引号来避免转义

可以使用单引号转义

```yaml
- name: "Display all ports from cluster1"
  debug:
    var: item
  loop: "{{ domain_definition | json_query('domain.server[?cluster==''cluster1''].port') }}"
```



#### ip地址过滤

测试字符串是有效的ip地址不

```jinja2
{{ myvar | ipaddr }}
```


字符串转ip协议地址

```jinja2
{{ myvar | ipv4 }}

{{ myvar | ipv6 }}
```


从cidr中获取地址信息

```jinja2
{{ '192.0.2.1/24' | ipaddr('address') }}
```



#### Network CLI 过滤器

使用`parse_cli`过滤器将网络设备CLI命令的输出转换为JSON输出

```jinja2
{{ output | parse_cli('path/to/spec') }}
```



还支持使用TextFSM库解析CLI命令的输出

```jinja2
{{ output | parse_cli_textfsm('path/to/fsm') }}
```



#### Network XML 过滤器

使用`parse_xml`过滤器将网络设备CLI命令的输出转换为XML输出

```jinja2
{{ output | parse_xml('path/to/spec') }}
```



#### Network VLAN 过滤器

```jinja2
{{ [3003, 3004, 3005, 100, 1688, 3002, 3999] | vlan_parser }}
```

输出

```jinj2
['100,1688,3002-3005,3999']
```

另一个jinja2模板例子

```jinja2
{% set parsed_vlans = vlans | vlan_parser %}
switchport trunk allowed vlan {{ parsed_vlans[0] }}
{% for i in range (1, parsed_vlans | count) %}
switchport trunk allowed vlan add {{ parsed_vlans[i] }}
```


#### 哈希过滤器

获取字符串得hash值
```jinja2
{{ 'test1'|hash('sha1') }}

{{ 'test1'|hash('md5') }}
```


获取字符串校验和
```jinja2
{{ 'test2'|checksum }}
```


获取sha512密码哈希
```jinja2
{{ 'passwordsaresecret'|password_hash('sha512') }}

{{ 'secretpassword'|password_hash('sha256', 'mysecretsalt') }}
```

#### 合并散列


```jinja2
{{ {'a':1, 'b':2}|combine({'b':3}) }}
```
结果
```
{'a':1, 'b':3}
```


支持递归合并
```jinja2
{{ {'a':{'foo':1, 'bar':2}, 'b':2}|combine({'a':{'bar':3, 'baz':4}}, recursive=True) }}
```


结果
```jinja2
{'a':{'foo':1, 'bar':3, 'baz':4}, 'b':2}
```



#### 提取过滤器

使用 `map`  `extract`筛选器将索引列表映射到容器中的值作为列表返回


```jinja2
{{ [0,2]|map('extract', ['x','y','z'] )| list }}

# ['x', 'z']
```

```jinja2
{{ ['x','y']|map('extract', {'x': 42, 'y': 31})|list }}

# [42, 31]
```

```jinja2
{{ groups['x']|map('extract', hostvars, 'ec2_ip_address')|list }}
```

这需要组'x'中的主机列表，在主机中查找主机，然后查找结果的ec2_ip_address。 最后的结果是组'x'中的主机的IP地址列表。
```jinja2
{{ groups['test'] | map('extract', hostvars, 'ansible_default_ipv4.address')|list }}
```


过滤器的第三个参数也可以是一个列表，用于容器内的递归查找：

```jinja2
{{ ['a']|map('extract', b, ['x','y'])|list }}

#  b['a']['x']['y']
```

map中也可以使用其他过滤器

```jinja2
# 更改列表中的文件目录
{{ ['/test/t.gz'] | map('basename')| map('regex_replace', '(.*)', '/tmp/\\1') | list )}}
```


#### 注释过滤

`comment` 过滤器允许用选择的注释样式装饰文本。

```jinja2
{{ "Plain style (default)" | comment }}
```
输出
```
#
# Plain style (default)
#
```



**指定特定的注释字符**

```yaml
{{ "My Special Case" | comment(decoration="! ") }}
```

输出

```
!
! My Special Case
!
```

**输出各种语言的注释风格**

```jinja2
{{ "C style" | comment('c') }}
{{ "C block style" | comment('cblock') }}
{{ "Erlang style" | comment('erlang') }}
{{ "XML style" | comment('xml') }}
```


还可以自定义
```jinja2
{{ "Custom style" | comment('plain', prefix='#######\n#', postfix='#\n#######\n   ###\n    #') }}
```

输出

```
#######
#
# Custom style
#
#######
   ###
    #
```



#### url 分割过滤器

使用 `urlsplit` 过滤器从url字符串中取其中的一个片段

```jinja2
{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('hostname') }}
# => 'www.acme.com'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('netloc') }}
# => 'user:password@www.acme.com:9000'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('username') }}
# => 'user'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('password') }}
# => 'password'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('path') }}
# => '/dir/index.html'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('port') }}
# => '9000'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('scheme') }}
# => 'http'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('query') }}
# => 'query=term'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit('fragment') }}
# => 'fragment'

{{ "http://user:password@www.acme.com:9000/dir/index.html?query=term#fragment" | urlsplit }}
# =>
#   {
#       "fragment": "fragment",
#       "hostname": "www.acme.com",
#       "netloc": "user:password@www.acme.com:9000",
#       "password": "password",
#       "path": "/dir/index.html",
#       "port": 9000,
#       "query": "query=term",
#       "scheme": "http",
#       "username": "user"
#   }
```



#### 正则匹配

```jinja2
# search for "foo" in "foobar"
{{ 'foobar' | regex_search('(foo)') }}

# will return empty if it cannot find a match
{{ 'ansible' | regex_search('(foobar)') }}

# case insensitive search in multiline mode
{{ 'foo\nBAR' | regex_search("^bar", multiline=True, ignorecase=True) }}
```

搜索所有匹配的regex

```jinja2
# Return a list of all IPv4 addresses in the string
{{ 'Some DNS servers are 8.8.8.8 and 8.8.4.4' | regex_findall('\\b(?:[0-9]{1,3}\\.){3}[0-9]{1,3}\\b') }}
```

正则替换

```jinja2
# convert "ansible" to "able"
{{ 'ansible' | regex_replace('^a.*i(.*)$', 'a\\1') }}

# convert "foobar" to "bar"
{{ 'foobar' | regex_replace('^f.*o(.*)$', '\\1') }}

# convert "localhost:80" to "localhost, 80" using named groups
{{ 'localhost:80' | regex_replace('^(?P<host>.+):(?P<port>\\d+)$', '\\g<host>, \\g<port>') }}

# convert "localhost:80" to "localhost"
{{ 'localhost:80' | regex_replace(':80') }}
```

转义特殊字符

```jinja
# convert '^f.*o(.*)$' to '\^f\.\*o\(\.\*\)\$'
{{ '^f.*o(.*)$' | regex_escape() }}

# convert '^f.*o(.*)$' to '\^f\.\*o(\.\*)\$'
{{ '^f.*o(.*)$' | regex_escape('posix_basic') }}
```



#### Kubernetes 过滤器

使用`k8s_config_resource_name`过滤器来获取Kubernetes ConfigMap或Secret的名称

```jinja2
{{ configmap_resource_definition | k8s_config_resource_name }}
```



#### 其他的常用过滤

 为shell增加双引号

```yaml
- shell: echo {{ string_value | quote }}
```

根据True，False来返回值

```jinja2
{{ ('name' == 'John') | ternary('Mr','Ms') }}

{{ enabled | ternary('no shutdown', 'shutdown', omit) }} # null 使用第三个值
```

列表转换字符
```jinja2
{{ list | join(" ") }}
```


获取路径的文件名
```jinja2
{{ path | basename }}
```


获取文件的绝对路径
```jinja2
{{ '~/.ssh/id_rsa' | expanduser }}
```


windows平台下获取路径的文件名
```jinja2
{{ path | win_basename }}
```


获取路径中的目录
```jinja2
{{ path | dirname }}
```

展开包含环境变量的路径

```jinja2
{{ path | expandvars }}
```

获取软连接的真实路径

```jinja2
{{ path | realpath }}

{{ path | relpath('/etc') }}  # 指定启点
```


获取文件名的名称和扩展名
```jinja2
{{ path | splitext }}
```


base64编码
```jinja2
{{ encoded | b64decode }}
{{ decoded | string | b64encode }}

{{ encoded | b64decode(encoding='utf-16-le') }}
{{ decoded | string | b64encode(encoding='utf-16-le') }}
```


从字符串创建UUID（1.9版中的新功能）
```jinja2
{{ hostname | to_uuid }}
```


将转换为布尔类型，如"True" 字符串转换为True
```
- debug: msg=test
 when: some_string_value | bool
```


日期
```jinja2
# Get total amount of seconds between two dates. Default date format is %Y-%m-%d %H:%M:%S but you can pass your own format
{{ (("2016-08-14 20:00:12" | to_datetime) - ("2015-12-25" | to_datetime('%Y-%m-%d'))).total_seconds() }}

# Get remaining seconds after delta has been calculated. NOTE: This does NOT convert years, days, hours, etc to seconds. For that, use total_seconds()
{{ (("2016-08-14 20:00:12" | to_datetime) - ("2016-08-14 18:00:00" | to_datetime)).seconds }}
# This expression evaluates to "12" and not "132". Delta is 2 hours, 12 seconds

# get amount of days between two dates. This returns only number of days and discards remaining hours, minutes, and seconds
{{ (("2016-08-14 20:00:12" | to_datetime) - ("2015-12-25" | to_datetime('%Y-%m-%d'))).days }}
```

格式化日期

```jinja2
# Display year-month-day
{{ '%Y-%m-%d' | strftime }}

# Display hour:min:sec
{{ '%H:%M:%S' | strftime }}

# Use ansible_date_time.epoch fact
{{ '%Y-%m-%d %H:%M:%S' | strftime(ansible_date_time.epoch) }}

# Use arbitrary epoch value
{{ '%Y-%m-%d' | strftime(0) }}          # => 1970-01-01
{{ '%Y-%m-%d' | strftime(1441357287) }} # => 2015-09-04
```

查看变量的python类型

```jinja2
{{ myvar | type }}
```



#### 组合过滤器

```yaml
- name: give me largest permutations (order matters)
  debug:
    msg: "{{ [1,2,3,4,5] | permutations | list }}"

- name: give me permutations of sets of three
  debug:
    msg: "{{ [1,2,3,4,5] | permutations(3) | list }}"
    
- name: give me combinations for sets of two
  debug:
    msg: "{{ [1,2,3,4,5] | combinations(2) | list }}"
```



#### Product  过滤器

`product`过滤器返回输入迭代的笛卡尔积。

```yaml
- name: generate multiple hostnames
  debug:
    msg: "{{ ['foo', 'bar'] | product(['com']) | map('join', '.') | join(',') }}"
```

输出

```json
{ "msg": "foo.com,bar.com" }
```



#### debug 过滤器

```jinja2
{{ myvar | type_debug }}
```



#### 字节转换

将数字转换为人类可读的字符串

```yaml
- name: "Human Readable"
  assert:
    that:
      - '"1.00 Bytes" == 1|human_readable'
      - '"1.00 bits" == 1|human_readable(isbits=True)'
      - '"10.00 KB" == 10240|human_readable'
      - '"97.66 MB" == 102400000|human_readable'
      - '"0.10 GB" == 102400000|human_readable(unit="G")'
      - '"0.10 Gb" == 102400000|human_readable(isbits=True, unit="G")'
```

返回

```json
{ "changed": false, "msg": "All assertions passed" }
```



以字节格式返回给定的字符串。

```yaml
- name: "Human to Bytes"
  assert:
    that:
      - "{{'0'|human_to_bytes}}        == 0"
      - "{{'0.1'|human_to_bytes}}      == 0"
      - "{{'0.9'|human_to_bytes}}      == 1"
      - "{{'1'|human_to_bytes}}        == 1"
      - "{{'10.00 KB'|human_to_bytes}} == 10240"
      - "{{  '11 MB'|human_to_bytes}} == 11534336"
      - "{{ '1.1 GB'|human_to_bytes}} == 1181116006"
      - "{{'10.00 Kb'|human_to_bytes(isbits=True)}} == 10240"
```

返回
```json
{ "changed": false, "msg": "All assertions passed" }
```



### 测试



除了过滤器，所谓的“测试”也是可用的。测试可以用于对照普通表达式测试一个变量。 要测试一个变量或表达式，你要在变量后加上一个 is 以及测试的名称。例如，要得出 一个值是否定义过，你可以用 name is defined ，这会根据 name 是否定义返回 true 或 false 。


#### 测试语法

```
variable is test_name
```

例如

```
result is failed
```

测试也可以接受参数。如果测试只接受一个参数，你可以省去括号来分组它们。例如， 下面的两个表达式做同样的事情:


```jinja2
{% if loop.index is divisibleby 3 %}
{% if loop.index is divisibleby(3) %}
```


#### 测试字符串

```
vars:
  url: "http://example.com/users/foo/resources/bar"

tasks:
    - debug:
        msg: "matched pattern 1"
      when: url is match("http://example.com/users/.*/resources/.*")

    - debug:
        msg: "matched pattern 2"
      when: url is search("/users/.*/resources/.*")

    - debug:
        msg: "matched pattern 3"
      when: url is search("/users/")

    - debug:
        msg: "matched pattern 4"
      when: url is regex("example.com/\w+/foo")
```

`match`需要在字符串中完全匹配，而`search`只需要匹配字符串的子集。匹配成功返回`True`，任务则执行。

 

#### 版本比较

检查ansible_distribution_version版本是否大于或等于'12 .04'，条件成立返回True。
```jinja2
{{ ansible_distribution_version is version_compare('12.04', '>=') }}
```


进行严格的版本检查
```jinja2
{{ sample_version_var is version_compare('1.0', operator='lt', strict=True) }}
```
可接受的运算符
```
<, lt, <=, le, >, gt, >=, ge, ==, =, eq, !=, <>, ne
```



#### 包含测试

测试一个列表是否包含另一个列表。

```yaml
vars:
    a: [1,2,3,4,5]
    b: [2,3]
tasks:
    - debug:
        msg: "A includes B"
      when: a is superset(b)

    - debug:
        msg: "B is included in A"
      when: b is subset(a)
```

测试列表是否包含值

```yaml
vars:
  lacp_groups:
    - master: lacp0
      network: 10.65.100.0/24
      gateway: 10.65.100.1
      dns4:
        - 10.65.100.10
        - 10.65.100.11
      interfaces:
        - em1
        - em2

    - master: lacp1
      network: 10.65.120.0/24
      gateway: 10.65.120.1
      dns4:
        - 10.65.100.10
        - 10.65.100.11
      interfaces:
          - em3
          - em4

tasks:
  - debug:
      msg: "{{ (lacp_groups|selectattr('interfaces', 'contains', 'em1')|first).master }}"
```

您可以使用`any ` 和 ` all`来检查列表中的任何元素或所有元素是否为真

```yaml
vars:
  mylist:
      - 1
      - "{{ 3 == 3 }}"
      - True
  myotherlist:
      - False
      - True
tasks:

  - debug:
      msg: "all are true!"
    when: mylist is all

  - debug:
      msg: "at least one is true"
    when: myotherlist is any
```

#### 路径测试

```
- debug:
    msg: "path is a directory"
  when: mypath is directory

- debug:
    msg: "path is a file"
  when: mypath is file

- debug:
    msg: "path is a symlink"
  when: mypath is link

- debug:
    msg: "path already exists"
  when: mypath is exists

- debug:
    msg: "path is {{ (mypath is abs)|ternary('absolute','relative')}}"

- debug:
    msg: "path is the same file as path2"
  when: mypath is same_file(path2)

- debug:
    msg: "path is a mount"
  when: mypath is mount
```

#### 测试命令结果

以下playbook是检查任务状态的测试。

```
tasks:

- shell: /usr/bin/foo
  register: result
  ignore_errors: True

- debug: msg="it failed"
  when: result is failed
  
- debug: msg="it changed"
  when: result is changed

- debug: msg="it succeeded in Ansible >= 2.1"
  when: result is succeeded

- debug: msg="it succeeded"
  when: result is success

- debug: msg="it was skipped"
  when: result is skipped
```

### lookup 插件

`lookup` 插件允许访问外部数据源。

```yaml
# 获取文件内容
vars:
  motd_value: "{{ lookup('file', '/etc/motd') }}"
tasks:
  - debug:
      msg: "motd value is {{ motd_value }}"
```

lookup 更多的插件使用请看 [lookup 插件](/basic/Playbook-features/#lookup)

### if 语句

ad-hoc
```bash
ansible localhost -m debug -a "msg={%- if ansible_play_hosts.index(inventory_hostname) < 3 -%}master{%- else -%}slave{%- endif -%}" 
```

playbook

```yaml
- debug:
      msg: >-
        {%- if ansible_play_hosts.index(inventory_hostname) < 3 -%}
          master
        {%- else -%}
          slave
        {%- endif -%}
```

### for 语句

ad-hoc

```bash
ansible localhost -m debug -a "msg={%- for t in [1,2,3] -%}{{ t }}{%- endfor -%}"
```

playbook

```yaml
- debug:
    msg: |-
      {%- for t in [1,2,3] -%}
        {{ t }}
      {%- endfor -%}
```

### 在 when 里使用 jinja2 表达式

```yaml
- hosts: target_host
  tasks:
  - name: Show debug
    debug: msg='条件满足你就会看到我。'
    when: '{% if def_a_var|d("abc") == "abc" %}{{ foo | d("true") }}{% endif %}'
```