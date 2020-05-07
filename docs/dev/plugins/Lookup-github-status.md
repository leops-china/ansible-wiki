# lookup plugins: github_status

## 需求

获取github项目分支的提交状态

## 编写插件

文件路径 `lookup_plugins/github_status.py`

```bash
from __future__ import (absolute_import, division, print_function)
__metaclass__ = type

DOCUMENTATION = """
    lookup: github_status
    author: lework
    version_added: historical
    short_description: return github repository branch status from list
    description:
      - this lookup get the commit status of the github repository branch
    options:
      _terms:
        description: list of github repository names
      branch:
        description: github repository branch name
"""

EXAMPLES = """
- name: look up github status for ansible
  debug:
    msg: "Current branch status is: {{ lookup('github_status', 'ansible/ansible', branch='devel') }}!"
"""

RETURN = """
_raw:
   description: repository branch state
"""

import json
from ansible.errors import AnsibleError
from ansible.module_utils.urls import open_url
from ansible.module_utils._text import to_text
from ansible.plugins.lookup import LookupBase
from ansible.utils.display import Display

display = Display()

class LookupModule(LookupBase):

    def run(self, terms, variables=None, **kwargs):
        ret = []

        for term in terms:
            display.debug("Github_status lookup term: %s" % term)
            branch = kwargs.get('branch', 'master')
            display.vv("Github_status lookup get [%s] repository [%s] branch status." % (term, branch))

            url = 'https://api.github.com/repos/{}/commits/{}/status'.format(term, branch)
            try:
                data = json.loads(open_url(url).read())
                ret.append(to_text(data['state']))
            except Exception as e:
                raise AnsibleError("lookup_plugin.github_status Get %s status error. %s" % (term, e))
        
        return ret
```

## 执行 playbook

```yaml
# cat test_lookup.yml
---
- name: look up github status for ansible
  hosts: localhost
  gather_facts: no
  tasks:
  - debug:
      msg: "Current branch status is: {{ lookup('github_status', 'ansible/ansible', branch='devel') }}!"
```

执行结果

```bash
# ansible-playbook test_lookup.yml

PLAY [look up github status for ansible] *****************************************************************************

TASK [debug] *********************************************************************************************************
ok: [localhost] => {
    "msg": "Current branch status is: success!"
}

PLAY RECAP ***********************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

## 执行 ad-hoc

配置`ansible.cfg`,设置自定义的插件目录

```ini
[defaults]
lookup_plugins     = /etc/ansible/lookup_plugins
```

```bash
ansible localhost -m debug -a "msg=\"Current branch status is: {{ lookup('github_status', 'ansible/ansible', branch='devel') }}\""
localhost | SUCCESS => {
    "msg": "Current branch status is: success"
}
```

