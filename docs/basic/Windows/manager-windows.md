# 管理 windows 主机

## windows 系统要求

- PowerShell 3 或更高
- 不支持Cygwin

> 在Windows 7和Server 2008 R2计算机上，由于Windows Management Framework 3.0中的错误，可能需要安装此修补程序 http://support.microsoft.com/kb/2842230 以避免收到内存和堆栈溢出异常。已知新安装的Server 2008 R2系统与Windows更新不兼容，具有此问题。Windows 8.1和Server 2012 R2不受Windows Management Framework 4.0附带的此问题的影响。

## inventory 示例文件

```yml
[windows]
winserver1.example.com
winserver2.example.com

[windows:vars]
ansible_user=Administrator
ansible_password=123456
ansible_port=5986
ansible_connection=winrm
# The following is necessary for Python 2.7.9+ (or any older Python that has backported SSLContext, eg, Python 2.7.5 on RHEL7) when using default WinRM self-signed certificates:
ansible_winrm_server_cert_validation=ignore
```

## inventory 可用变量

- ansible_winrm_scheme：指定用于WinRM连接的连接方案（http或https）。https默认情况下可以使用，除非端口是5985。
- ansible_winrm_path：指定WinRM端点的备用路径。/wsman默认情况下可以使用。
- ansible_winrm_realm：指定用于Kerberos身份验证的领域。如果用户名包含@，Ansible将@默认使用部分用户名。
- ansible_winrm_transport：以一个逗号分隔的列表指定一个或多个传输。默认情况下，kerberos,plaintext如果已kerberos安装模块并定义了一个域，则“ 可用”将会使用，否则plaintext。
- ansible_winrm_server_cert_validation：指定服务器证书验证模式（ignore或validate）。validatePython 2.7.9及更高版本的可选默认值将导致Windows自签名证书的证书验证错误。除非在WinRM侦听器上配置了可验证的证书，否则应将其设置为ignore
- ansible_winrm_kerberos_delegation：设置为true在远程主机上使用Kerberos时启用命令委派。
- ansible_winrm_*：winrm.Protocol可以提供支持的任何其他关键字参数。

## 有什么模块可以用的？
	• add_host
	• assert
	• async
	• debug
	• fail
	• fetch
	• group_by
	• include_vars
	• meta
	• pause
	• raw
	• script
	• set_fact
	• setup
	• slurp
	• template (also: win_template)

专门用作windows系统的[模块](/basic/Reference/Module/#windows-modules)

## 获取 Windows Facts
```bash
ansible winhost.example.com -m setup
```

## Windows Playbook示例
```yaml
# 执行powershell脚本
- name: test script module
  hosts: windows
  tasks:
    - name: run test script
      script: files/test_script.ps1

# 获取ip地址信息
- name: test raw module
  hosts: windows
  tasks:
    - name: run ipconfig
      win_command: ipconfig
      register: ipconfig
    - debug: var=ipconfig

# 使用dos命令，移动文件
- name: another raw module example
  hosts: windows
  tasks:
     - name: Move file on remote Windows Server from one location to another
       win_command: CMD /C "MOVE /Y C:\teststuff\myfile.conf C:\builds\smtp.conf"

# 使用powershell命令，移动文件
- name: another raw module example demonstrating powershell one liner
  hosts: windows
  tasks:
     - name: Move file on remote Windows Server from one location to another
       win_command: Powershell.exe "Move-Item C:\teststuff\myfile.conf C:\builds\smtp.conf"

# 查看文件状态
- name: test stat module
  hosts: windows
  tasks:
    - name: test stat module on file
      win_stat: path="C:/Windows/win.ini"
      register: stat_file

    - debug: var=stat_file

    - name: check stat_file result
      assert:
          that:
             - "stat_file.stat.exists"
             - "not stat_file.stat.isdir"
             - "stat_file.stat.size > 0"
             - "stat_file.stat.md5"
```


## 本次实验环境

- windows os：`Microsoft Windows Server 2016`
- ansible manager：`centos 7.7 X64`
- ansible version： `2.9.6.0`
- python version：`Python 2.7.5`


##  Windows Server 2016 节点配置
1. 以管理员身份打开powershell
2. 查看当前ps版本
    ```powershell
    PS C:\Users\Administrator> $PSVersionTable

    Name                           Value
    ----                           -----
    PSVersion                      5.1.14393.1884
    PSEdition                      Desktop
    PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
    BuildVersion                   10.0.14393.1884
    CLRVersion                     4.0.30319.42000
    WSManStackVersion              3.0
    PSRemotingProtocolVersion      2.3
    SerializationVersion           1.1.0.1
    ```

    !!! tips
        Ansible 需要在 powershell 3.0, .net Framework 4.0或更新的版本上运行，可以用下列命令升级powershell
        ```powershell
        $url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Upgrade-PowerShell.ps1"
        $file = "$env:temp\Upgrade-PowerShell.ps1"
        $username = "Administrator"
        $password = "Password"

        (New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
        Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force

        # Version can be 3.0, 4.0 or 5.1
        &$file -Version 5.1 -Username $username -Password $password -Verbose
        ```
        完成后，您需要将删除自动登录并将执行策略设置回默认值Restricted。
        ```powershell
        # This isn't needed but is a good security practice to complete
        Set-ExecutionPolicy -ExecutionPolicy Restricted -Force

        $reg_winlogon_path = "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Winlogon"
        Set-ItemProperty -Path $reg_winlogon_path -Name AutoAdminLogon -Value 0
        Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultUserName -ErrorAction SilentlyContinue
        Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultPassword -ErrorAction SilentlyContinue
        ```
        
        在PowerShell v3.0上运行时，WinRM服务有一个缺陷，限制了WinRM可用的内存量。可以使用下列命令修补。
        ```powershell
        $url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Install-WMF3Hotfix.ps1"
        $file = "$env:temp\Install-WMF3Hotfix.ps1"

        (New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
        powershell.exe -ExecutionPolicy ByPass -File $file -Verbose
        ```

3. 配置winrm

    使用脚本启用HTTP和HTTPS的侦听器
    ```powershell
    $url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
    $file = "$env:temp\ConfigureRemotingForAnsible.ps1"

    (New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)

    powershell.exe -ExecutionPolicy ByPass -File $file
    ```

    获取winrm信息

    ```powershell
    PS C:\Users\Administrator\Desktop> winrm get winrm/config/Service
    Service
        RootSDDL = O:NSG:BAD:P(A;;GA;;;BA)(A;;GR;;;IU)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
        MaxConcurrentOperations = 4294967295
        MaxConcurrentOperationsPerUser = 1500
        EnumerationTimeoutms = 240000
        MaxConnections = 300
        MaxPacketRetrievalTimeSeconds = 120
        AllowUnencrypted = false
        Auth
            Basic = true
            Kerberos = true
            Negotiate = true
            Certificate = false
            CredSSP = false
            CbtHardeningLevel = Relaxed
        DefaultPorts
            HTTP = 5985
            HTTPS = 5986
        IPv4Filter = *
        IPv6Filter = *
        EnableCompatibilityHttpListener = false
        EnableCompatibilityHttpsListener = false
        CertificateThumbprint
        AllowRemoteAccess = true

    PS C:\Users\Administrator\Desktop> winrm get winrm/config/Winrs
    Winrs
        AllowRemoteShellAccess = true
        IdleTimeout = 7200000
        MaxConcurrentUsers = 2147483647
        MaxShellRunTime = 2147483647
        MaxProcessesPerShell = 2147483647
        MaxMemoryPerShellMB = 2147483647
        MaxShellsPerUser = 2147483647
    ```

    测试winrm连接

    ```powershell
    $username = "Administrator"
    $password = "Admin123"

    # Test out HTTP
    winrs -r:http://127.0.0.1:5985/wsman -u:$username -p:$password ipconfig

    # Test out HTTPS (will fail if the cert is not verifiable)
    winrs -r:https://127.0.0.1:5986/wsman -u:$username -p:$password -ssl ipconfig

    # Test out HTTPS, ignoring certificate verification
    $username = "Administrator"
    $password = ConvertTo-SecureString -String "Admin123" -AsPlainText -Force
    $cred = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $username, $password

    $session_option = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
    Invoke-Command -ComputerName 127.0.0.1 -UseSSL -ScriptBlock { ipconfig } -Credential $cred -SessionOption $session_option
    ```


## ansible manager 配置
1. 安装ansible和pywinrm
    ```bash
    yum -y install ansible
    curl -sL https://bootstrap.pypa.io/get-pip.py | python
    pip install pywinrm
    ```
2. 配置hosts
    ```bash
    [root@master ~]# cd /etc/ansible/
    [root@master ansible]# cat win_hosts 
    [windows]
    192.168.77.135
    [windows:vars]
    ansible_user=Administrator
    ansible_password=Admin123
    ansible_port=5986
    ansible_connection=winrm
    ansible_winrm_server_cert_validation=ignore
    ```

3. 测试通信
    ```bash
    # ansible -i win_hosts windows -m win_ping
    192.168.77.135 | SUCCESS => {
        "changed": false, 
        "ping": "pong"
    }
```
4. 查看系统信息
    ```bash
    # ansible -i win_hosts windows -m win_command -a "whoami"
    192.168.77.135 | CHANGED | rc=0 >>
    win-v5sbnpsnfom\administrator

    # ansible -i win_hosts windows -m win_command -a "systeminfo" 
    192.168.77.135 | CHANGED | rc=0 >>

    Host Name:                 WIN-V5SBNPSNFOM
    OS Name:                   Microsoft Windows Server 2016 Datacenter
    OS Version:                10.0.14393 N/A Build 14393
    OS Manufacturer:           Microsoft Corporation
    OS Configuration:          Standalone Server
    OS Build Type:             Multiprocessor Free
    Registered Owner:          Windows 用户
    Registered Organization:   
    Product ID:                00376-40000-00000-AA947
    Original Install Date:     2019/7/24, 14:54:43
    System Boot Time:          2020/4/8, 18:03:12
    System Manufacturer:       VMware, Inc.
    System Model:              VMware7,1
    System Type:               x64-based PC
    Processor(s):              2 Processor(s) Installed.
                               [01]: Intel64 Family 6 Model 60 Stepping 3 GenuineIntel ~3592 Mhz
                               [02]: Intel64 Family 6 Model 60 Stepping 3 GenuineIntel ~3592 Mhz
    BIOS Version:              VMware, Inc. VMW71.00V.14410784.B64.1908150010, 2019/8/15
    Windows Directory:         C:\Windows
    System Directory:          C:\Windows\system32
    Boot Device:               \Device\HarddiskVolume2
    System Locale:             zh-cn;Chinese (China)
    Input Locale:              zh-cn;Chinese (China)
    Time Zone:                 (UTC+08:00) Beijing, Chongqing, Hong Kong, Urumqi
    Total Physical Memory:     2,047 MB
    Available Physical Memory: 847 MB
    Virtual Memory: Max Size:  3,199 MB
    Virtual Memory: Available: 2,019 MB
    Virtual Memory: In Use:    1,180 MB
    Page File Location(s):     C:\pagefile.sys
    Domain:                    WORKGROUP
    Logon Server:              \\WIN-V5SBNPSNFOM
    Hotfix(s):                 2 Hotfix(s) Installed.
                               [01]: KB4049065
                               [02]: KB4048953
    Network Card(s):           1 NIC(s) Installed.
                               [01]: Intel(R) 82574L Gigabit Network Connection
                                     Connection Name: Ethernet0
                                     DHCP Enabled:    Yes
                                     DHCP Server:     192.168.77.254
                                     IP address(es)
                                     [01]: 192.168.77.135
                                     [02]: fe80::cd89:483d:58ae:d350
    Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.

    # ansible -i win_hosts windows -m win_shell -a "\$PSVersionTable"
    192.168.77.135 | CHANGED | rc=0 >>

    Name                           Value                               
    ----                           -----                               
    PSVersion                      5.1.14393.1884                      
    PSEdition                      Desktop                             
    PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}             
    BuildVersion                   10.0.14393.1884                     
    CLRVersion                     4.0.30319.42000                     
    WSManStackVersion              3.0                                 
    PSRemotingProtocolVersion      2.3                                 
    SerializationVersion           1.1.0.1  
    ```

4. 查看ip地址
    ```bash
    # ansible -i win_hosts windows -m win_command -a "ipconfig"
    192.168.77.135 | CHANGED | rc=0 >>

    Windows IP Configuration


    Ethernet adapter Ethernet0:

       Connection-specific DNS Suffix  . : localdomain
       Link-local IPv6 Address . . . . . : fe80::cd89:483d:58ae:d350%4
       IPv4 Address. . . . . . . . . . . : 192.168.77.135
       Subnet Mask . . . . . . . . . . . : 255.255.255.0
       Default Gateway . . . . . . . . . : 192.168.77.2

    Tunnel adapter isatap.localdomain:

       Media State . . . . . . . . . . . : Media disconnected
       Connection-specific DNS Suffix  . : localdomain

    Tunnel adapter Teredo Tunneling Pseudo-Interface:

       Connection-specific DNS Suffix  . : 
       IPv6 Address. . . . . . . . . . . : 2001:0:348b:fb58:1014:186b:3f57:b278
       Link-local IPv6 Address . . . . . : fe80::1014:186b:3f57:b278%2
       Default Gateway . . . . . . . . . : ::

    # ansible -i win_hosts windows -m raw -a "ipconfig"           
    192.168.77.135 | CHANGED | rc=0 >>

    Windows IP Configuration


    Ethernet adapter Ethernet0:

       Connection-specific DNS Suffix  . : localdomain
       Link-local IPv6 Address . . . . . : fe80::cd89:483d:58ae:d350%4
       IPv4 Address. . . . . . . . . . . : 192.168.77.135
       Subnet Mask . . . . . . . . . . . : 255.255.255.0
       Default Gateway . . . . . . . . . : 192.168.77.2

    Tunnel adapter isatap.localdomain:

       Media State . . . . . . . . . . . : Media disconnected
       Connection-specific DNS Suffix  . : localdomain

    Tunnel adapter Teredo Tunneling Pseudo-Interface:

       Connection-specific DNS Suffix  . : 
       IPv6 Address. . . . . . . . . . . : 2001:0:348b:fb58:1014:186b:3f57:b278
       Link-local IPv6 Address . . . . . : fe80::1014:186b:3f57:b278%2
       Default Gateway . . . . . . . . . : ::

    ```