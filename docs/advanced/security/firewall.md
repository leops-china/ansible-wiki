# 防火墙设置

## 规则

- 只开启ssh端口。
- 限制管理人员登录的ip地址。


### Iptables

```bash
# 清除所有规则
iptables -F
iptables -X
iptables -Z

# 添加规则，只允许192.168.77.1地址访问22端口，其他一律禁止。
iptables -I INPUT -s 192.168.77.1/32 -p tcp --dport 22 -j ACCEPT  
iptables -A INPUT -p tcp --dport 22 -j DROP
iptables -A INPUT -p icmp -j DROP
iptables -P INPUT DROP

# 保存配置并重启iptables服务
/etc/init.d/iptables save
/etc/init.d/iptables restart
```

## Firewalld

```bash
# 添加规则，只允许192.168.77.1地址访问22端口，其他一律禁止。
firewall-cmd --permanent --add-rich-rule='
        rule family="ipv4"
        source address="192.168.77.1/32"
        port protocol="tcp" port="22" accept'

# 重载配置
firewall-cmd --reload
```

### ufw

```bash
# 开启
ufw enbale

# 添加规则，只允许192.168.77.1地址访问22端口，其他一律禁止。
ufw allow proto tcp from 192.168.77.1 port 22

# 添加默认规则为禁用
ufw default deny
```