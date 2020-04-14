# docker_facts 模块

只返回facts数据的模块

## 功能实现

获取远程主机的docker信息，并将其注册到facts数据中。

## 创建module

> 本例使用shell脚本

file: library/docker_facts.sh 

```bash
#!/bin/bash

ANSIBLE_METADATA="{'metadata_version': '1.0',
		  'status': ['preview'],
		  'supported_by': 'community'}"

DOCUMENTATION="
---
module: docker_facts
short_description: Get docker facts data
version_added: '2.9'
description:
  - Get docker facts data on remote host.
author:
  - 'Lework'
"
EXAMPLES="
# Example from Ansible Playbooks
- name: get docker facts
  docker_facts:
"

RETURN="
ansible_facts:
    description: docker facts
    type: dict
    returned: always
"

set -e

cat <<EOF
{
    "ansible_facts": {
        "docker_server_version": "$(docker version -f '{{.Server.Version}}')",
        "docker_client_version": "$(docker version -f '{{.Client.Version}}')",
        "docker_info": $(curl -s --unix-socket /var/run/docker.sock http://:/info),
        "docker_version": $(curl -s --unix-socket /var/run/docker.sock http://:/version),
        "docker_containers": $(curl -s --unix-socket /var/run/docker.sock http://:/containers/json?all=true),
        "docker_images": $(curl -s --unix-socket /var/run/docker.sock http://:/images/json)
    },
    "changed": false
}
EOF

exit 0
```

## 运行module

### 本地运行测试
```bash
# chmod +x library/docker_facts.sh 
# ./library/docker_facts.sh 
{
    "ansible_facts": {
        "docker_server_version": "18.09.6",
        "docker_client_version": "18.09.6",
        "docker_info": {"ID":"7SAH:IRUL:HLJO:O5N4:32CG:HGCK:MHR7:OJHS:6UBH:NM6I:KVFY:BOKL","Containers":2,"ContainersRunning":0,"ContainersPaused":0,"ContainersStopped":2,"Images":2,"Driver":"overlay2","DriverStatus":[["Backing Filesystem","xfs"],["Supports d_type","true"],["Native Overlay Diff","true"]],"SystemStatus":null,"Plugins":{"Volume":["local"],"Network":["bridge","host","macvlan","null","overlay"],"Authorization":null,"Log":["awslogs","fluentd","gcplogs","gelf","journald","json-file","local","logentries","splunk","syslog"]},"MemoryLimit":true,"SwapLimit":true,"KernelMemory":true,"CpuCfsPeriod":true,"CpuCfsQuota":true,"CPUShares":true,"CPUSet":true,"IPv4Forwarding":true,"BridgeNfIptables":false,"BridgeNfIp6tables":false,"Debug":false,"NFd":22,"OomKillDisable":true,"NGoroutines":37,"SystemTime":"2020-04-13T12:11:06.689886761+08:00","LoggingDriver":"json-file","CgroupDriver":"cgroupfs","NEventsListener":0,"KernelVersion":"5.1.11-1.el7.elrepo.x86_64","OperatingSystem":"CentOS Linux 7 (Core)","OSType":"linux","Architecture":"x86_64","IndexServerAddress":"https://index.docker.io/v1/","RegistryConfig":{"AllowNondistributableArtifactsCIDRs":[],"AllowNondistributableArtifactsHostnames":[],"InsecureRegistryCIDRs":["127.0.0.0/8"],"IndexConfigs":{"docker.io":{"Name":"docker.io","Mirrors":["http://dockerhub.azk8s.cn/"],"Secure":true,"Official":true}},"Mirrors":["http://dockerhub.azk8s.cn/"]},"NCPU":1,"MemTotal":1007276032,"GenericResources":null,"DockerRootDir":"/var/lib/docker","HttpProxy":"","HttpsProxy":"","NoProxy":"","Name":"node130","Labels":[],"ExperimentalBuild":false,"ServerVersion":"18.09.6","ClusterStore":"","ClusterAdvertise":"","Runtimes":{"runc":{"path":"runc"}},"DefaultRuntime":"runc","Swarm":{"NodeID":"","NodeAddr":"","LocalNodeState":"inactive","ControlAvailable":false,"Error":"","RemoteManagers":null},"LiveRestoreEnabled":true,"Isolation":"","InitBinary":"docker-init","ContainerdCommit":{"ID":"bb71b10fd8f58240ca47fbb579b9d1028eea7c84","Expected":"bb71b10fd8f58240ca47fbb579b9d1028eea7c84"},"RuncCommit":{"ID":"2b18fe1d885ee5083ef9f0838fee39b62d653e30","Expected":"2b18fe1d885ee5083ef9f0838fee39b62d653e30"},"InitCommit":{"ID":"fec3683","Expected":"fec3683"},"SecurityOptions":["name=seccomp,profile=default"],"ProductLicense":"Community Engine","Warnings":["WARNING: bridge-nf-call-iptables is disabled","WARNING: bridge-nf-call-ip6tables is disabled"]},
        "docker_version": {"Platform":{"Name":"Docker Engine - Community"},"Components":[{"Name":"Engine","Version":"18.09.6","Details":{"ApiVersion":"1.39","Arch":"amd64","BuildTime":"2019-05-04T02:02:43.000000000+00:00","Experimental":"false","GitCommit":"481bc77","GoVersion":"go1.10.8","KernelVersion":"5.1.11-1.el7.elrepo.x86_64","MinAPIVersion":"1.12","Os":"linux"}}],"Version":"18.09.6","ApiVersion":"1.39","MinAPIVersion":"1.12","GitCommit":"481bc77","GoVersion":"go1.10.8","Os":"linux","Arch":"amd64","KernelVersion":"5.1.11-1.el7.elrepo.x86_64","BuildTime":"2019-05-04T02:02:43.000000000+00:00"},
        "docker_containers": [{"Id":"cb323ddf4982cd46d8b89a4c7a349ba515c183d2b3364b3edd5687ce34f78ad0","Names":["/keen_jackson"],"Image":"ubuntu:latest","ImageID":"sha256:4e5021d210f65ebe915670c7089120120bc0a303b90208592851708c1b8c04bd","Command":"bash","Created":1586312956,"Ports":[],"Labels":{},"State":"exited","Status":"Exited (255) 13 minutes ago","HostConfig":{"NetworkMode":"default"},"NetworkSettings":{"Networks":{"bridge":{"IPAMConfig":null,"Links":null,"Aliases":null,"NetworkID":"82382b47b631f9c295d2ba2f9456b90d9d17a65eefae08da916c321dd6504167","EndpointID":"ece9b5d82c6e5ae16a23159dd8ffc0f87b6e77808418c47c70ea72c1d81496b4","Gateway":"172.17.0.1","IPAddress":"172.17.0.3","IPPrefixLen":16,"IPv6Gateway":"","GlobalIPv6Address":"","GlobalIPv6PrefixLen":0,"MacAddress":"02:42:ac:11:00:03","DriverOpts":null}}},"Mounts":[]},{"Id":"f51ab9f8490bae100763c5b7b1eb2e3470efec5b2fa025864d46e0045d913835","Names":["/jolly_leavitt"],"Image":"dlang2/dmd-ubuntu","ImageID":"sha256:452334c0b9a959c88a2e6dac05f8bb26d3ea9da3757e52c4eb9314c023c6802d","Command":"bash","Created":1586227101,"Ports":[],"Labels":{},"State":"exited","Status":"Exited (255) 13 minutes ago","HostConfig":{"NetworkMode":"default"},"NetworkSettings":{"Networks":{"bridge":{"IPAMConfig":null,"Links":null,"Aliases":null,"NetworkID":"82382b47b631f9c295d2ba2f9456b90d9d17a65eefae08da916c321dd6504167","EndpointID":"7898339e7a463a489ae19e994680f1e33808680745a8dfa6eab24f25a6fc0349","Gateway":"172.17.0.1","IPAddress":"172.17.0.2","IPPrefixLen":16,"IPv6Gateway":"","GlobalIPv6Address":"","GlobalIPv6PrefixLen":0,"MacAddress":"02:42:ac:11:00:02","DriverOpts":null}}},"Mounts":[{"Type":"bind","Source":"/root/dub","Destination":"/tmp","Mode":"","RW":true,"Propagation":"rprivate"}]}],
        "docker_images": [{"Containers":-1,"Created":1586186041,"Id":"sha256:452334c0b9a959c88a2e6dac05f8bb26d3ea9da3757e52c4eb9314c023c6802d","Labels":null,"ParentId":"","RepoDigests":["dlang2/dmd-ubuntu@sha256:acd64e92240f7987ae10cd9f6ab8b0bdff4ffe10605cb29c1a48305e9d2c0e68"],"RepoTags":["dlang2/dmd-ubuntu:latest"],"SharedSize":-1,"Size":866485017,"VirtualSize":866485017},{"Containers":-1,"Created":1584732022,"Id":"sha256:4e5021d210f65ebe915670c7089120120bc0a303b90208592851708c1b8c04bd","Labels":null,"ParentId":"","RepoDigests":["ubuntu@sha256:bec5a2727be7fff3d308193cfde3491f8fba1a2ba392b7546b43a051853a341d"],"RepoTags":["ubuntu:latest"],"SharedSize":-1,"Size":64205678,"VirtualSize":64205678}]
    },
    "changed": false
}
```
以json格式输出docker信息。

### ansible 运行

```bash
# ansible localhost -M /etc/ansible/library -m docker_facts 
localhost | SUCCESS => {
    "ansible_facts": {
        "docker_client_version": "18.09.6", 
        "docker_containers": [
            {
                "Command": "bash", 
                "Created": 1586312956, 
                "HostConfig": {
                    "NetworkMode": "default"
                }, 
                "Id": "cb323ddf4982cd46d8b89a4c7a349ba515c183d2b3364b3edd5687ce34f78ad0", 
                "Image": "ubuntu:latest", 
                "ImageID": "sha256:4e5021d210f65ebe915670c7089120120bc0a303b90208592851708c1b8c04bd", 
                "Labels": {}, 
                "Mounts": [], 
                "Names": [
                    "/keen_jackson"
                ], 
                "NetworkSettings": {
                    "Networks": {
                        "bridge": {
                            "Aliases": null, 
                            "DriverOpts": null, 
                            "EndpointID": "ece9b5d82c6e5ae16a23159dd8ffc0f87b6e77808418c47c70ea72c1d81496b4", 
                            "Gateway": "172.17.0.1", 
                            "GlobalIPv6Address": "", 
                            "GlobalIPv6PrefixLen": 0, 
                            "IPAMConfig": null, 
                            "IPAddress": "172.17.0.3", 
                            "IPPrefixLen": 16, 
                            "IPv6Gateway": "", 
                            "Links": null, 
                            "MacAddress": "02:42:ac:11:00:03", 
                            "NetworkID": "82382b47b631f9c295d2ba2f9456b90d9d17a65eefae08da916c321dd6504167"
                        }
                    }
                }, 
                "Ports": [], 
                "State": "exited", 
                "Status": "Exited (255) 9 minutes ago"
            }, 
            {
                "Command": "bash", 
                "Created": 1586227101, 
                "HostConfig": {
                    "NetworkMode": "default"
                }, 
                "Id": "f51ab9f8490bae100763c5b7b1eb2e3470efec5b2fa025864d46e0045d913835", 
                "Image": "dlang2/dmd-ubuntu", 
                "ImageID": "sha256:452334c0b9a959c88a2e6dac05f8bb26d3ea9da3757e52c4eb9314c023c6802d", 
                "Labels": {}, 
                "Mounts": [
                    {
                        "Destination": "/tmp", 
                        "Mode": "", 
                        "Propagation": "rprivate", 
                        "RW": true, 
                        "Source": "/root/dub", 
                        "Type": "bind"
                    }
                ], 
                "Names": [
                    "/jolly_leavitt"
                ], 
                "NetworkSettings": {
                    "Networks": {
                        "bridge": {
                            "Aliases": null, 
                            "DriverOpts": null, 
                            "EndpointID": "7898339e7a463a489ae19e994680f1e33808680745a8dfa6eab24f25a6fc0349", 
                            "Gateway": "172.17.0.1", 
                            "GlobalIPv6Address": "", 
                            "GlobalIPv6PrefixLen": 0, 
                            "IPAMConfig": null, 
                            "IPAddress": "172.17.0.2", 
                            "IPPrefixLen": 16, 
                            "IPv6Gateway": "", 
                            "Links": null, 
                            "MacAddress": "02:42:ac:11:00:02", 
                            "NetworkID": "82382b47b631f9c295d2ba2f9456b90d9d17a65eefae08da916c321dd6504167"
                        }
                    }
                }, 
                "Ports": [], 
                "State": "exited", 
                "Status": "Exited (255) 9 minutes ago"
            }
        ], 
        "docker_images": [
            {
                "Containers": -1, 
                "Created": 1586186041, 
                "Id": "sha256:452334c0b9a959c88a2e6dac05f8bb26d3ea9da3757e52c4eb9314c023c6802d", 
                "Labels": null, 
                "ParentId": "", 
                "RepoDigests": [
                    "dlang2/dmd-ubuntu@sha256:acd64e92240f7987ae10cd9f6ab8b0bdff4ffe10605cb29c1a48305e9d2c0e68"
                ], 
                "RepoTags": [
                    "dlang2/dmd-ubuntu:latest"
                ], 
                "SharedSize": -1, 
                "Size": 866485017, 
                "VirtualSize": 866485017
            }, 
            {
                "Containers": -1, 
                "Created": 1584732022, 
                "Id": "sha256:4e5021d210f65ebe915670c7089120120bc0a303b90208592851708c1b8c04bd", 
                "Labels": null, 
                "ParentId": "", 
                "RepoDigests": [
                    "ubuntu@sha256:bec5a2727be7fff3d308193cfde3491f8fba1a2ba392b7546b43a051853a341d"
                ], 
                "RepoTags": [
                    "ubuntu:latest"
                ], 
                "SharedSize": -1, 
                "Size": 64205678, 
                "VirtualSize": 64205678
            }
        ], 
        "docker_info": {
            "Architecture": "x86_64", 
            "BridgeNfIp6tables": false, 
            "BridgeNfIptables": false, 
            "CPUSet": true, 
            "CPUShares": true, 
            "CgroupDriver": "cgroupfs", 
            "ClusterAdvertise": "", 
            "ClusterStore": "", 
            "ContainerdCommit": {
                "Expected": "bb71b10fd8f58240ca47fbb579b9d1028eea7c84", 
                "ID": "bb71b10fd8f58240ca47fbb579b9d1028eea7c84"
            }, 
            "Containers": 2, 
            "ContainersPaused": 0, 
            "ContainersRunning": 0, 
            "ContainersStopped": 2, 
            "CpuCfsPeriod": true, 
            "CpuCfsQuota": true, 
            "Debug": false, 
            "DefaultRuntime": "runc", 
            "DockerRootDir": "/var/lib/docker", 
            "Driver": "overlay2", 
            "DriverStatus": [
                [
                    "Backing Filesystem", 
                    "xfs"
                ], 
                [
                    "Supports d_type", 
                    "true"
                ], 
                [
                    "Native Overlay Diff", 
                    "true"
                ]
            ], 
            "ExperimentalBuild": false, 
            "GenericResources": null, 
            "HttpProxy": "", 
            "HttpsProxy": "", 
            "ID": "7SAH:IRUL:HLJO:O5N4:32CG:HGCK:MHR7:OJHS:6UBH:NM6I:KVFY:BOKL", 
            "IPv4Forwarding": true, 
            "Images": 2, 
            "IndexServerAddress": "https://index.docker.io/v1/", 
            "InitBinary": "docker-init", 
            "InitCommit": {
                "Expected": "fec3683", 
                "ID": "fec3683"
            }, 
            "Isolation": "", 
            "KernelMemory": true, 
            "KernelVersion": "5.1.11-1.el7.elrepo.x86_64", 
            "Labels": [], 
            "LiveRestoreEnabled": true, 
            "LoggingDriver": "json-file", 
            "MemTotal": 1007276032, 
            "MemoryLimit": true, 
            "NCPU": 1, 
            "NEventsListener": 0, 
            "NFd": 22, 
            "NGoroutines": 37, 
            "Name": "node130", 
            "NoProxy": "", 
            "OSType": "linux", 
            "OomKillDisable": true, 
            "OperatingSystem": "CentOS Linux 7 (Core)", 
            "Plugins": {
                "Authorization": null, 
                "Log": [
                    "awslogs", 
                    "fluentd", 
                    "gcplogs", 
                    "gelf", 
                    "journald", 
                    "json-file", 
                    "local", 
                    "logentries", 
                    "splunk", 
                    "syslog"
                ], 
                "Network": [
                    "bridge", 
                    "host", 
                    "macvlan", 
                    "null", 
                    "overlay"
                ], 
                "Volume": [
                    "local"
                ]
            }, 
            "ProductLicense": "Community Engine", 
            "RegistryConfig": {
                "AllowNondistributableArtifactsCIDRs": [], 
                "AllowNondistributableArtifactsHostnames": [], 
                "IndexConfigs": {
                    "docker.io": {
                        "Mirrors": [
                            "http://dockerhub.azk8s.cn/"
                        ], 
                        "Name": "docker.io", 
                        "Official": true, 
                        "Secure": true
                    }
                }, 
                "InsecureRegistryCIDRs": [
                    "127.0.0.0/8"
                ], 
                "Mirrors": [
                    "http://dockerhub.azk8s.cn/"
                ]
            }, 
            "RuncCommit": {
                "Expected": "2b18fe1d885ee5083ef9f0838fee39b62d653e30", 
                "ID": "2b18fe1d885ee5083ef9f0838fee39b62d653e30"
            }, 
            "Runtimes": {
                "runc": {
                    "path": "runc"
                }
            }, 
            "SecurityOptions": [
                "name=seccomp,profile=default"
            ], 
            "ServerVersion": "18.09.6", 
            "SwapLimit": true, 
            "Swarm": {
                "ControlAvailable": false, 
                "Error": "", 
                "LocalNodeState": "inactive", 
                "NodeAddr": "", 
                "NodeID": "", 
                "RemoteManagers": null
            }, 
            "SystemStatus": null, 
            "SystemTime": "2020-04-13T12:07:10.426882075+08:00", 
            "Warnings": [
                "WARNING: bridge-nf-call-iptables is disabled", 
                "WARNING: bridge-nf-call-ip6tables is disabled"
            ]
        }, 
        "docker_server_version": "18.09.6", 
        "docker_version": {
            "ApiVersion": "1.39", 
            "Arch": "amd64", 
            "BuildTime": "2019-05-04T02:02:43.000000000+00:00", 
            "Components": [
                {
                    "Details": {
                        "ApiVersion": "1.39", 
                        "Arch": "amd64", 
                        "BuildTime": "2019-05-04T02:02:43.000000000+00:00", 
                        "Experimental": "false", 
                        "GitCommit": "481bc77", 
                        "GoVersion": "go1.10.8", 
                        "KernelVersion": "5.1.11-1.el7.elrepo.x86_64", 
                        "MinAPIVersion": "1.12", 
                        "Os": "linux"
                    }, 
                    "Name": "Engine", 
                    "Version": "18.09.6"
                }
            ], 
            "GitCommit": "481bc77", 
            "GoVersion": "go1.10.8", 
            "KernelVersion": "5.1.11-1.el7.elrepo.x86_64", 
            "MinAPIVersion": "1.12", 
            "Os": "linux", 
            "Platform": {
                "Name": "Docker Engine - Community"
            }, 
            "Version": "18.09.6"
        }
    }, 
    "changed": false
}
```

### playbook 运行

playbook 内容

```yaml
---
- hosts: localhost
  gather_facts: no
  tasks:
   - name: get docker facts
     docker_facts:
   - name: show facts
     debug: var=ansible_facts.docker_version
```
playbook 运行
```bash
# ansible-playbook test.yml                                 

PLAY [localhost] *********************************************************************************************************************

TASK [get docker facts] **************************************************************************************************************
ok: [localhost]

TASK [show facts] ********************************************************************************************************************
ok: [localhost] => {
    "ansible_facts.docker_version": {
        "ApiVersion": "1.39", 
        "Arch": "amd64", 
        "BuildTime": "2019-05-04T02:02:43.000000000+00:00", 
        "Components": [
            {
                "Details": {
                    "ApiVersion": "1.39", 
                    "Arch": "amd64", 
                    "BuildTime": "2019-05-04T02:02:43.000000000+00:00", 
                    "Experimental": "false", 
                    "GitCommit": "481bc77", 
                    "GoVersion": "go1.10.8", 
                    "KernelVersion": "5.1.11-1.el7.elrepo.x86_64", 
                    "MinAPIVersion": "1.12", 
                    "Os": "linux"
                }, 
                "Name": "Engine", 
                "Version": "18.09.6"
            }
        ], 
        "GitCommit": "481bc77", 
        "GoVersion": "go1.10.8", 
        "KernelVersion": "5.1.11-1.el7.elrepo.x86_64", 
        "MinAPIVersion": "1.12", 
        "Os": "linux", 
        "Platform": {
            "Name": "Docker Engine - Community"
        }, 
        "Version": "18.09.6"
    }
}

PLAY RECAP ***************************************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
```