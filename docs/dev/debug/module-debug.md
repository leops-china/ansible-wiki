# 模块调试

## 本地调试

使用官方提供的脚本在本地运行模块。

```bash
wget https://raw.githubusercontent.com/ansible/ansible/devel/hacking/test-module.py
```

使下列命令运行module
```bash
# python test-module.py -m /usr/lib/python2.7/site-packages/ansible/modules/system/ping.py
* including generated source, if any, saving to: /root/.ansible_module_generated
* ansiballz module detected; extracted module source to: /root/debug_dir
***********************************
RAW OUTPUT

{"invocation": {"module_args": {"data": "pong"}}, "ping": "pong"}


***********************************
PARSED OUTPUT
{
    "invocation": {
        "module_args": {
            "data": "pong"
        }
    }, 
    "ping": "pong"
}

# python test-module.py -m /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py -a "/bin/sleep 3"
* including generated source, if any, saving to: /root/.ansible_module_generated
* ansiballz module detected; extracted module source to: /root/debug_dir
***********************************
RAW OUTPUT

{"changed": true, "end": "2020-04-08 23:48:57.125895", "stdout": "", "cmd": ["/bin/sleep", "3"], "rc": 0, "start": "2020-04-08 23:48:54.048553", "stderr": "", "delta": "0:00:03.077342", "invocation": {"module_args": {"creates": null, "executable": null, "_uses_shell": false, "strip_empty_ends": true, "_raw_params": "/bin/sleep 3", "removes": null, "argv": null, "warn": true, "chdir": null, "stdin_add_newline": true, "stdin": null}}}


***********************************
PARSED OUTPUT
{
    "changed": true, 
    "cmd": [
        "/bin/sleep", 
        "3"
    ], 
    "delta": "0:00:03.077342", 
    "end": "2020-04-08 23:48:57.125895", 
    "invocation": {
        "module_args": {
            "_raw_params": "/bin/sleep 3", 
            "_uses_shell": false, 
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
    "rc": 0, 
    "start": "2020-04-08 23:48:54.048553", 
    "stderr": "", 
    "stdout": ""
}

```

`test-module.py` 使用参数
```bash
# python test-module.py --help
Usage: test-module.py -[options] (-h for help)

Options:
  -h, --help            show this help message and exit
  -m MODULE_PATH, --module-path=MODULE_PATH
                        REQUIRED: full path of module source to execute
  -a MODULE_ARGS, --args=MODULE_ARGS
                        module argument string
  -D DEBUGGER, --debugger=DEBUGGER
                        path to python debugger (e.g. /usr/bin/pdb)
  -I INTERPRETER_TYPE=INTERPRETER_PATH, --interpreter=INTERPRETER_TYPE=INTERPRETER_PATH
                        path to interpreter to use for this module (e.g.
                        ansible_python_interpreter=/usr/bin/python)
  -c, --check           run the module in check mode
  -n, --noexecute       do not run the resulting module
  -o FILENAME, --output=FILENAME
                        Filename for resulting module

```


## 远程调试

在前面的介绍中，我们知道 **modules是在远程主机上执行的**，调试模块那就需要在远程主机上执行，ansible默认在执行完modules，会自动清理在远程主机上的临时文件。

使用`ANSIBLE_KEEP_REMOTE_FILES=1`环境变量 ，可以保留ansible在远程主机的执行文件，从而在远程主机上调试模块。

```bash
# ANSIBLE_KEEP_REMOTE_FILES=1 ansible localhost -m ping -a 'data=debugging_session' -vvv
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
```

模块文件是由base64编码的字符串文件，可使用`explode`将字符串转换成可执行的python文件
```bash
# python /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py explode
Module expanded into:
/root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/debug_dir
```

查看debug_dir目录
```bash
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
```

- ansible_module_ping.py 是模块本身的代码。
- args 文件包含一个JSON字符串。 该字符串是一个包含模块参数和其他变量的字典。
- ansible目录包含由ansible_module_ping模块使用的ansible.module_utils的代码文件。

修改了debug_dir文件中的代码之后，需要使用`execute`执行代码

```bash
# python /root/.ansible/tmp/ansible-tmp-1489477306.61-275734926719932/ping.py execute
{"invocation": {"module_args": {"data": "debugging_session"}}, "changed": false, "ping": "debugging_session"}
```
