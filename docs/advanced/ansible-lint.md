# 使用 ansible-lint

[Ansible Lint]( https://github.com/ansible/ansible-lint )是用于检测playbook的命令行工具，它可以提供建议来帮助你修正playbook。



## 安装

```bash
pip install ansible-lint
```



## 使用

命令选项

```bash
ansible-lint --help
Usage: ansible-lint [options] [playbook.yml [playbook2 ...]]

Options:
  --version             显示项目版本
  -h, --help            显示帮助信息
  -L                    列出所有规则
  -q                    输出少量信息
  -p                    以pep8格式解析的输出
  --parseable-severity  分析输出，包括规则的严重性
  -r RULESDIR           指定规则目录，使用多个-r指定多个目录会覆盖默认目录 /usr/lib/python2.7/site-packages/ansiblelint/rules, 使用-R则不覆盖默认规则目录
  -R                    跟-r一起使用。
  -t TAGS               仅检查tag标签的任务
  -T                    列出所有tag
  -v                    详细输出
  -x SKIP_LIST          跳过指定的id/tags任务
  --nocolor             关闭颜色输出
  --force-color         强制颜色输出
  --exclude=EXCLUDE_PATHS
                        要排除的目录或文件的路径。可多次指定。
  -c C                  指定配置文件，默认".ansible-lint"
```

### 检查roles

```bash
# ansible-lint roles/os-check   
[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:32
    - check_mail_host != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:33
    - check_mail_port != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:34
    - check_mail_username != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:35
    - check_mail_password != ""
```

### 检查playbook

```bash
# cat playbook.yaml 
---
- hosts: all
  tasks:
    - debug: msg=hello
  roles:
    - os-check
    
# ansible-lint playbook.yaml        
[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:32
    - check_mail_host != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:33
    - check_mail_port != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:34
    - check_mail_username != ""

[602] Don't compare to empty string
roles/os-check/tasks/main.yaml:35
    - check_mail_password != ""

```

根据规则提示，来修正你的playbook



## 配置文件

Ansible-lint 默认寻找当前目录的` .ansible-lint `作为配置文件，也可指定`-c file` 指定一个配置文件。

配置文件支持以下值，并且其功能与对应的CLI相同

```yaml
exclude_paths:
  - ./my/excluded/directory/
  - ./my/other/excluded/directory/
  - ./last/excluded/directory/
parseable: true
quiet: true
rulesdir:
  - ./rule/directory/
skip_list:
  - skip_this_tag
  - and_this_one_too
  - skip_this_id
  - '401'
tags:
  - run_this_tag
use_default_rules: true
verbosity: 1
```

## 规则

默认规则存在`/usr/lib/python2.7/site-packages/ansiblelint/rules` 目录中，可以使用`-r`选项指定规则目录，和` -R `一起使用时保留默认规则目录，反之替换。

### 列出规则

```bash
# ansible-lint -L 
101: Deprecated always_run
  Instead of ``always_run``, use ``check_mode``
102: No Jinja2 in when
  ``when`` lines should not include Jinja2 variables
103: Deprecated sudo
  Instead of ``sudo``/``sudo_user``, use ``become``/``become_user``.
104: Using bare variables is deprecated
  Using bare variables is deprecated. Update your playbooks so that the environment value uses the full variable syntax ``{{ your_variable }}``
105: Deprecated module
  These are deprecated modules, some modules are kept temporarily for backwards compatibility but usage is discouraged. For more details see: https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html
201: Trailing whitespace
  There should not be any trailing whitespace
202: Octal file permissions must contain leading zero or be a string
  Numeric file permissions without leading zero can behave in unexpected ways. See http://docs.ansible.com/ansible/file_module.html
203: Most files should not contain tabs
  Tabs can cause unexpected display issues, use spaces
204: Lines should be no longer than 160 chars
  Long lines make code harder to read and code review more difficult
205: Use ".yml" or ".yaml" playbook extension
  Playbooks should have the ".yml" or ".yaml" extension
206: Variables should have spaces before and after: {{ var_name }}
  Variables should have spaces before and after: ``{{ var_name }}``
301: Commands should not change things if nothing needs doing
  Commands should either read information (and thus set ``changed_when``) or not do something if it has already been done (using creates/removes) or only do it if another check has a particular result (``when``)
302: Using command rather than an argument to e.g. file
  Executing a command when there are arguments to modules is generally a bad idea
303: Using command rather than module
  Executing a command when there is an Ansible module is generally a bad idea
304: Environment variables don't work as part of command
  Environment variables should be passed to ``shell`` or ``command`` through environment argument
305: Use shell only when shell functionality is required
  Shell should only be used when piping, redirecting or chaining commands (and Ansible would be preferred for some of those!)
306: Shells that use pipes should set the pipefail option
  Without the pipefail option set, a shell command that implements a pipeline can fail and still return 0. If any part of the pipeline other than the terminal command fails, the whole pipeline will still return 0, which may be considered a success by Ansible. Pipefail is available in the bash shell.
401: Git checkouts must contain explicit version
  All version control checkouts must point to an explicit commit or tag, not just ``latest``
402: Mercurial checkouts must contain explicit revision
  All version control checkouts must point to an explicit commit or tag, not just ``latest``
403: Package installs should not use latest
  Package installs should use ``state=present`` with or without a version
404: Doesn't need a relative path in role
  ``copy`` and ``template`` do not need to use relative path for ``src``
501: become_user requires become to work as expected
  ``become_user`` without ``become`` will not actually change user
502: All tasks should be named
  All tasks should have a distinct name for readability and for ``--start-at-task`` to work
503: Tasks that run when changed should likely be handlers
  If a task has a ``when: result.changed`` setting, it is effectively acting as a handler
504: Do not use 'local_action', use 'delegate_to: localhost'
  Do not use ``local_action``, use ``delegate_to: localhost``
601: Don't compare to literal True/False
  Use ``when: var`` rather than ``when: var == True`` (or conversely ``when: not var``)
602: Don't compare to empty string
  Use ``when: var`` rather than ``when: var != ""`` (or conversely ``when: not var`` rather than ``when: var == ""``)
701: meta/main.yml should contain relevant info
  meta/main.yml should contain: ``author, description, license, min_ansible_version, platforms``
702: Tags must contain lowercase letters and digits only
  Tags must contain lowercase letters and digits only, and ``galaxy_tags`` is expected to be a list
703: meta/main.yml default values should be changed
  meta/main.yml default values should be changed for: ``author, description, company, license, license``
704: meta/main.yml video_links should be formatted correctly
  Items in ``video_links`` in meta/main.yml should be dictionaries, and contain only keys ``url`` and ``title``, and have a shared link from a supported provider
```

### 规则标记

使用下列的命令可以查看规则有那些标记

```bash
# ansible-lint -v -T
ANSIBLE0002 ['[201]']
ANSIBLE0004 ['[401]']
ANSIBLE0005 ['[402]']
ANSIBLE0006 ['[303]']
ANSIBLE0007 ['[302]']
ANSIBLE0008 ['[103]']
ANSIBLE0009 ['[202]']
ANSIBLE0010 ['[403]']
ANSIBLE0011 ['[502]']
ANSIBLE0012 ['[301]']
ANSIBLE0013 ['[305]']
ANSIBLE0014 ['[304]']
ANSIBLE0015 ['[104]']
ANSIBLE0016 ['[503]']
ANSIBLE0017 ['[501]']
ANSIBLE0018 ['[101]']
ANSIBLE0019 ['[102]']
behaviour ['[503]']
bug ['[304]']
command-shell ['[301]', '[302]', '[303]', '[304]', '[306]', '[305]']
deprecated ['[101]', '[105]', '[102]', '[103]', '[104]']
formatting ['[204]', '[203]', '[202]', '[205]', '[201]', '[104]', '[206]']
idempotency ['[301]']
idiom ['[602]', '[601]']
metadata ['[703]', '[701]', '[702]', '[704]']
module ['[401]', '[402]', '[403]', '[404]']
oddity ['[501]']
readability ['[502]']
repeatability ['[401]', '[402]', '[403]']
resources ['[302]', '[303]']
safety ['[305]']
task ['[501]', '[502]', '[504]', '[503]']
```

只检测一个标记规则

```bash
ansible-lint -t idempotency playbook.yml
```

排除规则

```bash
ansible-lint -x readability,safety playbook.yml
```

也可以指定规则id

```bash
ansible-lint -x ANSIBLE0011 playbook.yml
```

### 跳过规则

如果想在任务上跳过检查规则，可在行内末尾加上` # noqa [rule_id] ` 即可跳过对应的规则。

```yaml
- name: this would typically fire GitHasVersionRule 401 and BecomeUserWithoutBecomeRule 501
  become_user: alice  # noqa 401 501
  git: src=/path/to/git/repo dest=checkout
  
- name: this would typically fire LineTooLongRule 204 and VariableHasSpacesRule 206
  get_url:
    url: http://example.com/really_long_path/really_long_path/really_long_path/really_long_path/really_long_path/really_long_path/file.conf  # noqa 204
    dest: "{{dest_proj_path}}/foo.conf"  # noqa 206
```

使用命令行选项跳过

```bash
ansible-lint -x readability,safety playbook.yml
```

在配置文件中跳过

```yaml
skip_list:
  - skip_this_tag
  - and_this_one_too
  - skip_this_id
  - '401'
```

