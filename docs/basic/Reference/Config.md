**Ansible** 支持几个源来配置它的行为，包括一个名为`ansible.cfg`的ini文件、环境变量、命令行选项、playbook关键字和变量。

## 配置文件

**Ansible** 配置文件可以存放在不同的位置，但只有一个可用。在下列列表中，ansible从上往下依次检查，检查到哪个可用就用哪个。

- `ANSIBLE_CONFIG` 环境变量，可以定义配置文件的位置
- `./ansible.cfg` 存在于当前工作目录
- `~/.ansible.cfg` 存在与当前用户家目录
- `/etc/ansible/ansible.cfg`



### 获取默认配置

使用源码或者pip方式安装时，需要另行定义配置文件，可以在ansible仓库中获取最新的配置文件

https://raw.github.com/ansible/ansible/devel/examples/ansible.cfg

 

!!! note
	配置文件是INI格式的一种变体。当注释开始行时，散列符号（#）和分号（;）都被允许作为注释标记。



### 默认配置文件

> 下列是centos7系统上的ansible 2.9.6版本配置

```ini
# config file for ansible -- https://ansible.com/
# ===============================================

# nearly all parameters can be overridden in ansible-playbook
# or with command line flags. ansible will read ANSIBLE_CONFIG,
# ansible.cfg in the current working directory, .ansible.cfg in
# the home directory or /etc/ansible/ansible.cfg, whichever it
# finds first

[defaults]

# some basic default values...

#inventory      = /etc/ansible/hosts
#library        = /usr/share/my_modules/
#module_utils   = /usr/share/my_module_utils/
#remote_tmp     = ~/.ansible/tmp
#local_tmp      = ~/.ansible/tmp
#plugin_filters_cfg = /etc/ansible/plugin_filters.yml
#forks          = 5
#poll_interval  = 15
#sudo_user      = root
#ask_sudo_pass = True
#ask_pass      = True
#transport      = smart
#remote_port    = 22
#module_lang    = C
#module_set_locale = False

# plays will gather facts by default, which contain information about
# the remote system.
#
# smart - gather by default, but don't regather if already gathered
# implicit - gather by default, turn off with gather_facts: False
# explicit - do not gather by default, must say gather_facts: True
#gathering = implicit

# This only affects the gathering done by a play's gather_facts directive,
# by default gathering retrieves all facts subsets
# all - gather all subsets
# network - gather min and network facts
# hardware - gather hardware facts (longest facts to retrieve)
# virtual - gather min and virtual facts
# facter - import facts from facter
# ohai - import facts from ohai
# You can combine them using comma (ex: network,virtual)
# You can negate them using ! (ex: !hardware,!facter,!ohai)
# A minimal set of facts is always gathered.
#gather_subset = all

# some hardware related facts are collected
# with a maximum timeout of 10 seconds. This
# option lets you increase or decrease that
# timeout to something more suitable for the
# environment.
# gather_timeout = 10

# Ansible facts are available inside the ansible_facts.* dictionary
# namespace. This setting maintains the behaviour which was the default prior
# to 2.5, duplicating these variables into the main namespace, each with a
# prefix of 'ansible_'.
# This variable is set to True by default for backwards compatibility. It
# will be changed to a default of 'False' in a future release.
# ansible_facts.
# inject_facts_as_vars = True

# additional paths to search for roles in, colon separated
#roles_path    = /etc/ansible/roles

# uncomment this to disable SSH key host checking
#host_key_checking = False

# change the default callback, you can only have one 'stdout' type  enabled at a time.
#stdout_callback = skippy


## Ansible ships with some plugins that require whitelisting,
## this is done to avoid running all of a type by default.
## These setting lists those that you want enabled for your system.
## Custom plugins should not need this unless plugin author specifies it.

# enable callback plugins, they can output to stdout but cannot be 'stdout' type.
#callback_whitelist = timer, mail

# Determine whether includes in tasks and handlers are "static" by
# default. As of 2.0, includes are dynamic by default. Setting these
# values to True will make includes behave more like they did in the
# 1.x versions.
#task_includes_static = False
#handler_includes_static = False

# Controls if a missing handler for a notification event is an error or a warning
#error_on_missing_handler = True

# change this for alternative sudo implementations
#sudo_exe = sudo

# What flags to pass to sudo
# WARNING: leaving out the defaults might create unexpected behaviours
#sudo_flags = -H -S -n

# SSH timeout
#timeout = 10

# default user to use for playbooks if user is not specified
# (/usr/bin/ansible will use current user as default)
#remote_user = root

# logging is off by default unless this path is defined
# if so defined, consider logrotate
#log_path = /var/log/ansible.log

# default module name for /usr/bin/ansible
#module_name = command

# use this shell for commands executed under sudo
# you may need to change this to bin/bash in rare instances
# if sudo is constrained
#executable = /bin/sh

# if inventory variables overlap, does the higher precedence one win
# or are hash values merged together?  The default is 'replace' but
# this can also be set to 'merge'.
#hash_behaviour = replace

# by default, variables from roles will be visible in the global variable
# scope. To prevent this, the following option can be enabled, and only
# tasks and handlers within the role will see the variables there
#private_role_vars = yes

# list any Jinja2 extensions to enable here:
#jinja2_extensions = jinja2.ext.do,jinja2.ext.i18n

# if set, always use this private key file for authentication, same as
# if passing --private-key to ansible or ansible-playbook
#private_key_file = /path/to/file

# If set, configures the path to the Vault password file as an alternative to
# specifying --vault-password-file on the command line.
#vault_password_file = /path/to/vault_password_file

# format of string {{ ansible_managed }} available within Jinja2
# templates indicates to users editing templates files will be replaced.
# replacing {file}, {host} and {uid} and strftime codes with proper values.
#ansible_managed = Ansible managed: {file} modified on %Y-%m-%d %H:%M:%S by {uid} on {host}
# {file}, {host}, {uid}, and the timestamp can all interfere with idempotence
# in some situations so the default is a static string:
#ansible_managed = Ansible managed

# by default, ansible-playbook will display "Skipping [host]" if it determines a task
# should not be run on a host.  Set this to "False" if you don't want to see these "Skipping"
# messages. NOTE: the task header will still be shown regardless of whether or not the
# task is skipped.
#display_skipped_hosts = True

# by default, if a task in a playbook does not include a name: field then
# ansible-playbook will construct a header that includes the task's action but
# not the task's args.  This is a security feature because ansible cannot know
# if the *module* considers an argument to be no_log at the time that the
# header is printed.  If your environment doesn't have a problem securing
# stdout from ansible-playbook (or you have manually specified no_log in your
# playbook on all of the tasks where you have secret information) then you can
# safely set this to True to get more informative messages.
#display_args_to_stdout = False

# by default (as of 1.3), Ansible will raise errors when attempting to dereference
# Jinja2 variables that are not set in templates or action lines. Uncomment this line
# to revert the behavior to pre-1.3.
#error_on_undefined_vars = False

# by default (as of 1.6), Ansible may display warnings based on the configuration of the
# system running ansible itself. This may include warnings about 3rd party packages or
# other conditions that should be resolved if possible.
# to disable these warnings, set the following value to False:
#system_warnings = True

# by default (as of 1.4), Ansible may display deprecation warnings for language
# features that should no longer be used and will be removed in future versions.
# to disable these warnings, set the following value to False:
#deprecation_warnings = True

# (as of 1.8), Ansible can optionally warn when usage of the shell and
# command module appear to be simplified by using a default Ansible module
# instead.  These warnings can be silenced by adjusting the following
# setting or adding warn=yes or warn=no to the end of the command line
# parameter string.  This will for example suggest using the git module
# instead of shelling out to the git command.
# command_warnings = False


# set plugin path directories here, separate with colons
#action_plugins     = /usr/share/ansible/plugins/action
#become_plugins     = /usr/share/ansible/plugins/become
#cache_plugins      = /usr/share/ansible/plugins/cache
#callback_plugins   = /usr/share/ansible/plugins/callback
#connection_plugins = /usr/share/ansible/plugins/connection
#lookup_plugins     = /usr/share/ansible/plugins/lookup
#inventory_plugins  = /usr/share/ansible/plugins/inventory
#vars_plugins       = /usr/share/ansible/plugins/vars
#filter_plugins     = /usr/share/ansible/plugins/filter
#test_plugins       = /usr/share/ansible/plugins/test
#terminal_plugins   = /usr/share/ansible/plugins/terminal
#strategy_plugins   = /usr/share/ansible/plugins/strategy


# by default, ansible will use the 'linear' strategy but you may want to try
# another one
#strategy = free

# by default callbacks are not loaded for /bin/ansible, enable this if you
# want, for example, a notification or logging callback to also apply to
# /bin/ansible runs
#bin_ansible_callbacks = False


# don't like cows?  that's unfortunate.
# set to 1 if you don't want cowsay support or export ANSIBLE_NOCOWS=1
#nocows = 1

# set which cowsay stencil you'd like to use by default. When set to 'random',
# a random stencil will be selected for each task. The selection will be filtered
# against the `cow_whitelist` option below.
#cow_selection = default
#cow_selection = random

# when using the 'random' option for cowsay, stencils will be restricted to this list.
# it should be formatted as a comma-separated list with no spaces between names.
# NOTE: line continuations here are for formatting purposes only, as the INI parser
#       in python does not support them.
#cow_whitelist=bud-frogs,bunny,cheese,daemon,default,dragon,elephant-in-snake,elephant,eyes,\
#              hellokitty,kitty,luke-koala,meow,milk,moofasa,moose,ren,sheep,small,stegosaurus,\
#              stimpy,supermilker,three-eyes,turkey,turtle,tux,udder,vader-koala,vader,www

# don't like colors either?
# set to 1 if you don't want colors, or export ANSIBLE_NOCOLOR=1
#nocolor = 1

# if set to a persistent type (not 'memory', for example 'redis') fact values
# from previous runs in Ansible will be stored.  This may be useful when
# wanting to use, for example, IP information from one group of servers
# without having to talk to them in the same playbook run to get their
# current IP information.
#fact_caching = memory

#This option tells Ansible where to cache facts. The value is plugin dependent.
#For the jsonfile plugin, it should be a path to a local directory.
#For the redis plugin, the value is a host:port:database triplet: fact_caching_connection = localhost:6379:0

#fact_caching_connection=/tmp



# retry files
# When a playbook fails a .retry file can be created that will be placed in ~/
# You can enable this feature by setting retry_files_enabled to True
# and you can change the location of the files by setting retry_files_save_path

#retry_files_enabled = False
#retry_files_save_path = ~/.ansible-retry

# squash actions
# Ansible can optimise actions that call modules with list parameters
# when looping. Instead of calling the module once per with_ item, the
# module is called once with all items at once. Currently this only works
# under limited circumstances, and only with parameters named 'name'.
#squash_actions = apk,apt,dnf,homebrew,pacman,pkgng,yum,zypper

# prevents logging of task data, off by default
#no_log = False

# prevents logging of tasks, but only on the targets, data is still logged on the master/controller
#no_target_syslog = False

# controls whether Ansible will raise an error or warning if a task has no
# choice but to create world readable temporary files to execute a module on
# the remote machine.  This option is False by default for security.  Users may
# turn this on to have behaviour more like Ansible prior to 2.1.x.  See
# https://docs.ansible.com/ansible/become.html#becoming-an-unprivileged-user
# for more secure ways to fix this than enabling this option.
#allow_world_readable_tmpfiles = False

# controls the compression level of variables sent to
# worker processes. At the default of 0, no compression
# is used. This value must be an integer from 0 to 9.
#var_compression_level = 9

# controls what compression method is used for new-style ansible modules when
# they are sent to the remote system.  The compression types depend on having
# support compiled into both the controller's python and the client's python.
# The names should match with the python Zipfile compression types:
# * ZIP_STORED (no compression. available everywhere)
# * ZIP_DEFLATED (uses zlib, the default)
# These values may be set per host via the ansible_module_compression inventory
# variable
#module_compression = 'ZIP_DEFLATED'

# This controls the cutoff point (in bytes) on --diff for files
# set to 0 for unlimited (RAM may suffer!).
#max_diff_size = 1048576

# This controls how ansible handles multiple --tags and --skip-tags arguments
# on the CLI.  If this is True then multiple arguments are merged together.  If
# it is False, then the last specified argument is used and the others are ignored.
# This option will be removed in 2.8.
#merge_multiple_cli_flags = True

# Controls showing custom stats at the end, off by default
#show_custom_stats = True

# Controls which files to ignore when using a directory as inventory with
# possibly multiple sources (both static and dynamic)
#inventory_ignore_extensions = ~, .orig, .bak, .ini, .cfg, .retry, .pyc, .pyo

# This family of modules use an alternative execution path optimized for network appliances
# only update this setting if you know how this works, otherwise it can break module execution
#network_group_modules=eos, nxos, ios, iosxr, junos, vyos

# When enabled, this option allows lookups (via variables like {{lookup('foo')}} or when used as
# a loop with `with_foo`) to return data that is not marked "unsafe". This means the data may contain
# jinja2 templating language which will be run through the templating engine.
# ENABLING THIS COULD BE A SECURITY RISK
#allow_unsafe_lookups = False

# set default errors for all plays
#any_errors_fatal = False

[inventory]
# enable inventory plugins, default: 'host_list', 'script', 'auto', 'yaml', 'ini', 'toml'
#enable_plugins = host_list, virtualbox, yaml, constructed

# ignore these extensions when parsing a directory as inventory source
#ignore_extensions = .pyc, .pyo, .swp, .bak, ~, .rpm, .md, .txt, ~, .orig, .ini, .cfg, .retry

# ignore files matching these patterns when parsing a directory as inventory source
#ignore_patterns=

# If 'true' unparsed inventory sources become fatal errors, they are warnings otherwise.
#unparsed_is_failed=False

[privilege_escalation]
#become=True
#become_method=sudo
#become_user=root
#become_ask_pass=False

[paramiko_connection]

# uncomment this line to cause the paramiko connection plugin to not record new host
# keys encountered.  Increases performance on new host additions.  Setting works independently of the
# host key checking setting above.
#record_host_keys=False

# by default, Ansible requests a pseudo-terminal for commands executed under sudo. Uncomment this
# line to disable this behaviour.
#pty=False

# paramiko will default to looking for SSH keys initially when trying to
# authenticate to remote devices.  This is a problem for some network devices
# that close the connection after a key failure.  Uncomment this line to
# disable the Paramiko look for keys function
#look_for_keys = False

# When using persistent connections with Paramiko, the connection runs in a
# background process.  If the host doesn't already have a valid SSH key, by
# default Ansible will prompt to add the host key.  This will cause connections
# running in background processes to fail.  Uncomment this line to have
# Paramiko automatically add host keys.
#host_key_auto_add = True

[ssh_connection]

# ssh arguments to use
# Leaving off ControlPersist will result in poor performance, so use
# paramiko on older platforms rather than removing it, -C controls compression use
#ssh_args = -C -o ControlMaster=auto -o ControlPersist=60s

# The base directory for the ControlPath sockets.
# This is the "%(directory)s" in the control_path option
#
# Example:
# control_path_dir = /tmp/.ansible/cp
#control_path_dir = ~/.ansible/cp

# The path to use for the ControlPath sockets. This defaults to a hashed string of the hostname,
# port and username (empty string in the config). The hash mitigates a common problem users
# found with long hostnames and the conventional %(directory)s/ansible-ssh-%%h-%%p-%%r format.
# In those cases, a "too long for Unix domain socket" ssh error would occur.
#
# Example:
# control_path = %(directory)s/%%h-%%r
#control_path =

# Enabling pipelining reduces the number of SSH operations required to
# execute a module on the remote server. This can result in a significant
# performance improvement when enabled, however when using "sudo:" you must
# first disable 'requiretty' in /etc/sudoers
#
# By default, this option is disabled to preserve compatibility with
# sudoers configurations that have requiretty (the default on many distros).
#
#pipelining = False

# Control the mechanism for transferring files (old)
#   * smart = try sftp and then try scp [default]
#   * True = use scp only
#   * False = use sftp only
#scp_if_ssh = smart

# Control the mechanism for transferring files (new)
# If set, this will override the scp_if_ssh option
#   * sftp  = use sftp to transfer files
#   * scp   = use scp to transfer files
#   * piped = use 'dd' over SSH to transfer files
#   * smart = try sftp, scp, and piped, in that order [default]
#transfer_method = smart

# if False, sftp will not use batch mode to transfer files. This may cause some
# types of file transfer failures impossible to catch however, and should
# only be disabled if your sftp version has problems with batch mode
#sftp_batch_mode = False

# The -tt argument is passed to ssh when pipelining is not enabled because sudo 
# requires a tty by default. 
#usetty = True

# Number of times to retry an SSH connection to a host, in case of UNREACHABLE.
# For each retry attempt, there is an exponential backoff,
# so after the first attempt there is 1s wait, then 2s, 4s etc. up to 30s (max).
#retries = 3

[persistent_connection]

# Configures the persistent connection timeout value in seconds.  This value is
# how long the persistent connection will remain idle before it is destroyed.
# If the connection doesn't receive a request before the timeout value
# expires, the connection is shutdown. The default value is 30 seconds.
#connect_timeout = 30

# The command timeout value defines the amount of time to wait for a command
# or RPC call before timing out. The value for the command timeout must
# be less than the value of the persistent connection idle timeout (connect_timeout)
# The default value is 30 second.
#command_timeout = 30

[accelerate]
#accelerate_port = 5099
#accelerate_timeout = 30
#accelerate_connect_timeout = 5.0

# The daemon timeout is measured in minutes. This time is measured
# from the last activity to the accelerate daemon.
#accelerate_daemon_timeout = 30

# If set to yes, accelerate_multi_key will allow multiple
# private keys to be uploaded to it, though each user must
# have access to the system via SSH to add a new key. The default
# is "no".
#accelerate_multi_key = yes

[selinux]
# file systems that require special treatment when dealing with security context
# the default behaviour that copies the existing context or uses the user default
# needs to be changed to use the file system dependent context.
#special_context_filesystems=nfs,vboxsf,fuse,ramfs,9p,vfat

# Set this to yes to allow libvirt_lxc connections to work without SELinux.
#libvirt_lxc_noseclabel = yes

[colors]
#highlight = white
#verbose = blue
#warn = bright purple
#error = red
#debug = dark gray
#deprecate = purple
#skip = cyan
#unreachable = red
#ok = green
#changed = yellow
#diff_add = green
#diff_remove = red
#diff_lines = cyan


[diff]
# Always print diff when running ( same as always running with -D/--diff )
# always = no

# Set how many context lines to show in diff
# context = 3
```

### 常用设置

下列列出了常用的一些设置，可用作参考。

```ini
[defaults]
# Set the log_path
log_path = ~/ansible.log

# Additional default options for Ansible
forks = 20
host_key_checking = False
retry_files_enabled = False
retry_files_save_path = ~/ansible-installer-retries
nocows = True
remote_user = root
roles_path = roles/
gathering = smart
fact_caching = jsonfile
fact_caching_connection = $HOME/ansible/facts
fact_caching_timeout = 600
callback_whitelist = profile_tasks
inventory_ignore_extensions = secrets.py, .pyc, .cfg, .crt, .ini
# work around privilege escalation timeouts in ansible:
timeout = 30
host_key_checking = False

# Uncomment to use the provided example inventory
#inventory = inventory/hosts.example

[inventory]
# fail more helpfully when the inventory file does not parse (Ansible 2.4+)
unparsed_is_failed=true

# Additional ssh options for OpenShift Ansible
[ssh_connection]
retries = 15
pipelining = True
ssh_args = -o ControlMaster=auto -o ControlPersist=600s
timeout = 10
# shorten the ControlPath which is often too long; when it is,
# ssh connection reuse silently fails, making everything slower.
control_path = %(directory)s/%%h-%%r
```

## ansible-config

使用 `ansible-config` 程序可以查看所有可用的配置设置、以及它们的默认值、还有它们的当前值来自何处。 

**查看当前配置文件**

```bash
ansible-config view
```

**查看当前配置**

```bash
ansible-config dump
```

**查看配置项说明**

```bash
ansible-config list
```

## 配置的优先级

**Ansible** 提供了四种资源来控制它的行为。按照从最低(最容易被覆盖)到最高(覆盖所有其他)的优先级顺序，这些类别是 

- Configuration settings  配置文件设置

	!!! note
		**Ansible** 配置文件拥有最低的优先级，但文件可以存放在不同的位置，其中只有一个可用。在下列列表中，ansible从上往下依次检查，检查到哪个可用就用哪个。
		
		- `ANSIBLE_CONFIG` 环境变量，可以定义配置文件的位置
		- `./ansible.cfg` 存在于当前工作目录
		- `~/.ansible.cfg` 存在与当前用户家目录
		- `/etc/ansible/ansible.cfg`

- Command-line options 命令行选项

	!!! note
		命令行选项将覆盖任何配置文件的设置
    	```yaml
    	# 指定多个-u时，后面的覆盖前面
    	ansible -u mike -m ping myhost -u carol
    	# 可以指定多个-i选项
    	ansible -i /path/inventory1 -i /path/inventory2 -m ping all
    	```
- Playbook keywords  playbook关键字

	!!! note
    	playbook关键字 将覆盖命令行选项和配置文件中的设置
    	在playbook关键字中，优先级与playbook本身一起变动;越具体的设置越能战胜越笼统的设置，如 `tasks > blocks/includes/imports/roles > play`
    	```yaml
    	- hosts: all
      	  connection: ssh
    	  tasks:
    	    - name: This task uses ssh.
    	      ping:
    	    - name: This task uses paramiko.
    	      connection: paramiko
    	      ping:
    	```
- Variables  变量

	!!! note
		变量将覆盖playbook关键字、命令行选项和配置文件中设置
		在playbook中使用`vars` 设置变量，其中变量优先级也是遵守具体优先的策略。
		```yaml
        - hosts: cloud
          gather_facts: false
          become: yes
          vars:
            ansible_become_user: admin
          tasks:
            - name: This task uses admin as the become user.
              dnf:
                name: some-service
                state: latest
            - block:
                - name: This task uses service-admin as the become user.
                  # a task to configure the new service
                - name: This task also uses service-admin as the become user, defined in the block.
                  # second task to configure the service
              vars:
                ansible_become_user: service-admin
            - name: This task (outside of the block) uses admin as the become user again.
              service:
                name: some-service
                state: restarted
		```
		在命令行工具中使用 `-e` 指定变量时，将覆盖playbook中的变量
		```bash
		ansible -u carol -e 'ansible_user=brian' -a whoami all
		```

## 配置项

列出`ansible`目前版本（`2.9.6`）可用的选项配置

| 环境变量                                 | Ini key                       | Ini  section          | 类型     | 默认值                                                       | 说明                                                         |
| ---------------------------------------- | :---------------------------- | --------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ANSIBLE_ACTION_WARNINGS                  | action_warnings               | defaults              |   boolean       |True                                                              |      输出任务的警告信息                                                        |
| ANSIBLE_AGNOSTIC_BECOME_PROMPT                  | agnostic_become_prompt               | privilege_escalation              |   boolean       |True                                                              |      输出权限提升提示                                                        |
|             | allow_world_readable_tmpfiles | defaults              | boolean  | False                                                        | 是否在目标服务器上创建临时目录时显示警告而不是失败。         |
| ANSIBLE_CONNECTION_PATH            | ansible_connection_path | persistent_connection              | path  | None                                                        | 指定在何处查找ansibl-connection脚本，为空时，将在当前目录查找         |
| ANSIBLE_COW_PATH            | cowpath | defaults              | string  | None                                                        | 指定一个自定义cowsay路径         |
| ANSIBLE_COW_SELECTION            | cow_selection | defaults              |   | defaults                                                        | 选择一个特定的cowsay模板        |
| ANSIBLE_COW_WHITELIST            | cow_whitelist | defaults              | list  | [‘bud-frogs`, ‘bunny`, ‘cheese`, ‘daemon`, ‘default`, ‘dragon`, ‘elephant-in-snake`, ‘elephant`, ‘eyes`, ‘hellokitty`, ‘kitty`, ‘luke-koala`, ‘meow`, ‘milk`, ‘moofasa`, ‘moose`, ‘ren`, ‘sheep`, ‘small`, ‘stegosaurus`, ‘stimpy`, ‘supermilker`, ‘three-eyes`, ‘turkey`, ‘turtle`, ‘tux`, ‘udder`, ‘vader-koala`, ‘vader`, ‘www`] | Cowsay模板白名单         |
| ANSIBLE_FORCE_COLOR            | force_color | defaults              | boolean  | False                                                        | 强制输出颜色        |
| ANSIBLE_NOCOLOR                          | nocolor                       | defaults              | boolean  | False                                                        | 是否允许着色显示信息。                                       |
| ANSIBLE_NOCOWS                           | nocows                        | defaults              | boolean  | False                                                        | 如果你已经安装了cowsay，但是想避免使用`cows`，请使用这个。 |
| ANSIBLE_PIPELINING            | pipelining | connection              | boolean  | False                                                        | 连接管道        |
| ANSIBLE_SSH_PIPELINING                   | pipelining                    | ssh_connection        | boolean  | False                                                        | 启用管道模式， 启用后可以提高性能。                          |
| ANSIBLE_SSH_ARGS                         | ssh_args                      | ssh_connection        |          | -C -o  ControlMaster=auto -o ControlPersist=60s              | ssh参数                                                      |
| ANSIBLE_CONNECTION_PATH            | ansible_connection_path | persistent_connection              | path  | None                                                        | 指定在何处查找ansibl-connection脚本，为空时，将在当前目录查找         |
| ANSIBLE_SSH_CONTROL_PATH_DIR             | control_path_dir              | ssh_connection        |          | ~/.ansible/cp                                                | ssh控制路径的目录                                            |
| ANSIBLE_SSH_CONTROL_PATH                 | control_path                  | ssh_connection        |          | None                                                         | 这是保存ssh的ControlPath套接字的位置，它使用ssh的变量替换。  |
| ANSIBLE_SSH_EXECUTABLE                 | ssh_executable                  | ssh_connection        |          | ssh                                                         | 定义了ssh二进制文件的位置  |
| ANSIBLE_SSH_RETRIES                 | retries                  | ssh_connection        | 	integer   | 0                                                         | ssh尝试建立连接的次数  |
| ANSIBLE_ANY_ERRORS_FATAL                 | any_errors_fatal              | defaults              | boolean  | False                                                        | 为True，则任务失败将被视为致命错误，会立即停止执行           |
| ANSIBLE_BECOME_ALLOW_SAME_USER           | become_allow_same_user              | privilege_escalation              | boolean  | False                                                        | 当连接用户和become用户一致时，是否跳过become          |
| ANSIBLE_BECOME_PLUGINS          | become_plugins              | defaults              | pathspec  | ~/.ansible/plugins/become:/usr/share/ansible/plugins/become | become 插件路径         |
| ANSIBLE_INVENTORY                        | inventory                     | defaults              | pathlist | /etc/ansible/hosts                                           | 逗号分隔的主机文件列表                                       |
| ANSIBLE_LIBRARY                          | library                       | defaults              | pathspec | ~/.ansible/plugins/modules:/usr/share/ansible/plugins/modules | 冒号分隔的模块路径                                           |
| ANSIBLE_MODULE_UTILS                     | module_utils                  | defaults              | pathspec | ~/.ansible/plugins/module_utils:/usr/share/ansible/plugins/module_utils | 用于存放模块共享的文件                                       |
|                                          | remote_tmp                    | defaults              | tmppath  | ~/.ansible/tmp                                               | 节点的临时目录                                               |
| ANSIBLE_LOCAL_TEMP                       | local_tmp                     | defaults              | tmppath  | ~/.ansible/tmp                                               | 控制端的临时目录                                             |
|                                          | plugin_filters_cfg            | defaults              |          | /etc/ansible/plugin_filters.yml                              | 插件过滤器文件                                               |
| ANSIBLE_FORKS                            | forks                         | defaults              | integer  | 5                                                            | 在目标主机上执行任务的最大数。                               |
| ANSIBLE_POLL_INTERVAL                    | poll_interval                 | defaults              | integer  | 15                                                           | 指定异步任务的轮询间隔时间                                   |
| ANSIBLE_SUDO_USER                        | sudo_user                     | defaults              |          | None                                                         | sudo的用户，将在2.8废弃                                      |
| ANSIBLE_ASK_SUDO_PASS                    | ask_sudo_pass                 | defaults              | boolean  | False                                                        | 是否提示输入sudo用户的密码，将在2.8废弃                      |
| ANSIBLE_ASK_PASS                         | ask_pass                      | defaults              | boolean  | False                                                        | 是否提示输入ssh连接密码，使用ssh秘钥链接不需要打开此项。     |
| ANSIBLE_TRANSPORT                        | transport                     | defaults              |          | smart                                                        | 默认连接插件                                                 |
| ANSIBLE_REMOTE_PORT                      | remote_port                   | defaults              | integer  | None                                                         | 用于远程连接的端口，为空时，将用插件默认值                   |
| ANSIBLE_MODULE_LANG                      | module_lang                   | defaults              |          | {{ CONTROLLER_LANG }}                                        | 在目标上执行时用于模块的语言区域设置。  如果为空，它会尝试将其自身设置为控制器上的LANG环境变量。仅在module_set_locale为ture的时候。 |
| ANSIBLE_MODULE_SET_LOCALE                | module_set_locale             | defaults              | boolean  | False                                                        | 控制在目标上执行时是否为模块设置语言环境。                   |
| ANSIBLE_GATHERING                        | gathering                     | defaults              |          | implicit                                                     | 是否收集fact信息                                             |
| ANSIBLE_GATHER_SUBSET                    | gather_subset                 | defaults              |          | all                                                          | 设置收集fact的分组模块                                       |
| ANSIBLE_GATHER_TIMEOUT                   | gather_timeout                | defaults              | integer  | 10                                                           | 设置超时值，以秒为单位。                                     |
| ANSIBLE_ROLES_PATH                       | roles_path                    | defaults              | pathspec | ~/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles | 搜索roles的路径                                              |
| ANSIBLE_HOST_KEY_CHECKING                | host_key_checking             | defaults              | boolean  | True                                                         | 连接主机时是否进行主机密钥检查                               |
| ANSIBLE_STDOUT_CALLBACK                  | stdout_callback               | defaults              |          | defaults                                                     | 设置ansible显示输出的callback，只能设置一个。                |
| ANSIBLE_CALLBACK_WHITELIST               | callback_whitelist            | defaults              | list     | []                                                           | callback的白名单列表，只有在这个列表中，ansible才会使用。    |
| ANSIBLE_TASK_INCLUDES_STATIC             | task_includes_static          | defaults              | boolean  | False                                                        | 是否将include设置为静态包含。2.8废弃                         |
| ANSIBLE_HANDLER_INCLUDES_STATIC          | handler_includes_static       | defaults              | boolean  | False                                                        | 是否将include设置为静态包含。2.8废弃                         |
| ANSIBLE_ERROR_ON_MISSING_HANDLER         | error_on_missing_handler      | defaults              | boolean  | True                                                         | 是否在handler程序缺少或错误的时候，提示警告而不是错误。      |
| ANSIBLE_SUDO_EXE                         | sudo_exe                      | defaults              |          | sudo                                                         | 指定一个“sudo”可执行文件，2.8废弃                            |
| ANSIBLE_SUDO_FLAGS                       | sudo_flags                    | defaults              |          | -H -S -n                                                     | 指定sudo的参数，2.8废弃                                      |
| ANSIBLE_TIMEOUT                          | Timeout                       | defaults              | integer  | 10                                                           | 连接插件使用的默认超时时间。                                 |
| ANSIBLE_REMOTE_USER                      | remote_user                   | defaults              |          | None                                                         | 设置目标的登录用户，如果为空，则为运行ansible的用户          |
| ANSIBLE_LOG_PATH                         | log_path                      | defaults              |          | None                                                         | 在控制器上的日志文件路径，用于记录ansible运行的日志。        |
|                                          | module_name                   | defaults              |          | command                                                      | AdHoc命令一起使用，没有指定-m模块的就用这个默认值            |
| ANSIBLE_EXECUTABLE                       | executable                    | defaults              |          | /bin/sh                                                      | 在节点上，ansible执行的shell解释器。                         |
| ANSIBLE_HASH_BEHAVIOUR                   | hash_behaviour                | defaults              | string   | replace                                                      | 控制Ansible中的变量合并方式。                                |
| ANSIBLE_PRIVATE_ROLE_VARS                | private_role_vars             | defaults              | boolean  | False                                                        | 使角色变量无法从其他角色访问。                               |
| ANSIBLE_JINJA2_EXTENSIONS                | jinja2_extensions             | defaults              |          | []                                                           | 启用额外的Jinja2扩展列表                                     |
| ANSIBLE_PRIVATE_KEY_FILE                 | private_key_file              | defaults              |          | None                                                         | 连接证书或密码，-private-key的默认值                         |
| ANSIBLE_VAULT_PASSWORD_FILE              | vault_password_file           | defaults              | path     | None                                                         | 要使用的vault密码文件。  等同于-vault-password-file或-vault-id |
|                                          | ansible_managed               | defaults              |          | Ansible  managed                                             | 在模板ansible_managed的值                                    |
| DISPLAY_SKIPPED_HOSTS                    | display_skipped_hosts         | defaults              | boolean  | True                                                         | 在默认callback插件中是否显示跳过的主机信息。                 |
| ANSIBLE_DISPLAY_ARGS_TO_STDOUT           | display_args_to_stdout        | defaults              | boolean  | False                                                        | 是否在callback中显示任务的参数信息                           |
| ANSIBLE_ERROR_ON_UNDEFINED_VARS          | error_on_undefined_vars       | defaults              | boolean  | True                                                         | 模板中出现错误或未定义的变量，是否提示错误信息。             |
| ANSIBLE_SYSTEM_WARNINGS                  | system_warnings               | defaults              | boolean  | True                                                         | 是否显示系统警告信息。                                       |
| ANSIBLE_DEPRECATION_WARNINGS             | deprecation_warnings          | defaults              | boolean  | True                                                         | 是否显示模块被弃用的警告信息。                               |
| ANSIBLE_COMMAND_WARNINGS                 | command_warnings              | defaults              | boolean  | True                                                         | 是否显示，在shell和command模块中使用与ansible模块类似的警告信息。 |
| ANSIBLE_ACTION_PLUGINS                   | action_plugins                | defaults              | pathspec | ~/.ansible/plugins/action:/usr/share/ansible/plugins/action  | action插件的搜索路径                                         |
| ANSIBLE_CACHE_PLUGINS                    | cache_plugins                 | defaults              | pathspec | ~/.ansible/plugins/cache:/usr/share/ansible/plugins/cache    | cache插件的搜索路径                                          |
| ANSIBLE_CALLBACK_PLUGINS                 | callback_plugins              | defaults              | pathspec | ~/.ansible/plugins/callback:/usr/share/ansible/plugins/callback | callback插件的搜索路径                                       |
| ANSIBLE_CONNECTION_PLUGINS               | connection_plugins            | defaults              | pathspec | ~/.ansible/plugins/connection:/usr/share/ansible/plugins/connection | connection插件的搜索路径                                     |
| ANSIBLE_LOOKUP_PLUGINS                   | lookup_plugins                | defaults              | pathspec | ~/.ansible/plugins/lookup:/usr/share/ansible/plugins/lookup  | lookup插件的搜索路径                                         |
| ANSIBLE_INVENTORY_PLUGINS                | inventory_plugins             | defaults              | pathspec | ~/.ansible/plugins/inventory:/usr/share/ansible/plugins/inventory | inventory插件的搜索路径                                      |
| ANSIBLE_VARS_PLUGINS                     | vars_plugins                  | defaults              | pathspec | ~/.ansible/plugins/vars:/usr/share/ansible/plugins/vars      | vars插件的搜索路径                                           |
| ANSIBLE_FILTER_PLUGINS                   | filter_plugins                | defaults              | pathspec | ~/.ansible/plugins/filter:/usr/share/ansible/plugins/filter  | filter插件的搜索路径                                         |
| ANSIBLE_TEST_PLUGINS                     | test_plugins                  | defaults              | pathspec | ~/.ansible/plugins/test:/usr/share/ansible/plugins/test      | test插件的搜索路径                                           |
| ANSIBLE_TERMINAL_PLUGINS                 | terminal_plugins              | defaults              | pathspec | ~/.ansible/plugins/terminal:/usr/share/ansible/plugins/terminal | terminal插件的搜索路径                                       |
| ANSIBLE_STRATEGY_PLUGINS                 | strategy_plugins              | defaults              | pathspec | ~/.ansible/plugins/strategy:/usr/share/ansible/plugins/strategy | strategy插件的搜索路径                                       |
| ANSIBLE_STRATEGY                         | strategy                      | defaults              |          | linear                                                       | 默认策略                                                     |
| ANSIBLE_LOAD_CALLBACK_PLUGINS            | bin_ansible_callbacks         | defaults              | boolean  | False                                                        | 控制运行ansible时，是否加载callback插件                      |
| ANSIBLE_CACHE_PLUGIN                     | fact_caching                  | defaults              |          | memory                                                       | 选择使用哪个缓存插件为fact存储所用                           |
| ANSIBLE_CACHE_PLUGIN_CONNECTION                     | fact_caching_connection                  | defaults              |          | none                                                       | 定义缓存插件的连接                          |
| ANSIBLE_CACHE_PLUGIN_PREFIX                     | fact_caching_prefix                  | defaults              |          |ansible_facts                                                       | 缓存插件文件/表的前缀                          |
| ANSIBLE_CACHE_PLUGIN_TIMEOUT                     | fact_caching_timeout                  | defaults    |   integer     | 86400| 缓存插件数据的过期超时时间                         |
| ANSIBLE_RETRY_FILES_ENABLED              | retry_files_enabled           | defaults              | boolean  | True                                                         | 控制着一个失败的Ansible剧本应该创建一个.retry文件。          |
| ANSIBLE_RETRY_FILES_SAVE_PATH            | retry_files_save_path         | defaults              | path     | none                                                         | 保存.retry文件的路径。                                       |
| ANSIBLE_SQUASH_ACTIONS                   | squash_actions                | defaults              | list     | apk, apt,  dnf, homebrew, openbsd_pkg, pacman, pkgng, yum, zypper | 在使用with_循环时，Ansible可以优化调用支持列表参数的模块的操作。使参数组合为一个列表传递给模块。 |
| ANSIBLE_NO_LOG                           | no_log                        | defaults              | boolean  | False                                                        | 控制Ansible的显示和记录任务信息日志。                        |
| ANSIBLE_NO_TARGET_SYSLOG                 | no_target_syslog              | defaults              | boolean  | False                                                        | 执行任务时，Ansible日志是否显示在目标系统日志。              |
|                                          | module_compression            | defaults              |          | ZIP_DEFLATED                                                 | 将Python模块传输到目标时使用的压缩方案。                     |
| ANSIBLE_MAX_DIFF_SIZE                    | max_diff_size                 | defaults              | int      | 104448                                                       | 要显示差异文件的最大文件大小                                 |
| ANSIBLE_SHOW_CUSTOM_STATS                | show_custom_stats             | defaults              | boolean  | False                                                        | 是否通过set_stats插件设置的自定义统计信息添加到默认输出      |
| ANSIBLE_INVENTORY_IGNORE                 | inventory_ignore_extensions   | defaults              |          | {{(BLACKLIST_EXTS  + ( ‘~`, ‘.orig`, ‘.ini`, ‘.cfg`, ‘.retry`))}} | 将目录用作库存源时忽略的扩展名列表                           |
|                                          | allow_unsafe_lookups          | defaults              | boolean  | False | 为True时，此选项允许查找插件（无论在变量中用作{{lookup（'foo'）}}还是作为with_foo的循环）返回未标记为'unsafe'的数据。 |
| ANSIBLE_INVENTORY_ENABLED                | enable_plugins                | inventory             |          | [‘host_list`,  ‘script`, ‘yaml`, ‘ini`, ‘auto`]              | 启用的库存插件列表，也决定了它们的使用顺序。                 |
| ANSIBLE_INVENTORY_IGNORE                 | ignore_extensions             | inventory             |          | {{(BLACKLIST_EXTS  + ( ‘~`, ‘.orig`, ‘.ini`, ‘.cfg`, ‘.retry`))}} | 将目录用作库存源时忽略的扩展名列表                           |
| ANSIBLE_INVENTORY_IGNORE_REGEX           | ignore_patterns               | inventory             | list     | []                                                           | 将目录用作库存源时要忽略的模式列表                           |
| ANSIBLE_INVENTORY_UNPARSED_FAILED        | unparsed_is_failed            | inventory             | boolean  | False                                                        | 为true时，未分类的主机会提示致命错误。                       |
| ANSIBLE_BECOME                           | become                        | privilege_escalation  | boolean  | False                                                        | 是否开启特权升级                                             |
| ANSIBLE_BECOME_METHOD                    | become_method                 | privilege_escalation  |          | sudo                                                         | 特权升级的方式                                               |
| ANSIBLE_BECOME_USER                      | become_user                   | privilege_escalation  |          | root                                                         | 特权升级的用户                                               |
| ANSIBLE_BECOME_ASK_PASS                  | become_ask_pass               | privilege_escalation  | boolean  | False                                                        | 输入特权升级的密码                                           |
| ANSIBLE_BECOME_FLAGS                     | become_flags                  | privilege_escalation  |          |                                                              | 传递给特权升级可执行文件的参数。                             |
| ANSIBLE_BECOME_EXE                       | become_exe                    | privilege_escalation  |          | None                                                         | 可执行文件                                                   |
| ANSIBLE_PARAMIKO_LOOK_FOR_KEYS           | look_for_keys                 | paramiko_connection   | boolean  | True                                                         | paramiko在尝试向远程设备进行身份验证时默认查找SSH密钥。      |
| ANSIBLE_PARAMIKO_HOST_KEY_AUTO_ADD       | host_key_auto_add             | paramiko_connection   | boolean  | False | 默认情况下，Ansible将提示添加主机密钥。 这将导致在后台进程中运行的连接失败。为true时，Paramiko自动添加主机密钥。 |
| ANSIBLE_SCP_IF_SSH                       | scp_if_ssh                    | ssh_connection        |          | smart                                                        | 通过ssh传输文件时使用的首选方法，使用smart时，先尝试sftp，在尝试scp。 |
| ANSIBLE_SSH_TRANSFER_METHOD              | transfer_method               | ssh_connection        |          | None                                                         | 通过ssh传输文件时使用的首选方法，如果配置了，会覆盖scp_if_ssh |
| ANSIBLE_SFTP_BATCH_MODE                  | sftp_batch_mode               | ssh_connection        | boolean  | True                                                         | 如果为False，sftp将不使用批处理模式传输文件。                |
| ANSIBLE_PERSISTENT_CONNECT_TIMEOUT       | connect_timeout               | persistent_connection | integer  | 30                                                           | 控制连接保持空闲状态的时间。                                 |
| ANSIBLE_PERSISTENT_CONNECT_RETRY_TIMEOUT | connect_retry_timeout         | persistent_connection | integer  | 15                                                           | 控制连接重试超时时间                                         |
| ANSIBLE_PERSISTENT_CONNECT_TIMEOUT       | command_timeout               | persistent_connection | integer  | 30                                                           | 控制连接超时时间                                             |
| ANSIBLE_SELINUX_SPECIAL_FS               | special_context_filesystems   | selinux               | list     | fuse, nfs, vboxsf, ramfs, 9p, vfat| 在处理安全上下文时需要特殊处理的文件系统  |
| LIBVIRT_LXC_NOSECLABEL                   | libvirt_lxc_noseclabel        | selinux               | boolean  | False                                                        | 通过将-noseclabel传递给virsh，允许libvirt_lxc连接在没有SELinux的情况下工作。 |
| ANSIBLE_COLOR_HIGHLIGHT                  | highlight                     | colors                |          | white                                                        | 定义用于突出显示的颜色                                       |
| ANSIBLE_COLOR_VERBOSE                    | verbose                       | colors                |          | blue                                                         | 定义发出详细消息时要使用的颜色。  即那些用'-v'表示的。       |
| ANSIBLE_COLOR_WARN                       | warn                          | colors                |          | bright  purple                                               | 定义发出警告消息时要使用的颜色                               |
| ANSIBLE_COLOR_ERROR                      | error                         | colors                |          | red                                                          | 定义发出错误消息时使用的颜色                                 |
| ANSIBLE_COLOR_DEBUG                      | debug                         | colors                |          | dark gray                                                    | 定义发出调试消息时使用的颜色                                 |
| ANSIBLE_COLOR_DEPRECATE                  | deprecate                     | colors                |          | purple                                                       | 定义发出弃用消息时要使用的颜色                               |
| ANSIBLE_COLOR_UNREACHABLE                | unreachable                   | colors                |          | bright  red                                                  | 定义在“无法到达”状态下使用的颜色                             |
| ANSIBLE_COLOR_CHANGED                    | changed                       | colors                |          | yellow                                                       | 定义在“更改”任务状态上使用的颜色                             |
| ANSIBLE_COLOR_DIFF_ADD                   | diff_add                      | colors                |          | green                                                        | 定义在差异中显示添加行时使用的颜色                           |
| ANSIBLE_COLOR_DIFF_REMOVE                | diff_remove                   | colors                |          | red                                                          | 定义在差异中显示已删除行时使用的颜色                         |
| ANSIBLE_COLOR_DIFF_LINES                 | diff_lines                    | colors                |          | cyan                                                         | 定义显示差异时使用的颜色                                     |
| ANSIBLE_DIFF_ALWAYS                      | always                        | diff                  | boolean  | False                                                        | 是否显示模块在处于“更改”状态时显示差异，相当于--diff。       |
| ANSIBLE_DIFF_CONTEXT                     | context                       | diff                  | integer  | 3                                                            | 在显示文件之间的差异时显示多少行上下文。                     |
| ANSIBLE_YAML_FILENAME_EXT                | yaml_valid_extensions         | defaults              | List     | [`.yml`, `.yaml`, `.json`]                                  |         yaml文件的扩展名                                                     |

详细见[官网](https://docs.ansible.com/ansible/latest/reference_appendices/config.html)