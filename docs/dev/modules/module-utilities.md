# 模块工具类

 Ansible提供了许多模块实用类，或代码片段来帮助你在Python中快速构建ansible模块。 这些模块工具类默认存放在`/usr/lib/python2.7/site-packages/ansible/module_utils/` 中，` basic.py `模块类是ansible模块的主要入口，常见的工具类是` AnsibleModule `。



## AnsibleModule

想要使用此功能，使用` from ansible.module_utils.basic import AnsibleModule `命令导入即可。

```python
class ansible.module_utils.basic.AnsibleModule(argument_spec, bypass_checks=False, no_log=False, check_invalid_arguments=None, mutually_exclusive=None, required_together=None, required_one_of=None, add_file_common_args=False, supports_check_mode=False, required_if=None, required_by=None)
```

使用此功能，可以在Python中快速构建ansible模块的通用代码(尽管您可以用任何可以返回JSON的东西来编写模块)。

- `add_path_info`(*kwargs*) 对于文件结果，请在返回路径中添加有关文件路径的统计信息，以补充有关文件的信息。 
- `atomic_move`(*src*, *dest*, *unsafe_writes=False*)  原子性的移动文件
- `backup_local`(*fn*) 对指定文件进行带日期标记的备份，成功或失败时返回True或False
- `boolean`(*arg*) 将参数转换为布尔值
- `digest_from_file`(*filename*, *algorithm*)  返回本地文件的十六进制摘要以获取由名称指定的digest_method；如果文件不存在，则返回None。 
- `exit_json`( *\*\*kwargs* )  以json数据的形式从模块返回
- `fail_json`( *\*\*kwargs* )  以json数据的形式从模块返回，并带有错误信息。
- `get_bin_path`(*arg*, *required=False*, *opt_dirs=None*) 查找系统中的可执行文件的路径。
- `is_executable`(*path*) 判断给定的路径是否可执行
- `is_special_selinux_path`(*path*) 如果给定的路径位于NFS或其他特殊的fs挂载点上，则返回一个包含(True, selinux上下文)的元组，否则返回将为(False, None)。 
- `load_file_common_arguments`(*params*)  封装了file模块的常见选项,以便可以多次利用。
- `md5`(*filename*)  使用`digest_from_file()`返回本地文件的MD5摘要 
- `preserved_copy`(*src*, *dest*) 复制一个文件,保留所有权限
- `run_command`(*args*, *check_rc=False*, *close_fds=True*, *executable=None*, *data=None*, *binary_data=False*, *path_prefix=None*, *cwd=None*, *use_unsafe_shell=False*, *prompt_regex=None*, *environ_update=None*, *umask=None*, *encoding='utf-8'*, *errors='surrogate_or_strict'*, *expand_user_and_vars=True*, *pass_fds=None*, *before_communicate_callback=None*) 执行一个命令,返回rc、stdout和stderr。
- `sha1`(*filename*) 使用`digest_from_file()`返回本地文件的SHA1摘要。
- `sha256`(*filename*) 使用`digest_from_file()`返回本地文件的SHA256摘要。

更多内容见`basic`文件：`/usr/lib/python2.7/site-packages/ansible/module_utils/basic.py`

## Basic

想要使用此功能，使用` import ansible.module_utils.basic `命令导入即可。

-  `ansible.module_utils.basic.AnsibleFallbackNotFound`    异常
- `ansible.module_utils.basic.env_fallback`(*\*args*, *\*\*kwargs*)  从环境中加载值
- `ansible.module_utils.basic.heuristic_log_sanitize`( *data*, *no_log_values=None* ) 从日志消息中删除类似密码的字符串
- `ansible.module_utils.basic.remove_values`( *value*, *no_log_strings*)  从 *value* 中删除 *no_log_strings* 字符串中的字符串 

更多内容见`basic`文件：`/usr/lib/python2.7/site-packages/ansible/module_utils/basic.py`

## module 工具类的命名和查找

通常，您从名称或位置就可以知道模块工具类的功能。

- `lib/ansible/module_utils/urls.py` 包含用于解析URL的共享代码
- `lib/ansible/module_utils/storage/emc/` 包含与EMC相关的共享代码
- `lib/ansible/modules/storage/emc/` 包含与EMC相关的模块

自定义的模块程序遵循此模式，可以很方便的查找和使用。
 

## 其他工具类

- `api.py` - Supports generic API modules
- `basic.py` - General definitions and helper utilities for Ansible modules
- `common/dict_transformations.py` - Helper functions for dictionary transformations
- `common/file.py` - Helper functions for working with files
- `common/text/` - Helper functions for converting and formatting text.
- `common/parameters.py` - Helper functions for dealing with module parameters
- `common/sys_info.py` - Functions for getting distribution and platform information
- `common/validation.py` - Helper functions for validating module parameters against a module argument spec
- `facts/` - Directory of utilities for modules that return facts. See [PR 23012](https://github.com/ansible/ansible/pull/23012) for more information
- `ismount.py` - Single helper function that fixes os.path.ismount
- `json_utils.py` - Utilities for filtering unrelated output around module JSON output, like leading and trailing lines
- `known_hosts.py` - utilities for working with known_hosts file
- `network/common/config.py` - Configuration utility functions for use by networking modules
- `network/common/netconf.py` - Definitions and helper functions for modules that use Netconf transport
- `network/common/parsing.py` - Definitions and helper functions for Network modules
- `network/common/network.py` - Functions for running commands on networking devices
- `network/common/utils.py` - Defines commands and comparison operators and other utilises for use in networking modules
- `powershell/` - Directory of definitions and helper functions for Windows PowerShell modules
- `pycompat24.py` - Exception workaround for Python 2.4
- `service.py` - Utilities to enable modules to work with Linux services (placeholder, not in use)
- `shell.py` - Functions to allow modules to create shells and work with shell commands
- `six/__init__.py` - Bundled copy of the [Six Python library](https://pythonhosted.org/six/) to aid in writing code compatible with both Python 2 and Python 3
- `splitter.py` - String splitting and manipulation utilities for working with Jinja2 templates
- `urls.py` - Utilities for working with http and https requests