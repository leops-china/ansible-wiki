Ansible Vault是Ansible的一项功能，它允许你将密码或密钥等敏感数据保存在加密的文件中，而不是明文保存在剧本或角色中。然后可以将这些库文件分发或放置在源代码控制中。



## 创建加密文件

创建新的加密文件，可使用以下命令

```bash
# ansible-vault create foo.yml
New Vault password: 
Confirm New Vault password: 
```

> 在输入加密密码后，在编辑界面输入加密内容保存即可加密

查看加密后的文件

```bash
# cat foo.yml 
$ANSIBLE_VAULT;1.1;AES256
66623733393134373761386161313462613530313331393464363366623063653261306631616333
3635363533623230633432343131633430663039363536340a383535623264363334656161333632
37346635636331613732313132653830636234643230616661383630373863643233626265373034
6665623561643337370a623336636362316330663862373833363263386563636261613765386635
3434
```

> 默认的加密方式是 AES

创建拥有id的加密文件

```bash
ansible-vault create --vault-id password1@prompt foo.yml
```

> `--vault-id label@source`  label为标签， source为密码的获取方式

## 编辑加密文件

```bash
ansible-vault edit foo.yml
```

>  此命令将文件解密为一个临时文件，并允许您编辑该文件，完成后将其保存并删除临时文件

编辑拥有id的加密文件

```bash
ansible-vault edit --vault-id pass2@vault2 foo.yml
```

## 重新加密文件

```bash
ansible-vault rekey foo.yml bar.yml baz.yml
```

> 该命令可以同时对多个数据文件进行密钥重设，并要求输入原始密码和新密码。

重新加密拥有id的加密文件

```bash
ansible-vault rekey --vault-id preprod2@ppold --new-vault-id preprod2@prompt foo.yml bar.yml baz.yml
```



## 文件加密

对hosts文件进行加密

```bash
#  ansible-vault encrypt /etc/ansible/hosts
New Vault password: 
Confirm New Vault  password: 
Encryption successful
```

使用id加密文件

```bash
ansible-vault encrypt --vault-id project@prompt foo.yml bar.yml baz.yml
```



## 文件解密

```bash
ansible-vault decrypt foo.yml bar.yml baz.yml
```



## 使用 `encrypt_string` 在`yaml` 中创建加密变量



```bash
# echo 123 > a_password_file 

# ansible-vault encrypt_string --vault-password-file a_password_file 'foobar' --name 'the_secret'
the_secret: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          33366336396662373333323664653438366364316136333234346533326665326130316261363564
          6462616561333938393133303461376265336538313637380a326331373537363566656230313237
          66306131616133316339666337653131306564393633643037653461363133373234376264373738
          3437303466366436300a336136383033323230303764633862383731326464633536343164353034
          3532
Encryption successful
```

输出的字符串可使用在playbook中



使用`vault-id` 

```bash
# ansible-vault encrypt_string --vault-id dev@a_password_file 'foooodev' --name 'the_dev_secret'
the_dev_secret: !vault |
          $ANSIBLE_VAULT;1.2;AES256;dev
          35313739373461366564323863386435363738616130313833653432363337326339343834303638
          6531303333373330316666653536373733303334333332330a393938643935643134623064343133
          35396538326465323431656430633835613066343561386663613034366134393739643934663865
          6133326634643164660a346634366433613662336566376134346361373166356563663536313935
          6361
Encryption successful

```

从stdin读取字符串并将其命名为`db_password`

```bash
echo -n 'letmein' | ansible-vault encrypt_string --vault-id dev@a_password_file --stdin-name 'db_password'
Reading plaintext input from stdin. (ctrl-d to end input)
db_password: !vault |
          $ANSIBLE_VAULT;1.2;AES256;dev
          65656661383162623438313763613462616361626237623630323839366130613530323437313036
          3635636261303662363832376635663466623662356666640a653432336437633436376236323634
          33373632666533653062323431396164396263623565616131333766343561353561636430373338
          3637393832656164640a643463366165376461663032373439663536363538386232643230393638
          6365
Encryption successful

```

在yaml中使用

```yaml
notsecret: myvalue
db_password: !vault |
          $ANSIBLE_VAULT;1.2;AES256;dev
          65656661383162623438313763613462616361626237623630323839366130613530323437313036
          3635636261303662363832376635663466623662356666640a653432336437633436376236323634
          33373632666533653062323431396164396263623565616131333766343561353561636430373338
          3637393832656164640a643463366165376461663032373439663536363538386232643230393638
          6365
```



## 提供 `Vault` 密码

当使用加密数据时，应该使用`--ask-vault-pass`或`--vault-password`选项。

```bash
# 定义密码文件
echo 123456 > /path/to/my/vault-password-file site.yml

# 指定密码
ansible-playbook --vault-password-file /path/to/my/vault-password-file site.yml
```

交互式输入密码

```bash
ansible-playbook --ask-vault-pass site.yml
```

执行脚本获取密码

```bash
ansible-playbook --vault-password-file my-vault-password.py
```

也可以指定环境变量

```bash
DEFAULT_VAULT_PASSWORD_FILE=/path/to/my/vault-password-file ansible-playbook --ask-vault-pass site.yml
```

## Vaults 标签

默认情况下，`vault-id`标签只是一个提示，任何用密码加密的值都会被解密。配置选项的默认保险库ID匹配可以设置为要求保险库ID与加密值时使用的保险库ID匹配。这可以减少使用不同密码加密不同值时的错误。

`DEFAULT_VAULT_ID_MATCH ` 环境变量可以设置需要指定的`vault-id`标签



为`vault-id` 标签`dev`使用密码文件

```bash
ansible-playbook --vault-id dev-password site.yml
```

为`vault-id` 标签 `dev`使用交互输入密码

```bash
ansible-playbook --vault-id dev@prompt site.yml
```

为`vault-id` 标签 `dev`使用脚本输入密码

```bash
ansible-playbook --vault-id dev@my-vault-password.py
```

`DEFAULT_VAULT_IDENTITY_LIST ` 环境变量可以设置需要指定的`vault-id`和密码源，而不必指定`--vault-id`选项

```bash
ansible-playbook --vault-id dev-password site.yml

ansible-playbook --vault-id @prompt site.yml

ansible-playbook --vault-id my-vault-password.py
```



## 多个 Vault 密码

Ansible 2.4 之后的额版本，可以多次指定`vault-id`选项来设置多个密码

```bash
ansible-playbook --vault-id dev@dev-password --vault-id prod@prompt site.yml
```

在上述情况下，首先尝试`dev`密码，然后是prod密码， Ansible不知道哪个金库ID是用来加密的东西。



## 使用客户端脚本设置 Vault 密码

客户端脚本是一个以`--client`结尾的可执行脚本。

```bash
ansible-playbook --vault-id dev@contrib/vault/vault-keyring-client.py
```



脚本内容

```python
ANSIBLE_METADATA = {'status': ['preview'],
                    'supported_by': 'community',
                    'version': '1.0'}

import argparse
import sys
import getpass
import keyring

from ansible.config.manager import ConfigManager

KEYNAME_UNKNOWN_RC = 2


def build_arg_parser():
    parser = argparse.ArgumentParser(description='Get a vault password from user keyring')

    parser.add_argument('--vault-id', action='store', default=None,
                        dest='vault_id',
                        help='name of the vault secret to get from keyring')
    parser.add_argument('--username', action='store', default=None,
                        help='the username whose keyring is queried')
    parser.add_argument('--set', action='store_true', default=False,
                        dest='set_password',
                        help='set the password instead of getting it')
    return parser


def main():
    config_manager = ConfigManager()
    username = config_manager.data.get_setting('vault.username')
    if not username:
        username = getpass.getuser()

    keyname = config_manager.data.get_setting('vault.keyname')
    if not keyname:
        keyname = 'ansible'

    arg_parser = build_arg_parser()
    args = arg_parser.parse_args()

    username = args.username or username
    keyname = args.vault_id or keyname

    # print('username: %s keyname: %s' % (username, keyname))

    if args.set_password:
        intro = 'Storing password in "{}" user keyring using key name: {}\n'
        sys.stdout.write(intro.format(username, keyname))
        password = getpass.getpass()
        confirm = getpass.getpass('Confirm password: ')
        if password == confirm:
            keyring.set_password(keyname, username, password)
        else:
            sys.stderr.write('Passwords do not match\n')
            sys.exit(1)
    else:
        secret = keyring.get_password(keyname, username)
        if secret is None:
            sys.stderr.write('vault-keyring-client could not find key="%s" for user="%s" via backend="%s"\n' %
                             (keyname, username, keyring.get_keyring().name))
            sys.exit(KEYNAME_UNKNOWN_RC)

        # print('secret: %s' % secret)
        sys.stdout.write('%s\n' % secret)

    sys.exit(0)


if __name__ == '__main__':
    main()
```







## 加速加密速度

如果你有许多文件需要加密，可以使用`cryptography`来进行加快加密速度

```bash
pip install cryptography
```



## Vault 文件

Vault 加密文件是UTF-8编码的txt文件。

文件格式包括一个换行结束的头文件。

```bash
$ANSIBLE_VAULT;1.1;AES256

# or

$ANSIBLE_VAULT;1.2;AES256;vault-id-label
```

标题包含 `vault_id`、vault版本、vault加密方式和vault-id标签，用分号分隔