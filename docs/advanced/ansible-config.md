# Ansible 的常用设置


## ansible.cfg

下列列出了常用的一些设置，可用作参考。

```ini
# /etc/ansible/ansible.cfg

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

ansible_managed = Ansible managed: {file} modified by {uid} on {host}

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