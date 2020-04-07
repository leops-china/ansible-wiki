# yaml语法

YAML 语言（发音 /ˈjæməl/ ）的设计目标，就是方便人类读写。它实质上是一种通用的数据串行化格式。



它的基本语法规则如下。

- 大小写敏感
- 使用缩进表示层级关系
- 缩进时不允许使用Tab键，只允许使用空格。
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- yaml文件以"---"作为文档的开始，"..."作为文档的结束

- \# 表示注释，从这个字符一直到行尾，都会被解析器忽略。
- 相同缩进级别的行以“- ”（破折号和空格）开头的组成一个列表。

```yaml
---
# A list of tasty fruits
- Apple
- Orange
- Strawberry
- Mango
...
```



YAML 支持的数据结构有三种。

- 数组：一组按次序排列的值，又称为序列（sequence） /      列表（list）
- 对象：键值对的集合，又称为映射（mapping）/ 哈希（hashes） / 字典（dictionary）
- 纯量（scalars）：单个的、不可再分的值

 

## 数组

相同缩进级别的行以“- ”（破折号和空格）开头的组成一个列表。

```yaml
---

fruits:
    - Apple
    - Orange
    - Strawberry
    - Mango
```



## 对象

对象的一组键值对，使用冒号结构表示(冒号后面要有个空格)。

```yaml
job: Developer

# An employee record
martin:
    name: Martin D'vloper
    job: Developer
    skill: Elite
```

更复杂的数据结构

```yaml
# Employee records
-  martin:
    name: Martin D'vloper
    job: Developer
    skills:
      - python
      - perl
      - pascal
-  tabitha:
    name: Tabitha Bitumen
    job: Developer
    skills:
      - lisp
      - fortran
      - erlang
```

字典和列表也可以使用缩写的形式,即行内表示法

```yaml
---
martin: {name: Martin D'vloper, job: Developer, skill: Elite}
fruits: ['Apple', 'Orange', 'Strawberry', 'Mango']
```

 

## 纯量

### 数值

```yaml
number: 12

float:12.30
```

### 布尔值

表示true的值

true, True, TRUE, yes, Yes, YES, on, On, ON, y, Y

表示false的值

false, False, FALSE, no, No, NO, off, Off, OFF, n, N

```yaml
create_key: yes
needs_agent: no
knows_oop: True
likes_emacs: TRUE
uses_cvs: false
```



### 强制类型转换

YAML 允许使用两个感叹号，强制转换数据类型。

```yaml
e: !!str 123

f: !!str true
```

 

### 字符串

字符串默认不使用引号表示。

```yaml
str: 这是一行字符串
```



如果字符串之中包含空格或特殊字符，需要放在引号之中。

```yaml
s1: '内容\n字符串'

s2: "内容\n字符串"
```

> 单引号和双引号都可以使用，双引号不会对特殊字符转义。

 

Ansible对变量使用`{{var}}`,需要使用双引号包裹

```yaml
foo: "{{ variable }}"
foo: "{{ variable }}/additional/string/literal"
```

 

单引号之中如果还有单引号，必须连续使用两个单引号转义。

```yaml
str: 'labor''s day' 
```



字符串可以写成多行，从第二行开始，必须有一个单空格缩进。换行符会被转为空格。

```yaml
str: 这是一段
  多行
  字符串
```

 

多行字符串可以使用`|`保留换行符，也可以使用`>`折叠换行。

```yaml
this: |
  Foo
  Bar

that: >
  Foo
  Bar
```

 

`+`表示保留文字块末尾的换行，`-`表示删除字符串末尾的换行。

```yaml
s1: |
  Foo


s2: |+
  Foo


s3: |-
  Foo

```



字符串之中可以插入 HTML 标记。

```yaml
message: |
  <p style="color: red">
  段落
  </p>
```



 ## 引用

锚点`&`和别名`*`，可以用来引用，以便于数据可以重复利用，从而精简声明

```yaml
defaults: &defaults   # 锚点
  adapter: postgres
  host: localhost
  
development:
  database: myapp_development
  <<: *defaults    # 引用
  
test:
  database: myapp_test
  <<: *defaults
```

>  &用来建立锚点（defaults），<<表示合并到当前数据，*用来引用锚点。
>

等同于下面的代码。

```yaml
defaults:
  adapter:  postgres
  host:     localhost
  
development:
  database: myapp_development
  adapter:  postgres
  host:     localhost

test:
  database: myapp_test
  adapter:  postgres
  host:     localhost
```

下面是另一个例子。

```yaml
- &showell Steve 
- Clark 
- Brian 
- Oren 
- *showell 
```

等同于

```yaml
- Steve
- Clark 
- Brian 
- Oren 
- Steve
```

## 参考

Playbooks 采用YMAL 语法结构，基本的YMAL 语法请参考

http://docs.ansible.com/YAMLSyntax.html

 

python利用pyyaml模块进行解析yaml语言

http://pyyaml.org/wiki/PyYAMLDocumentation

 

yaml格式在线检查

http://yaml-online-parser.appspot.com/