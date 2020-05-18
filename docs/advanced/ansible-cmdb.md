# Ansible-cmdb

[ansible-cmdb](https://github.com/fboender/ansible-cmdb) 获取Ansible facts数据的输出，并将其转换为包含系统配置信息的静态HTML概述页面（及其他内容）。



## 安装

```bash
yum -y install python-pip

pip install ansible-cmdb
```



## 使用

生成所有主机得facts信息

```bash
ansible -m setup --tree out/ all
```



生成web页面

```
ansible-cmdb out/ > overview.html
```

![](/images/advanced/ansible-cmdb01.png)



如果facts用了本地缓存，`-f` 指定缓存目录即可。

```bash
ansible-cmdb -f /path/to/facts/dir > overview.html
```



以资产列表得形式统计出ansible主机信息。

```bash
# ansible-cmdb -t txt_table --columns name,os,ip,mem,cpus out/
Name       OS          IP              Mem  CPUs  
---------  ----------  --------------  ---  ----  
localhost  CentOS 7.6  192.168.77.130  1g   1  
```

输出csv格式的主机信息。

```bash
# ansible-cmdb -t csv out/             
"Name","OS","IP","Arch","Mem","MemFree","MemUsed","CPUs","Virt","Disk avail"
"localhost","CentOS 7.6","192.168.77.130","x86_64/x86_64","1g","0g","1g","1","VMware/guest","28.0g, 0.0g"

```


输出sql文件，导入数据到mysql或者SQLite。

```bash
# ansible-cmdb -t sql out/
DROP TABLE IF EXISTS hosts;
CREATE TABLE hosts (
    name VARCHAR(255),
    fqdn VARCHAR(255),
    main_ip VARCHAR(15),
    os_name VARCHAR(80),
    os_version VARCHAR(40),
    system VARCHAR(40),
    kernel VARCHAR(40),
    arch_hardware VARCHAR(12),
    arch_userspace VARCHAR(12),
    virt_type VARCHAR(20),
    virt_role VARCHAR(20),
    cpu_type VARCHAR(60),
    vcpus INT,
    ram FLOAT,
    disk_total FLOAT,
    disk_free FLOAT
);

    INSERT INTO hosts (
        name,
        fqdn,
        main_ip,
        os_name,
        os_version,
        system,
        kernel,
        arch_hardware,
        arch_userspace,
        virt_type,
        virt_role,
        cpu_type,
        vcpus,
        ram,
        disk_total,
        disk_free
    ) VALUES (
        "localhost",
        "a23-202-231-167.deploy.static.akamaitechnologies.com",
        "192.168.77.130",
        "CentOS",
        "7.6",
        "Linux",
        "5.1.11-1.el7.elrepo.x86_64",
        "x86_64",
        "x86_64",
        "VMware",
        "guest",
        "Intel(R) Core(TM) i3-4160 CPU @ 3.60GHz",
        1,
        0.9,
        29.8,
        27.4
    );
```

其他模板格式。

```bash
ansible-cmdb -t json out/ 
ansible-cmdb -t markdown out/
```

