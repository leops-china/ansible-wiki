# ssh登录二次验证

本次二次认证方式使用 Google 身份验证器

## 资源

谷歌身份验证器pam
https://github.com/google/google-authenticator-libpam

移动app源码
https://github.com/google/google-authenticator

Google 身份验证器商店地址
https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2

Google 身份验证器app下载地址
https://storage.evozi.com/apk/dl/16/09/05/com.google.android.apps.authenticator2.apk?h=4FgH1NXU1UokEVwXN5sVBw&t=1499507124

## 服务器配置
同步时间
```bash
/usr/sbin/ntpdate asia.pool.ntp.org >>/var/log/ntpdate.log
```
安装依赖包
```bash
yum install pam-devel make gcc-c++ wget -y
```
下载谷歌身份验证器包
```bash
wget https://github.com/google/google-authenticator-libpam/archive/1.03.tar.gz
```
编译安装
```bash
tar zxf 1.03.tar.gz 
cd google-authenticator-libpam-1.03/
./bootstrap.sh
./configure 
make 
make install
```
复制google 身份验证器pam模块到系统下
```bash
cp /usr/local/lib/security/pam_google_authenticator.so /lib64/security/
```
修改ssh的pam登录模块为pam_google_authenticator.so
```bash
# cat /etc/pam.d/sshd 
#%PAM-1.0
#auth	   required	pam_sepermit.so
auth	   required	pam_google_authenticator.so
auth       include      password-auth
account    required     pam_nologin.so
account    include      password-auth
password   include      password-auth
# pam_selinux.so close should be the first session rule
session    required     pam_selinux.so close
session    required     pam_loginuid.so
# pam_selinux.so open should only be followed by sessions to be executed in the user context
session    required     pam_selinux.so open env_params
session    optional     pam_keyinit.so force revoke
session    include      password-auth
```

修改ChallengeResponseAuthentication 为yes
```bash
sed -i 's#^ChallengeResponseAuthentication no#ChallengeResponseAuthentication yes#' /etc/ssh/sshd_config
```
生成key，手机app上添加账户所需要的。
```bash
./google-authenticator 

Do you want authentication tokens to be time-based (y/n) y
https://www.google.com/chart?chs=200x200&chld=M|0&cht=qr&chl=otpauth://totp/root@node1%3Fsecret%3D6GY7RPMXCVWN6HHVSSX4XM3WWssuer%3Dnode1          ## 二维码
Your new secret key is: 6GY7RPMXCVWN6HHVSSX4XM3WWI    ## 密钥
Your verification code is 467014
Your emergency scratch codes are:    ##后备验证码保存好，永久可用。
  66339556
  56534014
  64738014
  23546970
  43468735

Do you want me to update your "/root/.google_authenticator" file? (y/n) y  ## 配置文件

Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y

By default, tokens are good for 30 seconds. In order to compensate for
possible time-skew between the client and the server, we allow an extra
token before and after the current time. If you experience problems with
poor time synchronization, you can increase the window from its default
size of +-1min (window size of 3) to about +-4min (window size of
17 acceptable tokens).
Do you want to do so? (y/n) y 

If the computer that you are logging into isn't hardened against brute-force
login attempts, you can enable rate-limiting for the authentication module.
By default, this limits attackers to no more than 3 login attempts every 30s.
Do you want to enable rate-limiting (y/n) y
```
重启ssh服务
```bash
service sshd restart
```

> 重启后，不要关闭当前窗口，以免配置错误出现登录不了服务器。

## 手机端配置

本次使用安卓手机，下载app并安装。苹果手机在苹果商店里搜索google authenticator并安装。

添加帐号


![image.png](/images/advanced/ssh-2step01.png)

![image.png](/images/advanced/ssh-2step02.png)

输入刚才生成的key


![image.png](/images/advanced/ssh-2step03.png)

点击添加

![image.png](/images/advanced/ssh-2step04.png)


这时，点击完成后，可以看到没美30秒一次变换的验证码

![image.png](/images/advanced/ssh-2step05.png)



## ssh命令登录
```bash
[root@master ~]# ssh 192.168.77.129
Verification code:                                   # 先输入app上的验证码
Password:                                                # 在输入root密码
Last login: Sat Jul  8 15:55:59 2017 from 192.168.77.1
[root@node1 ~]# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0C:29:7D:D4:7A  
          inet addr:192.168.77.129  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe7d:d47a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:298600746 (284.7 MiB)  TX bytes:24281004 (23.1 MiB)
```
## xshell客户端登录

设置登陆方法为Keyboard Interactive

![image.png](/images/advanced/ssh-2step06.png)

先输入谷歌验证码

![image.png](/images/advanced/ssh-2step07.png)

再输入root密码

![image.png](/images/advanced/ssh-2step08.png)

成功登录

![image.png](/images/advanced/ssh-2step09.png)
