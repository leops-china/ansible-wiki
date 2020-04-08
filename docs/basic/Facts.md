# 11. Facts 数据

Facts主要是用来采集目标系统信息的，采集到信息存储在`ansible_facts`变量中，也有许多信息存储在以`ansible_`开头的变量。

 

## 获取Facts信息

### 使用setup模块来获取目标系统信息

可以使用`setup`模块手动的获取目标系统信息

```bash
ansible hostname -m setup
```

向`setup`模块传递`filter`选项，就可以选择获取哪些内容，例如仅显示与ansible相关的内存信息

```bash
ansible all -m setup -a 'filter=ansible_*_mb'
```

### 使用playbook来获取目标系统信息

默认情况下，playbook的第一个任务就是`Facts`信息，显示的结果如下:

```yaml
PLAY [192.168.77.130] ******************************************
TASK [Gathering Facts] ****************************************************************
ok: [192.168.77.130]
TASK [test] ****************************************************
changed: [192.168.77.130]
```

如果要关闭playbook的这一操作，就需要为play添加`gather_facts`关键字

```yaml
# 关闭关闭自动采集Facts
- hosts: whatever
  gather_facts: no
```

默认情况下，是收集所有的facts信息，可以通过修改ansible配置文件来达到只获取某一类型的信息

```ini
# /etc/ansible/ansible.cfg

# all - 收集所有子集，默认
# network - 收集网络信息子集
# hardware - 收集硬件信息子集
# virtual - 收集虚拟相关的信息
# facter - 收集自定义的fact信息
# ohai -  收集ohai信息
# 可以使用多个子集 (ex: network,virtual)
# 可以排除子集 (ex: !hardware,!facter,!ohai)
gather_subset = all
```



### 在task中设置facts信息

可以使用`set_fact` 来设置当前运行主机的facts信息

```yaml
- hosts: hostname
  tasks:
    - command: whoami
      register: result
    - set_fact:
        one: "{{ result.stdout }}"
        two: true
    - debug: var=one
    - debug: var=two
```

### 自定义目标系统facts

在远程主机/etc/ansible/facts.d/目录下创建.fact 结尾的文件，也可以是json、ini 或者返回json 格式数据的可执行文件，这些将被作为远程主机本地的facts 执行

 **在远程主机上操作**

```bash
mkdir -p /etc/ansible/facts.d
cat << EOF > /etc/ansible/facts.d/hello.fact
[test]
h=hello
p=world
EOF
```

**在ansible控制节点上操作**

远程主机的自定义facts信息，存储在`ansible_local`变量中，可以通过`setup`模块过滤获取

```bash
ansible 192.168.77.130 -m setup -a "filter=ansible_local" 
192.168.77.130 | SUCCESS => {
    "ansible_facts": {
        "ansible_local": {
            "hello": {
                "test": {
                    "h": "hello", 
                    "p": "world"
                }
            }
        }, 
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false
}
```

也可以通过在任务中使用`{{ ansible_local.hello }}`的方式访问该变量

```bash
---
- hosts: 192.168.77.130
  tasks:
    - debug: var=ansible_local.hello
    - debug: var=ansible_local.hello.test.h
```



当然，我们可以把上面的步骤，通过playbook来实现

>  运用playbook 定义远端facts.d，并加载到fact中

```yaml
- hosts: node1
  tasks:
     - name: create directory for ansible custom facts
       file: state=directory recurse=yes path=/etc/ansible/facts.d
     - name: install custom test fact
       copy:
         content: |
           [test]
           h=hello
           p=world
         dest: /etc/ansible/facts.d/test.fact
     - name: re-read facts after adding custom fact
       setup: filter=ansible_local
     - name: ansible_local vars
       debug: var=ansible_local
```

### Facts 返回的信息

以`ansible 2.9.1`版本返回`centos 7`系统的Facts信息

```json
"ansible_facts": {
    "ansible_all_ipv4_addresses": [
        "192.168.77.130", 
        "172.17.0.1"
    ], 
    "ansible_all_ipv6_addresses": [
        "fe80::6d73:3667:2ed6:a7c2", 
        "fe80::4d03:8744:2f0d:2085"
    ], 
    "ansible_apparmor": {
        "status": "disabled"
    }, 
    "ansible_architecture": "x86_64", 
    "ansible_bios_date": "07/29/2019", 
    "ansible_bios_version": "6.00", 
    "ansible_cmdline": {
        "BOOT_IMAGE": "/vmlinuz-5.1.11-1.el7.elrepo.x86_64", 
        "crashkernel": "auto", 
        "quiet": true, 
        "rhgb": true, 
        "ro": true, 
        "root": "UUID=a7d49533-e756-4a71-a977-5efb174eb09c", 
        "user_namespace.enable": "1"
    }, 
    "ansible_date_time": {
        "date": "2020-03-31", 
        "day": "31", 
        "epoch": "1585627320", 
        "hour": "12", 
        "iso8601": "2020-03-31T04:02:00Z", 
        "iso8601_basic": "20200331T120200260891", 
        "iso8601_basic_short": "20200331T120200", 
        "iso8601_micro": "2020-03-31T04:02:00.260966Z", 
        "minute": "02", 
        "month": "03", 
        "second": "00", 
        "time": "12:02:00", 
        "tz": "CST", 
        "tz_offset": "+0800", 
        "weekday": "星期二", 
        "weekday_number": "2", 
        "weeknumber": "13", 
        "year": "2020"
    }, 
    "ansible_default_ipv4": {
        "address": "192.168.77.130", 
        "alias": "ens33", 
        "broadcast": "192.168.77.255", 
        "gateway": "192.168.77.2", 
        "interface": "ens33", 
        "macaddress": "00:0c:29:88:01:c0", 
        "mtu": 1500, 
        "netmask": "255.255.255.0", 
        "network": "192.168.77.0", 
        "type": "ether"
    }, 
    "ansible_default_ipv6": {}, 
    "ansible_device_links": {
        "ids": {
            "sr0": [
                "ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001"
            ]
        }, 
        "labels": {}, 
        "masters": {}, 
        "uuids": {
            "sda1": [
                "93556f71-6dad-4761-9207-edee35d47129"
            ], 
            "sda2": [
                "0c0f8a5a-58dd-4fc6-a49e-fc5e63f5d8a3"
            ], 
            "sda3": [
                "a7d49533-e756-4a71-a977-5efb174eb09c"
            ]
        }
    }, 
    "ansible_devices": {
        "sda": {
            "holders": [], 
            "host": "SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)", 
            "links": {
                "ids": [], 
                "labels": [], 
                "masters": [], 
                "uuids": []
            }, 
            "model": "VMware Virtual S", 
            "partitions": {
                "sda1": {
                    "holders": [], 
                    "links": {
                        "ids": [], 
                        "labels": [], 
                        "masters": [], 
                        "uuids": [
                            "93556f71-6dad-4761-9207-edee35d47129"
                        ]
                    }, 
                    "sectors": "409600", 
                    "sectorsize": 512, 
                    "size": "200.00 MB", 
                    "start": "2048", 
                    "uuid": "93556f71-6dad-4761-9207-edee35d47129"
                }, 
                "sda2": {
                    "holders": [], 
                    "links": {
                        "ids": [], 
                        "labels": [], 
                        "masters": [], 
                        "uuids": [
                            "0c0f8a5a-58dd-4fc6-a49e-fc5e63f5d8a3"
                        ]
                    }, 
                    "sectors": "20971520", 
                    "sectorsize": 512, 
                    "size": "10.00 GB", 
                    "start": "411648", 
                    "uuid": "0c0f8a5a-58dd-4fc6-a49e-fc5e63f5d8a3"
                }, 
                "sda3": {
                    "holders": [], 
                    "links": {
                        "ids": [], 
                        "labels": [], 
                        "masters": [], 
                        "uuids": [
                            "a7d49533-e756-4a71-a977-5efb174eb09c"
                        ]
                    }, 
                    "sectors": "62502912", 
                    "sectorsize": 512, 
                    "size": "29.80 GB", 
                    "start": "21383168", 
                    "uuid": "a7d49533-e756-4a71-a977-5efb174eb09c"
                }
            }, 
            "removable": "0", 
            "rotational": "1", 
            "sas_address": null, 
            "sas_device_handle": null, 
            "scheduler_mode": "mq-deadline", 
            "sectors": "83886080", 
            "sectorsize": "512", 
            "size": "40.00 GB", 
            "support_discard": "0", 
            "vendor": "VMware,", 
            "virtual": 1
        }, 
        "sr0": {
            "holders": [], 
            "host": "IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)", 
            "links": {
                "ids": [
                    "ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001"
                ], 
                "labels": [], 
                "masters": [], 
                "uuids": []
            }, 
            "model": "VMware IDE CDR10", 
            "partitions": {}, 
            "removable": "1", 
            "rotational": "1", 
            "sas_address": null, 
            "sas_device_handle": null, 
            "scheduler_mode": "mq-deadline", 
            "sectors": "2097151", 
            "sectorsize": "512", 
            "size": "1024.00 MB", 
            "support_discard": "0", 
            "vendor": "NECVMWar", 
            "virtual": 1
        }
    }, 
    "ansible_distribution": "CentOS", 
    "ansible_distribution_file_parsed": true, 
    "ansible_distribution_file_path": "/etc/redhat-release", 
    "ansible_distribution_file_variety": "RedHat", 
    "ansible_distribution_major_version": "7", 
    "ansible_distribution_release": "Core", 
    "ansible_distribution_version": "7.6", 
    "ansible_dns": {
        "nameservers": [
            "192.168.77.2"
        ]
    }, 
    "ansible_docker0": {
        "active": false, 
        "device": "docker0", 
        "features": {
            "esp_hw_offload": "off [fixed]", 
            "esp_tx_csum_hw_offload": "off [fixed]", 
            "fcoe_mtu": "off [fixed]", 
            "generic_receive_offload": "on", 
            "generic_segmentation_offload": "on", 
            "highdma": "on", 
            "hw_tc_offload": "off [fixed]", 
            "l2_fwd_offload": "off [fixed]", 
            "large_receive_offload": "off [fixed]", 
            "loopback": "off [fixed]", 
            "netns_local": "on [fixed]", 
            "ntuple_filters": "off [fixed]", 
            "receive_hashing": "off [fixed]", 
            "rx_all": "off [fixed]", 
            "rx_checksumming": "off [fixed]", 
            "rx_fcs": "off [fixed]", 
            "rx_gro_hw": "off [fixed]", 
            "rx_udp_tunnel_port_offload": "off [fixed]", 
            "rx_vlan_filter": "off [fixed]", 
            "rx_vlan_offload": "off [fixed]", 
            "rx_vlan_stag_filter": "off [fixed]", 
            "rx_vlan_stag_hw_parse": "off [fixed]", 
            "scatter_gather": "on", 
            "tcp_segmentation_offload": "on", 
            "tls_hw_record": "off [fixed]", 
            "tls_hw_rx_offload": "off [fixed]", 
            "tls_hw_tx_offload": "off [fixed]", 
            "tx_checksum_fcoe_crc": "off [fixed]", 
            "tx_checksum_ip_generic": "on", 
            "tx_checksum_ipv4": "off [fixed]", 
            "tx_checksum_ipv6": "off [fixed]", 
            "tx_checksum_sctp": "off [fixed]", 
            "tx_checksumming": "on", 
            "tx_esp_segmentation": "on", 
            "tx_fcoe_segmentation": "on", 
            "tx_gre_csum_segmentation": "on", 
            "tx_gre_segmentation": "on", 
            "tx_gso_partial": "on", 
            "tx_gso_robust": "on", 
            "tx_ipxip4_segmentation": "on", 
            "tx_ipxip6_segmentation": "on", 
            "tx_lockless": "on [fixed]", 
            "tx_nocache_copy": "off", 
            "tx_scatter_gather": "on", 
            "tx_scatter_gather_fraglist": "on", 
            "tx_sctp_segmentation": "on", 
            "tx_tcp6_segmentation": "on", 
            "tx_tcp_ecn_segmentation": "on", 
            "tx_tcp_mangleid_segmentation": "on", 
            "tx_tcp_segmentation": "on", 
            "tx_udp_segmentation": "on", 
            "tx_udp_tnl_csum_segmentation": "on", 
            "tx_udp_tnl_segmentation": "on", 
            "tx_vlan_offload": "on", 
            "tx_vlan_stag_hw_insert": "on", 
            "udp_fragmentation_offload": "off", 
            "vlan_challenged": "off [fixed]"
        }, 
        "hw_timestamp_filters": [], 
        "id": "8000.024238d96cf4", 
        "interfaces": [], 
        "ipv4": {
            "address": "172.17.0.1", 
            "broadcast": "172.17.255.255", 
            "netmask": "255.255.0.0", 
            "network": "172.17.0.0"
        }, 
        "macaddress": "02:42:38:d9:6c:f4", 
        "mtu": 1500, 
        "promisc": false, 
        "stp": false, 
        "timestamping": [
            "rx_software", 
            "software"
        ], 
        "type": "bridge"
    }, 
    "ansible_domain": "", 
    "ansible_effective_group_id": 0, 
    "ansible_effective_user_id": 0, 
    "ansible_ens33": {
        "active": true, 
        "device": "ens33", 
        "features": {
            "esp_hw_offload": "off [fixed]", 
            "esp_tx_csum_hw_offload": "off [fixed]", 
            "fcoe_mtu": "off [fixed]", 
            "generic_receive_offload": "on", 
            "generic_segmentation_offload": "on", 
            "highdma": "off [fixed]", 
            "hw_tc_offload": "off [fixed]", 
            "l2_fwd_offload": "off [fixed]", 
            "large_receive_offload": "off [fixed]", 
            "loopback": "off [fixed]", 
            "netns_local": "off [fixed]", 
            "ntuple_filters": "off [fixed]", 
            "receive_hashing": "off [fixed]", 
            "rx_all": "off", 
            "rx_checksumming": "off", 
            "rx_fcs": "off", 
            "rx_gro_hw": "off [fixed]", 
            "rx_udp_tunnel_port_offload": "off [fixed]", 
            "rx_vlan_filter": "on [fixed]", 
            "rx_vlan_offload": "on", 
            "rx_vlan_stag_filter": "off [fixed]", 
            "rx_vlan_stag_hw_parse": "off [fixed]", 
            "scatter_gather": "on", 
            "tcp_segmentation_offload": "on", 
            "tls_hw_record": "off [fixed]", 
            "tls_hw_rx_offload": "off [fixed]", 
            "tls_hw_tx_offload": "off [fixed]", 
            "tx_checksum_fcoe_crc": "off [fixed]", 
            "tx_checksum_ip_generic": "on", 
            "tx_checksum_ipv4": "off [fixed]", 
            "tx_checksum_ipv6": "off [fixed]", 
            "tx_checksum_sctp": "off [fixed]", 
            "tx_checksumming": "on", 
            "tx_esp_segmentation": "off [fixed]", 
            "tx_fcoe_segmentation": "off [fixed]", 
            "tx_gre_csum_segmentation": "off [fixed]", 
            "tx_gre_segmentation": "off [fixed]", 
            "tx_gso_partial": "off [fixed]", 
            "tx_gso_robust": "off [fixed]", 
            "tx_ipxip4_segmentation": "off [fixed]", 
            "tx_ipxip6_segmentation": "off [fixed]", 
            "tx_lockless": "off [fixed]", 
            "tx_nocache_copy": "off", 
            "tx_scatter_gather": "on", 
            "tx_scatter_gather_fraglist": "off [fixed]", 
            "tx_sctp_segmentation": "off [fixed]", 
            "tx_tcp6_segmentation": "off [fixed]", 
            "tx_tcp_ecn_segmentation": "off [fixed]", 
            "tx_tcp_mangleid_segmentation": "off", 
            "tx_tcp_segmentation": "on", 
            "tx_udp_segmentation": "off [fixed]", 
            "tx_udp_tnl_csum_segmentation": "off [fixed]", 
            "tx_udp_tnl_segmentation": "off [fixed]", 
            "tx_vlan_offload": "on [fixed]", 
            "tx_vlan_stag_hw_insert": "off [fixed]", 
            "udp_fragmentation_offload": "off", 
            "vlan_challenged": "off [fixed]"
        }, 
        "hw_timestamp_filters": [], 
        "ipv4": {
            "address": "192.168.77.130", 
            "broadcast": "192.168.77.255", 
            "netmask": "255.255.255.0", 
            "network": "192.168.77.0"
        }, 
        "ipv6": [
            {
                "address": "fe80::6d73:3667:2ed6:a7c2", 
                "prefix": "64", 
                "scope": "link"
            }, 
            {
                "address": "fe80::4d03:8744:2f0d:2085", 
                "prefix": "64", 
                "scope": "link"
            }
        ], 
        "macaddress": "00:0c:29:88:01:c0", 
        "module": "e1000", 
        "mtu": 1500, 
        "pciid": "0000:02:01.0", 
        "promisc": false, 
        "speed": 1000, 
        "timestamping": [
            "tx_software", 
            "rx_software", 
            "software"
        ], 
        "type": "ether"
    }, 
    "ansible_env": {
        "HOME": "/root", 
        "LANG": "zh_CN.UTF-8", 
        "LESSOPEN": "||/usr/bin/lesspipe.sh %s", 
        "LOGNAME": "root", 
        "LS_COLORS": "rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=01;05;37;41:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=01;36:*.au=01;36:*.flac=01;36:*.mid=01;36:*.midi=01;36:*.mka=01;36:*.mp3=01;36:*.mpc=01;36:*.ogg=01;36:*.ra=01;36:*.wav=01;36:*.axa=01;36:*.oga=01;36:*.spx=01;36:*.xspf=01;36:", 
        "MAIL": "/var/mail/root", 
        "PATH": "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin", 
        "PWD": "/root", 
        "SHELL": "/bin/bash", 
        "SHLVL": "2", 
        "SSH_CLIENT": "192.168.77.128 46964 22", 
        "SSH_CONNECTION": "192.168.77.128 46964 192.168.77.130 22", 
        "SSH_TTY": "/dev/pts/1", 
        "TERM": "linux", 
        "USER": "root", 
        "XDG_RUNTIME_DIR": "/run/user/0", 
        "XDG_SESSION_ID": "22", 
        "_": "/usr/bin/python"
    }, 
    "ansible_fibre_channel_wwn": [], 
    "ansible_fips": false, 
    "ansible_form_factor": "Other", 
    "ansible_fqdn": "node130", 
    "ansible_hostname": "node130", 
    "ansible_hostnqn": "", 
    "ansible_interfaces": [
        "lo", 
        "docker0", 
        "ens33"
    ], 
    "ansible_is_chroot": false, 
    "ansible_iscsi_iqn": "", 
    "ansible_kernel": "5.1.11-1.el7.elrepo.x86_64", 
    "ansible_kernel_version": "#1 SMP Mon Jun 17 15:51:08 EDT 2019", 
    "ansible_lo": {
        "active": true, 
        "device": "lo", 
        "features": {
            "esp_hw_offload": "off [fixed]", 
            "esp_tx_csum_hw_offload": "off [fixed]", 
            "fcoe_mtu": "off [fixed]", 
            "generic_receive_offload": "on", 
            "generic_segmentation_offload": "on", 
            "highdma": "on [fixed]", 
            "hw_tc_offload": "off [fixed]", 
            "l2_fwd_offload": "off [fixed]", 
            "large_receive_offload": "off [fixed]", 
            "loopback": "on [fixed]", 
            "netns_local": "on [fixed]", 
            "ntuple_filters": "off [fixed]", 
            "receive_hashing": "off [fixed]", 
            "rx_all": "off [fixed]", 
            "rx_checksumming": "on [fixed]", 
            "rx_fcs": "off [fixed]", 
            "rx_gro_hw": "off [fixed]", 
            "rx_udp_tunnel_port_offload": "off [fixed]", 
            "rx_vlan_filter": "off [fixed]", 
            "rx_vlan_offload": "off [fixed]", 
            "rx_vlan_stag_filter": "off [fixed]", 
            "rx_vlan_stag_hw_parse": "off [fixed]", 
            "scatter_gather": "on", 
            "tcp_segmentation_offload": "on", 
            "tls_hw_record": "off [fixed]", 
            "tls_hw_rx_offload": "off [fixed]", 
            "tls_hw_tx_offload": "off [fixed]", 
            "tx_checksum_fcoe_crc": "off [fixed]", 
            "tx_checksum_ip_generic": "on [fixed]", 
            "tx_checksum_ipv4": "off [fixed]", 
            "tx_checksum_ipv6": "off [fixed]", 
            "tx_checksum_sctp": "on [fixed]", 
            "tx_checksumming": "on", 
            "tx_esp_segmentation": "off [fixed]", 
            "tx_fcoe_segmentation": "off [fixed]", 
            "tx_gre_csum_segmentation": "off [fixed]", 
            "tx_gre_segmentation": "off [fixed]", 
            "tx_gso_partial": "off [fixed]", 
            "tx_gso_robust": "off [fixed]", 
            "tx_ipxip4_segmentation": "off [fixed]", 
            "tx_ipxip6_segmentation": "off [fixed]", 
            "tx_lockless": "on [fixed]", 
            "tx_nocache_copy": "off [fixed]", 
            "tx_scatter_gather": "on [fixed]", 
            "tx_scatter_gather_fraglist": "on [fixed]", 
            "tx_sctp_segmentation": "on", 
            "tx_tcp6_segmentation": "on", 
            "tx_tcp_ecn_segmentation": "on", 
            "tx_tcp_mangleid_segmentation": "on", 
            "tx_tcp_segmentation": "on", 
            "tx_udp_segmentation": "off [fixed]", 
            "tx_udp_tnl_csum_segmentation": "off [fixed]", 
            "tx_udp_tnl_segmentation": "off [fixed]", 
            "tx_vlan_offload": "off [fixed]", 
            "tx_vlan_stag_hw_insert": "off [fixed]", 
            "udp_fragmentation_offload": "off", 
            "vlan_challenged": "on [fixed]"
        }, 
        "hw_timestamp_filters": [], 
        "ipv4": {
            "address": "127.0.0.1", 
            "broadcast": "host", 
            "netmask": "255.0.0.0", 
            "network": "127.0.0.0"
        }, 
        "ipv6": [
            {
                "address": "::1", 
                "prefix": "128", 
                "scope": "host"
            }
        ], 
        "mtu": 65536, 
        "promisc": false, 
        "timestamping": [
            "tx_software", 
            "rx_software", 
            "software"
        ], 
        "type": "loopback"
    }, 
    "ansible_local": {
        "hello": {
            "test": {
                "h": "hello", 
                "p": "world"
            }
        }, 
        "test": {
            "test": {
                "h": "hello", 
                "p": "world"
            }
        }
    }, 
    "ansible_lsb": {}, 
    "ansible_machine": "x86_64", 
    "ansible_machine_id": "c6e2cb0cdbad41f19c30d690896aabe0", 
    "ansible_memfree_mb": 476, 
    "ansible_memory_mb": {
        "nocache": {
            "free": 695, 
            "used": 265
        }, 
        "real": {
            "free": 476, 
            "total": 960, 
            "used": 484
        }, 
        "swap": {
            "cached": 0, 
            "free": 10239, 
            "total": 10239, 
            "used": 0
        }
    }, 
    "ansible_memtotal_mb": 960, 
    "ansible_mounts": [
        {
            "block_available": 10389, 
            "block_size": 4096, 
            "block_total": 50345, 
            "block_used": 39956, 
            "device": "/dev/sda1", 
            "fstype": "xfs", 
            "inode_available": 83285, 
            "inode_total": 83624, 
            "inode_used": 339, 
            "mount": "/boot", 
            "options": "rw,relatime,attr2,inode64,noquota", 
            "size_available": 42553344, 
            "size_total": 206213120, 
            "uuid": "93556f71-6dad-4761-9207-edee35d47129"
        }, 
        {
            "block_available": 7234718, 
            "block_size": 4096, 
            "block_total": 7809050, 
            "block_used": 574332, 
            "device": "/dev/sda3", 
            "fstype": "xfs", 
            "inode_available": 15558107, 
            "inode_total": 15625728, 
            "inode_used": 67621, 
            "mount": "/", 
            "options": "rw,relatime,attr2,inode64,noquota", 
            "size_available": 29633404928, 
            "size_total": 31985868800, 
            "uuid": "a7d49533-e756-4a71-a977-5efb174eb09c"
        }
    ], 
    "ansible_nodename": "node130", 
    "ansible_os_family": "RedHat", 
    "ansible_pkg_mgr": "yum", 
    "ansible_proc_cmdline": {
        "BOOT_IMAGE": "/vmlinuz-5.1.11-1.el7.elrepo.x86_64", 
        "crashkernel": "auto", 
        "quiet": true, 
        "rhgb": true, 
        "ro": true, 
        "root": "UUID=a7d49533-e756-4a71-a977-5efb174eb09c", 
        "user_namespace.enable": "1"
    }, 
    "ansible_processor": [
        "0", 
        "GenuineIntel", 
        "Intel(R) Core(TM) i3-4160 CPU @ 3.60GHz"
    ], 
    "ansible_processor_cores": 1, 
    "ansible_processor_count": 1, 
    "ansible_processor_threads_per_core": 1, 
    "ansible_processor_vcpus": 1, 
    "ansible_product_name": "VMware Virtual Platform", 
    "ansible_product_serial": "VMware-56 4d 4b f0 c3 97 be 18-aa c9 56 08 cb 88 01 c0", 
    "ansible_product_uuid": "f04b4d56-97c3-18be-aac9-5608cb8801c0", 
    "ansible_product_version": "None", 
    "ansible_python": {
        "executable": "/usr/bin/python", 
        "has_sslcontext": true, 
        "type": "CPython", 
        "version": {
            "major": 2, 
            "micro": 5, 
            "minor": 7, 
            "releaselevel": "final", 
            "serial": 0
        }, 
        "version_info": [
            2, 
            7, 
            5, 
            "final", 
            0
        ]
    }, 
    "ansible_python_version": "2.7.5", 
    "ansible_real_group_id": 0, 
    "ansible_real_user_id": 0, 
    "ansible_selinux": {
        "status": "disabled"
    }, 
    "ansible_selinux_python_present": true, 
    "ansible_service_mgr": "systemd", 
    "ansible_ssh_host_key_ecdsa_public": "AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBK2zovckFKduH7EsvGaWar2mA+LdC4kTjgFG4h9RQlxZ1v5kEPx8Bs7jWnj94Cd8lY8BGb7RU7akUFpq3V59WIY=", 
    "ansible_ssh_host_key_ed25519_public": "AAAAC3NzaC1lZDI1NTE5AAAAIEgM8JK59UtnryS0IhtNoPJHbOSqy7Xy2jExPYMvAex5", 
    "ansible_ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQDfNgNsUWXmYOD7Iz94nO98XRmw4dWKREbxWz6rZBP2QHYFN38nzdo9h5UT4HMuUM/FraPwwbfPubznNgn0/cXfMkqu8JIssxizpIRBZv82HFqwHTYRvkFAEII8ftkHs2RVlq64+ljPZzWvGL14nkfU7P+kc8Ym4jZGtorKRBoHFCeu67fycmZSCLFJxkKSumOaZ9TbNzP6bziyfmdDIGfj8UgzJRSuBW+B5XNeJp/QtsQZTjgpxSZZ9QRf/FeRx1NDR5Si91Fkd0NILIgoOSz536lP+aCCUOx7ukaoV1T/kyUKOj8a3wpBGiBWWZUGZa6O02Ig0eHnx8F4lZ2iOnNN", 
    "ansible_swapfree_mb": 10239, 
    "ansible_swaptotal_mb": 10239, 
    "ansible_system": "Linux", 
    "ansible_system_capabilities": [
        "cap_chown", 
        "cap_dac_override", 
        "cap_dac_read_search", 
        "cap_fowner", 
        "cap_fsetid", 
        "cap_kill", 
        "cap_setgid", 
        "cap_setuid", 
        "cap_setpcap", 
        "cap_linux_immutable", 
        "cap_net_bind_service", 
        "cap_net_broadcast", 
        "cap_net_admin", 
        "cap_net_raw", 
        "cap_ipc_lock", 
        "cap_ipc_owner", 
        "cap_sys_module", 
        "cap_sys_rawio", 
        "cap_sys_chroot", 
        "cap_sys_ptrace", 
        "cap_sys_pacct", 
        "cap_sys_admin", 
        "cap_sys_boot", 
        "cap_sys_nice", 
        "cap_sys_resource", 
        "cap_sys_time", 
        "cap_sys_tty_config", 
        "cap_mknod", 
        "cap_lease", 
        "cap_audit_write", 
        "cap_audit_control", 
        "cap_setfcap", 
        "cap_mac_override", 
        "cap_mac_admin", 
        "cap_syslog", 
        "35", 
        "36", 
        "37+ep"
    ], 
    "ansible_system_capabilities_enforced": "True", 
    "ansible_system_vendor": "VMware, Inc.", 
    "ansible_uptime_seconds": 4004, 
    "ansible_user_dir": "/root", 
    "ansible_user_gecos": "root", 
    "ansible_user_gid": 0, 
    "ansible_user_id": "root", 
    "ansible_user_shell": "/bin/bash", 
    "ansible_user_uid": 0, 
    "ansible_userspace_architecture": "x86_64", 
    "ansible_userspace_bits": "64", 
    "ansible_virtualization_role": "guest", 
    "ansible_virtualization_type": "VMware", 
    "gather_subset": [
        "all"
    ], 
    "module_setup": true
}
```

其中较为常用的变量

- ansible_distribution   

- ansible_distribution_release

- ansible_distribution_version  

- ansible_fqdn

- ansible_hostname

- ansible_os_family

- ansible_pkg_mgr

- ansible_default_ipv4.address

- ansible_default_ipv6.address

 

## 缓存Facts信息

Facts信息默认存储在内存中，即每次运行后，信息就不会存在了，这样会导致我们每次都需要重新去获取主机的所有Facts信息，浪费了很多时间，Facts给了几种缓存方式。



###  使用文件作为缓存

创建缓存存放的目录

```bash
mkdir /tmp/facts_cache
```

修改ansible配置文件

```ini
# /etc/ansible/ansible.cfg

gathering = smart
fact_caching = jsonfile
fact_caching_timeout = 86400
fact_caching_connection = /tmp/facts_cache
```

获取主机的Facts信息

```bash
ansible 192.168.77.130 -m setup
```

查看缓存目录

```bash
ll /tmp/facts_cache/
总用量 28
-rw-r--r-- 1 root root 25241 3月  31 11:39 192.168.77.130
```

> 上述文件中存储着json序列化的facts数据

### 使用redis作为缓存

 安装redis

```bash
# centos 7
yum -y install redis
easy_install pip
pip install redis
```

配置redis，使用密码登陆

```bash
echo 'requirepass "admin"' > /etc/redis.conf
```

启动redis

```bash
systemctl enable --now redis
```

修改ansible配置文件

```ini
# /etc/ansible/ansible.cfg

gathering = smart
fact_caching = redis
fact_caching_timeout = 86400
fact_caching_connection = localhost:6379:0:admin
```

获取主机的Facts信息

```bash
ansible 192.168.77.130 -m setup
```

查看redis内容

```bash
# redis-cli
127.0.0.1:6379> auth admin
OK
127.0.0.1:6379> keys *
1) "ansible_cache_keys"
2) "ansible_facts192.168.77.130"
127.0.0.1:6379> get ansible_facts192.168.77.130
.....
```

### 使用memcached作为缓存

安装  memcached

```bash
# centos 7
yum install memcached

easy_install pip
pip install python-memcached
```

启动memcached

```bash
systemctl enable --now memcached
```

修改ansible配置文件

```ini
# /etc/ansible/ansible.cfg

gathering = smart
fact_caching = memcached
fact_caching_timeout = 86400
fact_caching_connection = localhost:11211
```


获取主机的Facts信息

```bash
ansible 192.168.77.130 -m setup
```


查看memcached内容

```bash
# telnet 127.0.0.1 11211
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
stats items
STAT items:3:number 1
STAT items:3:age 135
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
STAT items:3:reclaimed 0
STAT items:3:expired_unfetched 0
STAT items:3:evicted_unfetched 0
STAT items:21:number 1
STAT items:21:age 135
STAT items:21:evicted 0
STAT items:21:evicted_nonzero 0
STAT items:21:evicted_time 0
STAT items:21:outofmemory 0
STAT items:21:tailrepairs 0
STAT items:21:reclaimed 0
STAT items:21:expired_unfetched 0
STAT items:21:evicted_unfetched 0
END
stats cachedump 3 0
ITEM ansible_cache_keys [46 b; 1585626688 s]
END
stats cachedump 21 0
ITEM ansible_facts192.168.77.130 [8349 b; 1585713251 s]
END
```

### 刷新缓存

默认情况下，缓存的生存时间是`fact_caching_timeout`控制的，如果我们想强制刷新缓存的话，可以使用`--flush-cache`选项

```bash
ansible-playbook --flush-cache /etc/ansible/test3.yaml
```

