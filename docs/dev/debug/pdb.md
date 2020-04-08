# pdb本地调试


Ansible是用Python编写的，用于调试本地代码执行的工具是Python调试器 **`pdb`** 。这个工具允许我们在Ansys中插入断点代码和交互式地逐行执行代码。


## 调试 ansible 代码


找到ansible的运行文件

```bash
[root@master ~]# whereis ansible
ansible: /usr/bin/ansible /etc/ansible /usr/share/man/man1/ansible.1.gz
```

在`/usr/bin/ansible`文件开始处加入

```vim hl_lines="3"
57 if __name__ == '__main__':
58 
59     import pdb; pdb.set_trace()
60     display = LastResort()
61     
62     try:  # bad ANSIBLE_CONFIG or config options can force ugly stacktrace
63         import ansible.constants as C
64         from ansible.utils.display import Display
65     except AnsibleOptionsError as e:
66         display.error(to_text(e), wrap_text=False)
67         sys.exit(5)
```

然后运行ansible命令，就进入了pdb调试状态

```bash
# ansible localhost -m ping
> /usr/bin/ansible(60)<module>()
-> display = LastResort()
(Pdb) 
```


## pdb常用命令

输入 help 查看帮助信息

```bash
(Pdb) help

Documented commands (type help <topic>):
========================================
EOF    bt         cont      enable  jump  pp       run      unt   
a      c          continue  exit    l     q        s        until 
alias  cl         d         h       list  quit     step     up    
args   clear      debug     help    n     r        tbreak   w     
b      commands   disable   ignore  next  restart  u        whatis
break  condition  down      j       p     return   unalias  where 

Miscellaneous help topics:
==========================
exec  pdb

Undocumented commands:
======================
retval  rv

```


输入`n(next)`，让程序运行下一行，如果当前语句有一个函数调用，用n是不会进入被调用的函数体中的 

```bash
(Pdb) n
> /usr/bin/ansible(62)<module>()
-> try:  # bad ANSIBLE_CONFIG or config options can force ugly stacktrace
(Pdb) 

```


输入`l(list)`，查看代码片段

```bash
(Pdb) l
 57  	if __name__ == '__main__':
 58  	
 59  	    import pdb; pdb.set_trace()
 60  	    display = LastResort()
 61  	
 62  ->	    try:  # bad ANSIBLE_CONFIG or config options can force ugly stacktrace
 63  	        import ansible.constants as C
 64  	        from ansible.utils.display import Display
 65  	    except AnsibleOptionsError as e:
 66  	        display.error(to_text(e), wrap_text=False)
 67  	        sys.exit(5)
(Pdb) 

```

输入`p(pp)` 查看变量的值

```bash
(Pdb) pp display
<__main__.LastResort object at 0xbe3410>
(Pdb) p display
<__main__.LastResort object at 0xbe3410>
(Pdb) 

```

输入`s(step into)` 跟`n`相似，但是如果当前有一个函数调用，那么`s`会进入被调用的函数体中 

```bash
(Pdb) s
> /usr/bin/ansible(63)<module>()
-> import ansible.constants as C
(Pdb) 

```


输入`r(return)` 执行代码直到从当前函数返回
```bash
(Pdb) r
--Call--
> /usr/lib/python2.7/site-packages/ansible/module_utils/six/__init__.py(193)find_module()
-> def find_module(self, fullname, path=None):
(Pdb) 

```

输入`b` 设置断点，例如 "b 78"，就是在当前脚本的78行打上断点，还能输入函数名作为参数，断点就打到具体的函数入口，如果只敲b，会显示现有的全部断点 

```bash
(Pdb) b 194
Breakpoint 1 at /usr/lib/python2.7/site-packages/ansible/module_utils/six/__init__.py:194
(Pdb) b
Num Type         Disp Enb   Where
1   breakpoint   keep yes   at /usr/lib/python2.7/site-packages/ansible/module_utils/six/__init__.py:194
(Pdb) 

```


输入`a(rgs)`，打印当前函数的参数 

```bash
(Pdb) a
self = <ansible.module_utils.six._SixMetaPathImporter object at 0xb016d0>
fullname = ansible.constants
path = ['/usr/lib/python2.7/site-packages/ansible']
(Pdb) 

```

输入`bt(w)` 打印堆栈跟踪，最下面的帧位于底部。箭头表示"当前帧"，它决定了大多数命令的上下文。

```bash
(Pdb) bt
  /usr/bin/ansible(63)<module>()
-> import ansible.constants as C
> /usr/lib/python2.7/site-packages/ansible/module_utils/six/__init__.py(193)find_module()
-> def find_module(self, fullname, path=None):
(Pdb) 

```

输入`c (continue)` 停止 debug 继续执行程序,直到下一个断点。

```bash
(Pdb) c
> /usr/lib/python2.7/site-packages/ansible/module_utils/six/__init__.py(194)find_module()
-> if fullname in self.known_modules:
(Pdb) 

```

输入`q(uit)`，退出调试


> 有时候我们只是想调试某一部分代码，如果从命令入口开始调试则很难找到相应的代码，这样就需要在某一模块的入口上添加调试点就可以了。


## 调试 Playbook 代码

`Playbook`负责加载，解析，执行yml文件的playbook。

palybook的主要入口在`playbook/__init__.py`文件的Playbook类，这个文件在linux下通常存在`/usr/lib/python2.7/site-packages/ansible/playbook/__init__.py`.

下面是在__init__()方法中添加了断点
```vim hl_lines="4"
 38 class Playbook:
 39 
 40     def __init__(self, loader):
 41         import pdb; pdb.set_trace()
 42         # Entries in the datastructure of a playbook may
 43         # be either a play or an include statement
 44         self._entries = []
 45         self._basedir = to_text(os.getcwd(), errors='surrogate_or_strict')
 46         self._loader = loader
 47         self._file_name = None

```
运行命令

```bash
# ansible-playbook debuger.yaml 
> /usr/lib/python2.7/site-packages/ansible/playbook/__init__.py(44)__init__()
-> self._entries = []
(Pdb) l
 39  	
 40  	    def __init__(self, loader):
 41  	        import pdb; pdb.set_trace()
 42  	        # Entries in the datastructure of a playbook may
 43  	        # be either a play or an include statement
 44  ->	        self._entries = []
 45  	        self._basedir = to_text(os.getcwd(), errors='surrogate_or_strict')
 46  	        self._loader = loader
 47  	        self._file_name = None
 48  	
 49  	    @staticmethod
(Pdb) 
```

## 调试  Inventory 代码

`inventory`负责发现，解析，加载主机清单。

`inventory`的主要入口在`inventory/manager.py`文件中的InventoryManager类，这个文件在linux下通常存在`/usr/lib/python2.7/site-packages/ansible/inventory/manager.py`，如果不知道自己的ansible路径在哪里，可以使用`python -c "import ansible; print(ansible)"`命令查看。
下面是在__init__()方法中添加了断点

```vim
136 class InventoryManager(object):
137     ''' Creates and manages inventory '''
138 
139     def __init__(self, loader, sources=None):
140         import pdb; pdb.set_trace()
141 
142         # base objects
143         self._loader = loader
144         self._inventory = InventoryData()

```
执行命令
```bash
# ansible localhost -m ping
> /usr/lib/python2.7/site-packages/ansible/inventory/manager.py(143)__init__()
-> self._loader = loader
(Pdb) l
138  	
139  	    def __init__(self, loader, sources=None):
140  	        import pdb; pdb.set_trace()
141  	
142  	        # base objects
143  ->	        self._loader = loader
144  	        self._inventory = InventoryData()
145  	
146  	        # a list of host(names) to contain current inquiries to
147  	        self._restriction = None
148  	        self._subset = None
(Pdb) 

```

## 调试 Plugins 代码

plugins 相关的代码是在控制节点中执行的，可以使用本地调试。下列以`callback/default` 插件代码为测试

文件`/usr/lib/python2.7/site-packages/ansible/plugins/callback/default.py`

```vim hl_lines="14"
 63 class CallbackModule(CallbackBase):
 64 
 65     '''
 66     This is the default callback interface, which simply prints messages
 67     to stdout when new callback events are received.
 68     '''
 69 
 70     CALLBACK_VERSION = 2.0
 71     CALLBACK_TYPE = 'stdout'
 72     CALLBACK_NAME = 'default'
 73 
 74     def __init__(self):
 75 
 76         import pdb; pdb.set_trace()
```

可以更进一步的调试callback回调接口
```vim hl_lines="3"
 95     def v2_runner_on_failed(self, result, ignore_errors=False):
 96 
 97         import pdb; pdb.set_trace()
 98         delegated_vars = result._result.get('_ansible_delegated_vars', None)
 99         self._clean_results(result._result, result._task.action)
```
```vim hl_lines="2"
122     def v2_runner_on_ok(self, result):
123         import pdb; pdb.set_trace()
124 
125         delegated_vars = result._result.get('_ansible_delegated_vars', None)
126 
127         if isinstance(result._task, TaskInclude):
```

运行命令

```bash
# ansible-playbook debuger.yaml
> /usr/lib/python2.7/site-packages/ansible/plugins/callback/default.py(77)__init__()
-> self._play = None
(Pdb) l
 72  	    CALLBACK_NAME = 'default'
 73  	
 74  	    def __init__(self):
 75  	
 76  	        import pdb; pdb.set_trace()
 77  ->	        self._play = None
 78  	        self._last_task_banner = None
 79  	        self._last_task_name = None
 80  	        self._task_type_cache = {}
 81  	        super(CallbackModule, self).__init__()
 82  	

```

!!! info
	`module` 模块代码是在远端执行的，所以不能使用pdb本地调试


