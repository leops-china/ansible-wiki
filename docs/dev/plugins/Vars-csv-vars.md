# vars plugins: csv_vars

## 需求

将 csv 中的数据解析为主机变量

csv 文件示例

```csv
hostname,gateway,vlan30,vlan40,vlan50,vlan60,vlan70
localhost,192.168.30.254,192.168.30.31,192.168.40.31,192.168.50.31,192.168.60.31,192.168.70.31
```

- 将 csv 文件放在 `inventory` 或 `playbook` 下的`csv_vars`目录中，就会被自动解析。
- csv 中的 `hostname` 字段要与 `inventory` 的主机名称一致。
- 建议将 csv 命名为 <GROUP_OR_HOST_NAME>.csv，支持多个 csv 文件，并且支持变量覆盖。

## 编写插件

文件路径 `vars_plugins/csv_vars.py`

```bash
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Copyright 2019 Zijian Guo <guozijian@unitedstack.com>, <guozijn@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

from __future__ import print_function

DOCUMENTATION = '''
    vars: csv_vars
    short_description: Parsing vars from csv file
    description:
        - Load YAML variable into ansible host corresponding to "hostname" in csv_vars/servers.csv file.
    options:
      _valid_extensions:
        default: [".csv"]
'''

from ansible.errors import AnsibleParserError
from ansible.inventory.group import Group
from ansible.inventory.host import Host
from ansible.module_utils._text import to_bytes
from ansible.module_utils._text import to_native
from ansible.plugins.vars import BaseVarsPlugin
from ansible.utils.vars import combine_vars
import csv
import os
import yaml

FOUND = {}


def load_from_csv(file_name):
    with open(file_name, 'r') as csv_data:
        reader = csv.DictReader(csv_data)
        out = yaml.safe_dump([row for row in reader])
    return yaml.safe_load(out)


class VarsModule(BaseVarsPlugin):

    def get_vars(self, loader, path, entities, cache=True):
        '''parses the csv file'''
        if not isinstance(entities, list):
            entities = [entities]

        super(VarsModule, self).get_vars(loader, path, entities)

        data = {}
        for entity in entities:
            if isinstance(entity, Host):
                subdir = 'csv_vars'
            elif isinstance(entity, Group):
                continue
            else:
                raise AnsibleParserError(
                    "Supplied entity must be Host or got %s instead"
                    % (type(entity))
                )

            # avoid 'chroot' type inventory hostnames /path/to/chroot
            if not entity.name.startswith(os.path.sep):
                try:
                    found_files = []
                    # load vars
                    opath = os.path.realpath(os.path.join(self._basedir, subdir))
                    key = '%s.%s' % (entity.name, opath)
                    if cache and key in FOUND:
                        found_files = FOUND[key]
                    else:
                        b_opath = to_bytes(opath)
                        # no need to do much if path does not exist for basedir
                        if os.path.exists(b_opath):
                            if os.path.isdir(b_opath):
                                self._display.debug("\tprocessing dir %s" % opath)
                                found_files = loader.find_vars_files(
                                    opath,
                                    'nodes',
                                    ['.csv']
                                )
                                FOUND[key] = found_files
                            else:
                                self._display.warning(
                                    "Found %s that is not a directory, \
                                    skipping: %s" % (subdir, opath)
                                )
                    for found in found_files:
                        new_data = load_from_csv(found)
                        for row_data in new_data:
                            if row_data['hostname'] == entity.name:
                                data = combine_vars(data, row_data)

                except Exception as e:
                    raise AnsibleParserError(to_native(e))
        return data
```
> 代码来自 https://github.com/guozijn/csv_vars


## csv 文件

将 csv 文件放在 inventory 或 playbook 下的`csv_vars`目录中

```bash
mdkir csv_vars
cat << EOF >> csv_vars/nodes.csv
hostname,gateway,vlan30,vlan40,vlan50,vlan60,vlan70
192.168.77.130,192.168.30.254,192.168.30.31,192.168.40.31,192.168.50.31,192.168.60.31,192.168.70.31
EOF
```

## 执行 playbook

```yaml
# cat test_vars.yml
- hosts: 192.168.77.130
  gather_facts: no
  tasks:
    - debug:
        msg: "{{ lookup('vars', item) }}"
      loop: "{{ hostvars[inventory_hostname].keys() | select('match', '^vlan.*$|gateway') | list }}"
```

执行结果

```bash
# ansible-playbook test_vars.yml

PLAY [192.168.77.130] ************************************************************************************************

TASK [debug] *********************************************************************************************************
ok: [192.168.77.130] => (item=gateway) => {
    "msg": "192.168.30.254"
}
ok: [192.168.77.130] => (item=vlan60) => {
    "msg": "192.168.60.31"
}
ok: [192.168.77.130] => (item=vlan30) => {
    "msg": "192.168.30.31"
}
ok: [192.168.77.130] => (item=vlan40) => {
    "msg": "192.168.40.31"
}
ok: [192.168.77.130] => (item=vlan70) => {
    "msg": "192.168.70.31"
}
ok: [192.168.77.130] => (item=vlan50) => {
    "msg": "192.168.50.31"
}

PLAY RECAP ***********************************************************************************************************
192.168.77.130             : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```

## 执行 ad-hoc

配置`ansible.cfg`,设置自定义的插件目录

```ini
[defaults]
vars_plugins       = /etc/ansible/vars_plugins
```

```bash
# ansible 192.168.77.130 -m debug -a 'var=gateway'
192.168.77.130 | SUCCESS => {
    "gateway": "192.168.30.254"
}

# ansible 192.168.77.130 -m debug -a 'var=vlan30'
192.168.77.130 | SUCCESS => {
    "vlan30": "192.168.30.31"
}
```

