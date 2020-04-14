# 使用动态主机清单

如果你的 Ansible 主机清单随时间而变动，随着主机开启和关闭，以响应业务需求。那么静态配置的主机清单已经满足不了你的现状。 Ansible 支持两种方式来实现动态的主机清单: **Inventory** 插件和 **Inventory** 脚本。 

**Inventory** 插件是随着Ansible核心代码更新的最新代码。对于动态主机清单，我们建议使用 **Inventory 插件** 而不是脚本。您可以编写自己的插件来连接到其他动态主机清单源。 

## Inventory 插件

通过`ansible-doc`命令可列出当前可用的插件列表

```bash
# ansible-doc -t inventory -l 
nmap                Uses nmap to find hosts to target                                                                            
host_list           Parses a 'host list' string                                                                                  
hcloud              Ansible dynamic inventory plugin for the Hetzner Cloud                                                       
openstack           OpenStack inventory source                                                                                   
vultr               Vultr inventory source                                                                                       
aws_ec2             EC2 inventory source                                                                                         
cloudscale          cloudscale.ch inventory source                                                                               
virtualbox          virtualbox inventory source                                                                                  
constructed         Uses Jinja2 to construct vars and groups based on existing inventory                                         
k8s                 Kubernetes (K8s) inventory source                                                                            
generator           Uses Jinja2 to construct hosts and groups from patterns                                                      
script              Executes an inventory script that returns JSON                                                               
vmware_vm_inventory VMware Guest inventory source                                                                                
linode              Ansible dynamic inventory plugin for Linode                                                                  
docker_machine      Docker Machine inventory source                                                                              
yaml                Uses a specific YAML file as an inventory source                                                             
online              Online inventory source                                                                                      
azure_rm            Azure Resource Manager inventory plugin                                                                      
docker_swarm        Ansible dynamic inventory plugin for Docker swarm nodes                                                      
advanced_host_list  Parses a 'host list' with ranges                                                                             
foreman             foreman inventory source                                                                                     
auto                Loads and executes an inventory plugin specified in a YAML config                                            
kubevirt            KubeVirt inventory source                                                                                    
gitlab_runners      Ansible dynamic inventory plugin for GitLab runners                                                          
netbox              NetBox inventory source                                                                                      
gcp_compute         Google Cloud Compute Engine inventory source                                                                 
aws_rds             rds instance source                                                                                          
openshift           OpenShift inventory source                                                                                   
toml                Uses a specific TOML file as an inventory source                                                             
tower               Ansible dynamic inventory plugin for Ansible Tower                                                           
scaleway            Scaleway inventory source                                                                                    
ini                 Uses an Ansible INI file as inventory source       
```

!!! tips
    inventory 插件的文件默认存储在 `/lib/python2.7/site-packages/ansible/plugins/inventory/` 目录中。

## AWS EC2 动态清单

###  使用 **Inventory** 插件

#### 安装依赖

```bash
pip install boto3
```

#### 开启插件

大多数随Ansible自带的插件在默认情况下是禁用的，需要在你的`Ansible .cfg`文件中加入白名单才能正常运行。 

```ini
[inventory]
enable_plugins = aws_ec2
```

#### 配置插件

使用inventory插件时，需要配置一个yaml文件来描述使用的插件和插件选项。例如`aws_ec2` inventory插件必须以`aws_ec2.(yml|yaml)` 结尾创建一个文件。

```yaml
# hosts_aws_ec2.yml
plugin: aws_ec2
# aws
regions:
  - cn-north-1
# aws_profile: default
aws_access_key: 'aws_access_key_id'
aws_secrets_key: 'aws_secret_access_key'

# cache
cache: True
cache_plugin: jsonfile
cache_prefix: aws-ec2
cache_timeout: 7200
cache_connection: /tmp/aws_inventory

# 忽略403错误
strict_permissions: False

# 自定义组
keyed_groups:
  # Add e.g. x86_64 hosts to an arch_x86_64 group
  - prefix: arch
    key: 'architecture'
  # Add hosts to tag_Name_Value groups for each Name/Value tag pair
  - prefix: tag
    key: tags
  # Add hosts to e.g. instance_type_z3_tiny
  - prefix: instance_type
    key: instance_type
  # Create security_groups_sg_abcd1234 group for each SG
  - key: 'security_groups|json_query("[].group_id")'
    prefix: 'security_groups'
  # Create a group for each value of the Application tag
  - key: tags.Application
    separator: ''
  # Create a group per region e.g. aws_region_us_east_2
  - key: placement.region
    prefix: aws_region
  # Create a group (or groups) based on the value of a custom tag "Role" and add them to a metagroup called "project"
  - key: tags['Role']
    prefix: foo
    parent_group: "project"
    
# 主机名变量
hostnames:
  - tag:Name
  - ip-address
  - dns-name
  - private-ip-address

# 设置变量
compose:
  ansible_host: public_ip_address
  # ansible_ssh_user: root
  # ansible_ssh_pass: 123456
```

> aws_access_key 指定aws访问key，aws_secrets_key 指定aws访问秘钥, 更多参数见 [aws_ec2 插件帮助](https://docs.ansible.com/ansible/latest/plugins/inventory/aws_ec2.html)

#### 获取主机列表

```bash
ansible-inventory -i hosts_aws_ec2.yml --graph
```

#### 执行命令

```bash
ansible -i hosts_aws_ec2.yml tag_Env_test -m ping
```

> tag_Env_test 是包含`Env:test`标签的主机组。主机认证可使用ssh密钥认证，或者在`compose` 中指定连接用户和密码。

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列两种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f /tmp/aws_inventory/aws_ec2*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新

### 使用 **Inventory** 脚本

> 目前已不建议使用

使用  [EC2 external inventory]( https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.py )  外部脚本来获取AWS EC2主机的信息。

####  下载脚本

```bash
wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.py
wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.ini
chmod +x ec2.py
```

!!! note
	`ec2.py`脚本是使用Boto EC2库编写的，并将向AWS查询您正在运行的Amazon EC2实例。 
	`ec2.ini`文件是`ec2.py`的配置文件，可用于限制Ansible的访问范围。 

#### 安装依赖

```bash
pip install boto
```

#### 配置`ec2.ini`

```
[ec2]
regions = cn-north-1
regions_exclude =
destination_variable = public_dns_name
hostname_variable = tag_Name
vpc_destination_variable = ip_address
route53 = False
all_instances = False
all_rds_instances = False
include_rds_clusters = False
all_elasticache_replication_groups = False
all_elasticache_clusters = False
all_elasticache_nodes = False
cache_path = ~/.ansible/tmp
cache_max_age = 3600
nested_groups = False
replace_dash_in_groups = True
expand_csv_tags = False
group_by_instance_id = True
group_by_region = True
group_by_availability_zone = True
group_by_aws_account = False
group_by_ami_id = True
group_by_instance_type = True
group_by_instance_state = False
group_by_platform = True
group_by_key_pair = True
group_by_vpc_id = True
group_by_security_group = True
group_by_tag_keys = True
group_by_tag_none = True
group_by_route53_names = True
group_by_rds_engine = True
group_by_rds_parameter_group = True
group_by_elasticache_engine = True
group_by_elasticache_cluster = True
group_by_elasticache_parameter_group = True
group_by_elasticache_replication_group = True
stack_filters = False

[credentials]
aws_access_key_id = aws_access_key_id
aws_secret_access_key = aws_secret_access_key
```



#### 获取主机列表

```bash
./ec2.py --list
```

#### 执行命令

```bash
ansible -i ec2.py tag_Env_test -m ping
```

> tag_Env_test 是包含`Env:test`标签的主机组。主机认证可使用ssh密钥认证，或者在`compose` 中指定连接用户和密码。

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列三种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f /tmp/aws_inventory/aws_ec2*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新
3. 使用`./ec2.py --refresh-cache`命令来刷新



## Alicloud ECS 动态清单

###  使用 **Inventory** 插件

目前 `ansible_alicloud` 只支持在 `python3` 环境运行

#### 安装依赖

```bash
sudo pip install ansible_alicloud

# 目前安装包不包含inventory插件，需要单独下载
wget https://raw.githubusercontent.com/alibaba/ansible-provider/master/lib/ansible/plugins/inventory/alicloud_ecs.py -O /usr/lib/python2.7/site-packages/ansible/plugins/inventory/alicloud_ecs.py
```

#### 开启插件

大多数随Ansible自带的插件在默认情况下是禁用的，需要在你的`Ansible .cfg`文件中加入白名单才能正常运行。 

```ini
[inventory]
enable_plugins = alicloud_ecs
```

#### 配置插件

使用inventory插件时，需要配置一个yaml文件来描述使用的插件和插件选项。例如`aws_ec2` inventory插件必须以`alicloud.(yml|yaml)` 结尾创建一个文件。

```bash
plugin: alicloud_ecs
regions:
  - cn-beijing
  
alicloud_access_key: alicloud_access_key
alicloud_secret_key: alicloud_secret_key

hostnames:
  - public_ip_address
  
keyed_groups:
  # add hosts to instance_type groups
  - prefix: instance_type
    key: instance_type
  # add hosts to instance_name groups
  - key: instance_name
    prefix: name

cache: true
cache_plugin: jsonfile
cache_timeout: 7200
cache_connection: /tmp/alicloud_inventory
cache_prefix: alicloud_ecs

strict: true

compose:
  ansible_host: public_ip_address
```

#### 获取主机列表

```bash
ansible-inventory -i hosts_alicloud.yml --graph
```

#### 执行命令

```bash
ansible -i hosts_alicloud.yml tag_Env_test -m ping
```

> tag_Env_test 是包含`Env:test`标签的主机组。主机认证可使用ssh密钥认证，或者在`compose` 中指定连接用户和密码。

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列两种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f /tmp/alicloud_inventory/alicloud_ecs*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新

### 使用 **Inventory** 脚本

> 目前已不建议使用

使用 [ECS external inventory]( https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.py )  外部脚本来获取AWS EC2主机的信息。

#### 下载脚本

```bash
wget https://raw.githubusercontent.com/alibaba/ansible-provider/2c9a81bf3d5d3f3e049e06479e1972e61b92c02c/contrib/inventory/alicloud.py
wget https://raw.githubusercontent.com/alibaba/ansible-provider/2c9a81bf3d5d3f3e049e06479e1972e61b92c02c/contrib/inventory/alicloud.ini
chmod +x alicloud.py
```

> 脚本只支持在 `python3` 环境运行
>
> 如果要在python2中运行，需将configparser库引用修正下
>
> ```
> import sys
> if sys.version_info[0] == 2:
>     import ConfigParser as configparser
> else:
>     import configparser
> ```

#### 安装依赖

```bash
pip install configparser
```

#### 配置`alicloud.ini`

```
[ecs]
regions = all
destination_variable = public_ip_address
hostname_variable = instance_id
all_instances = True
cache_path = /tmp/alicloud_inventory/
cache_max_age = 7200
nested_groups = False
replace_dash_in_groups = True
expand_csv_tags = False
group_by_instance_id = True
group_by_region = True
group_by_availability_zone = True
group_by_image_id = True
group_by_instance_type = True
group_by_vpc_id = True
group_by_vswitch_id = True
group_by_security_group = True
group_by_tag_keys = True
group_by_tag_none = True

[credentials]
alicloud_access_key = alicloud_access_key
alicloud_secret_key = alicloud_secret_key
```

#### 获取主机列表

```bash
./alicloud.py --list
```

#### 执行命令

```bash
ansible -i alicloud.py tag_Env_test -m ping
```

> tag_Env_test 是包含`Env:test`标签的主机组。主机认证可使用ssh密钥认证，或者在`compose` 中指定连接用户和密码。

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列三种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f /tmp/alicloud_inventory/*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新s
3. 使用`./alicloud.py --refresh-cache`命令来刷新

## OpenStack 动态清单

### 使用 **Inventory** 插件

#### 安装依赖

新版本不支持`python2`环境了。

```bash
# python 2
pip install openstacksdk==0.39.0
# python 3
pip install openstacksdk 
```

#### 开启插件

大多数随Ansible自带的插件在默认情况下是禁用的，需要在你的`Ansible.cfg`文件中加入白名单才能正常运行。 

```ini
[inventory]
enable_plugins = openstack
```

#### 配置插件

使用inventory插件时，需要配置一个yaml文件来描述使用的插件和插件选项。例如`aws_ec2` inventory插件必须以`(openstack|cloud).(yml|yaml)` 结尾创建一个文件。

```bash
plugin: openstack
inventory_hostname: name
private: yes
fail_on_errors: yes
expand_hostvars: yes
cache: true
cache_plugin: jsonfile
cache_connection: /tmp/openstack-inventory
cache_prefix: openstack_host
keyed_groups:
  - prefix: ''
    key: openstack.metadata.vm_role
compose:
  cloud: "openstack"
```

#### Source OpenStack RC 文件

可在 OpenStack  WEB管理界面下载RC文件

```bash
export OS_AUTH_URL=http://hosts:5000/v3/
# With the addition of Keystone we have standardized on the term **project**
# as the entity that owns the resources.
export OS_PROJECT_ID=OS_PROJECT_ID
export OS_PROJECT_NAME="admin"
export OS_USER_DOMAIN_NAME="Default"
if [ -z "$OS_USER_DOMAIN_NAME" ]; then unset OS_USER_DOMAIN_NAME; fi
export OS_PROJECT_DOMAIN_ID="default"
if [ -z "$OS_PROJECT_DOMAIN_ID" ]; then unset OS_PROJECT_DOMAIN_ID; fi
export OS_USERNAME="admin"
read -sr OS_PASSWORD_INPUT
export OS_PASSWORD=$OS_PASSWORD_INPUT
export OS_REGION_NAME="RegionOne"
if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
export OS_INTERFACE=public
export OS_IDENTITY_API_VERSION=3
```

#### 获取主机列表

```bash
ansible-inventory -i hosts_openstack.yml --graph
```

#### 执行命令

```bash
ansible -i hosts_openstack.yml zone1 -m ping
```

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列两种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f /tmp/openstack_inventory/*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新

### 使用 **Inventory** 脚本

> 目前已不建议使用

使用  [ECS external inventory]( https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.py )  外部脚本来获取AWS EC2主机的信息。

#### 下载脚本

```bash
wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/openstack_inventory.py
wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/openstack.yml -O /etc/ansible/openstack.yml
chmod +x openstack_inventory.py
```

#### 安装依赖

```bash
# python 2
pip install openstacksdk==0.39.0
# python 3
pip install openstacksdk 
```

#### 配置`openstack.yml`

配置文件需放置在`/etc/ansible/openstack.yml` 

```yaml
clouds:
  defaults:
    auth:
      auth_url: http://hosts:5000/v3/
      password: password
      project_domain_id: default
      project_name: admin
      user_domain_id: default
      username: admin
    identity_api_version: '3'
    region_name: RegionOne
    volume_api_version: '2'
ansible:
  use_hostnames: True
  expand_hostvars: False
  fail_on_errors: True
```

#### 获取主机列表

```bash
./openstack_inventory.py --list
```

#### 执行命令

```bash
ansible -i openstack_inventory.py zone3 -m ping
```

#### 刷新 **Inventory**  Cache

在指定了`cache: True`时，Inventory信息会存在一定的时间，如果想获取最新的数据，可使用下列三种方式

1. 手动的删除缓存信息, 比如删除缓存文件`rm -f ~/.cache/openstack/ansible-inventory.cache*`
2. 使用 `ansible-playbook --flush-cache ` 命令来刷新s
3. 使用`./openstack_inventory.py --refresh-cache`命令来刷新

