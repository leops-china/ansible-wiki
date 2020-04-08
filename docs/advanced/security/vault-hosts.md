# 加密主机清单

## 主机清单源文件
```
[root@master ansible]# cat /etc/ansible/hosts2 
[node1]
192.168.77.129 ansible_ssh_pass=123456
[node2]
192.168.77.130 ansible_ssh_pass=123456
[node3]
192.168.77.131 ansible_ssh_pass=123456
```

## 使用1234567密码进行加密主机清单
```
[root@master ansible]# ansible-vault encrypt /etc/ansible/hosts2
New Vault password: 
Confirm New Vault password: 
Encryption successful

再次去查看hosts2的文件内容时，内容是已经加密过的了
[root@master ansible]# cat /etc/ansible/hosts2
$ANSIBLE_VAULT;1.1;AES256
39623561303563343739653030366332363466353462363632336433346537376263326331643338
6531636436633334633533363664663266393939613938650a656261396661633732353536353339
61663162323861613032376463326566393034653963633038303162626135303463303233373130
3437363561323131320a376665383735613961616537333266353565386237373433393162386332
35313265303137616438353964316662646136623665633132393566333465333563383438643431
36376366633735366564383735656434373436326238343363383132373931353839333139333131
31323437393232306437363563366662613139386635356161396630376439343832346662393136
65353537643761376230653965393864643333356338386537343061306166396137343664346561
65663630306134623362383065316134353062323636326231396630313761326631373862653836
65623161633837306536616432646236646261656232626135396631666166636632643465383663
653832366630616363336566626432353164
```
## 编辑加密后的主机清单文件
```
[root@master ~]# ansible-vault edit /etc/ansible/hosts2 --ask-vault-pass
Vault password: 
```

## 使用加密文件运行任务

运行ansible时，会提示解密错误
```
[root@master ansible]# ansible -i /etc/ansible/hosts2 node1 -m ping
ERROR! Attempted to read "/etc/ansible/hosts2" as YAML: Decryption failed on /etc/ansible/hosts2
Attempted to read "/etc/ansible/hosts2" as ini file: Decryption failed on /etc/ansible/hosts2 
```
这时，我们需要输入加密的密码，才可以运行命令。
```
[root@master ansible]# ansible -i /etc/ansible/hosts2 node1 -m ping --ask-vault-pass 
Vault password: 
192.168.77.129 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
[root@master ansible]# ansible-playbook -i /etc/ansible/hosts2 test.yml --ask-vault-pass 
Vault password: 

PLAY [node1] *******************************************************************************************************************

TASK [command] *****************************************************************************************************************
changed: [192.168.77.129]

RUNNING HANDLER [test1] ********************************************************************************************************
ok: [192.168.77.129] => {
    "changed": false, 
    "msg": "456"
}

PLAY RECAP *********************************************************************************************************************
192.168.77.129             : ok=2    changed=1    unreachable=0    failed=0
```
