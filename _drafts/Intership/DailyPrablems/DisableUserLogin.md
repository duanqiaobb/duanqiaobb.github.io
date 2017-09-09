#### <div style="color:#369"> Linux用户管理 ----- 禁止用户登陆</div>

<div style="background-color:#051e30; padding-left: 4px; border-width:1px 1px 1px 4px; border-style: solid; border-color:#289ff4; color:#fff">

&ensp;&ensp;&ensp;&ensp;Linux下的用户主要分为两种，一种是系统用户，一种是普通管理用户, 系统用户和普通用户的区别就是,添加的系统用户不会出现在登陆界面，而添加的普通用户则会默认的出现在登陆界面上.
</div>

##### <div style="color:#369">如何分辨系统用户和普通管理用户</div>

<div style="background-color:#051e30; padding-left: 4px; border-width:1px 1px 1px 4px; border-style: solid; border-color:#289ff4; color:#fff">
&ensp;&ensp;&ensp;&ensp;普通管理用户和系统用户是Linux中的两个用户组，两个用户组是通过UID的范围来划分的，Linux系统默认的限定系统用户的UID的范围为 100~499, 普通管理用户的UID范围为1000-60000, 范围的定义在`etc/login.defs`文件中

</div>

```

   #/etc/login.defs文件中

   # Min/max values for automatic uid selection in useradd
   #
   # SYS_UID_MIN to SYS_UID_MAX inclusive is the range for
   # UIDs for dynamically allocated administrative and system accounts.
   # UID_MIN to UID_MAX inclusive is the range of UIDs of dynamically
   # allocated user accounts.
   #
   UID_MIN                  1000
   UID_MAX                 60000
   # System accounts
   SYS_UID_MIN               100
   SYS_UID_MAX               499

   # Min/max values for automatic gid selection in groupadd
   #
   # SYS_GID_MIN to SYS_GID_MAX inclusive is the range for
   # GIDs for dynamically allocated administrative and system groups.
   # GID_MIN to GID_MAX inclusive is the range of GIDs of dynamically
   # allocated groups.
   #
   GID_MIN                  1000
   GID_MAX                 60000
   # System accounts
   SYS_GID_MIN               100
   SYS_GID_MAX               499

```
 
<div style="background-color:#051e30; padding-left: 4px; border-width:1px 1px 1px 4px; border-style: solid; border-color:#289ff4; color:#fff">
&ensp; &ensp; &ensp; &ensp; 文件中包含了系统用户和普通管理用户之间的UID范围,同时指定了系统用户组和普通管理用户组之间的GID范围,用户也可以修改.

</div>

##### <div style="color:#369">禁止用户从登陆界面登陆</div>


<div style="background-color:#051e30; padding-left: 4px; border-width:1px 1px 1px 4px; border-style: solid; border-color:#289ff4; color:#fff">
&ensp;&ensp;&ensp;&ensp;平常我们通过adduser xx 来添加用户，默认添加的是普通管理用户，并且是可以通过登陆界面来登陆的,那么我们如何禁止我们创建的用户通过登陆界面来登陆系统呢，
</div>

+ 用<span style="color:#c7254e;background-color:#f9f2f4;border:1px solid #f9f2f4; margin-left: 10px; margin-right: 10px; border-radius:6px;">adduser</span>命令创建用户的时候，指定
<span style="color:#c7254e;background-color:#f9f2f4;border:1px solid #f9f2f4; margin-left: 10px; margin-right: 10px; border-radius:6px;">--system</span>
选项,　系统用户没密码而且不能登陆系统的,只能用来运行程序

```
   adduser --system xxx 

```

+ 用   <span style="color:#c7254e;background-color:#f9f2f4;border:1px solid #f9f2f4; margin-left: 10px; margin-right: 10px; border-radius:6px;">adduser</span>
+命令创建用户的时候，指定 <span style="color:#c7254e;background-color:#f9f2f4;border:1px solid #f9f2f4; margin-left: 10px; margin-right: 10px; border-radius:6px;">--disable-login</span>
选项未设置密码的用户进行登陆系统，但是如果设置了密码，那么用户就可以进行登陆

```
   adduser --disable-login xxx

```
**Note:** 用户仍然可以通过ssh进行登陆


+ 如果用户已经被创建，想禁用该用户从登陆界面登陆,我们可以通过修改你的界面管理器相关配置文件来实现，或者直接通过修改用户的uid范围到  <span style="color:#c7254e;background-color:#f9f2f4;border:1px solid #f9f2f4; margin-left: 10px; margin-right: 10px; border-radius:6px;">1-500
</span>

*检测系统是否安装了AccountsService*

> AccountsService是一个D-Bus服务用来查询,管理用户的信息

```
Jonans@jonans-Aspire-E1-571G /mnt/D/Developer/WorkPlace/Blog/Linux
master* $  dpkg -S accountsservice 


gir1.2-accountsservice-1.0: /usr/share/doc/gir1.2-accountsservice-1.0
gir1.2-accountsservice-1.0: /usr/share/doc/gir1.2-accountsservice-1.0/copyright
libaccountsservice0:amd64: /usr/lib/x86_64-linux-gnu/libaccountsservice.so.0
accountsservice: /usr/share/doc/accountsservice/TODO
accountsservice: /usr/share/doc/accountsservice/copyright
libaccountsservice0:amd64: /usr/share/doc/libaccountsservice0/copyright
libaccountsservice0:amd64: /usr/share/doc/libaccountsservice0/changelog.Debian.gz
accountsservice: /usr/lib/accountsservice
libaccountsservice0:amd64: /usr/lib/x86_64-linux-gnu/libaccountsservice.so.0.0.0
accountsservice: /usr/share/doc/accountsservice/changelog.Debian.gz
accountsservice: /usr/share/doc/accountsservice
accountsservice: /usr/share/doc/accountsservice/README
libaccountsservice0:amd64: /usr/share/doc/libaccountsservice0
gir1.2-accountsservice-1.0: /usr/share/doc/gir1.2-accountsservice-1.0/changelog.Debian.gz
accountsservice: /usr/lib/accountsservice/accounts-daemon
```
> 有上图所述的输出说明，系统安装了AccountService服务


*修改配置文件针对使用了AccountsService的系统来说, /var/lib/AccountsService/users/username(你修改用户名)*

```
  [User]
  SystemAccount=true
```

*修改配置文件(未安装AccountService服务并使用lightdm显示管理器的系统), /etc/lightdm/users.conf

```
#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess username(你的用户名)  #这里是在登陆界面隐藏哪些用户
hidden-shells=/bin/false 
```

**Note:** 这种方法只是禁用了用户从登陆界面但是没有禁用用户通过ssh或者ftp登陆





##### <div style="color:#369"> 禁止用户通过shell登陆，同时禁用ssh，ftp的方式登陆系统</div>

```shell

# 禁止用户远程登陆

# 通过修改/etc/passwd文件
username,,,:/home/username:/usr/sbin/nologin(有的系统为/sbin/nologin, 具体根据nologin文件存在在哪而定)

```

###### <div style="color:#369"> 如果你只是想禁用ssh登陆，而允许shell登陆以及其他远程登陆,如ftp等</div>

```shell 
#保持用户从shell登陆
username,,,:/home/username:/bin/bash(有的系统为/sbin/nologin, 具体根据nologin文件存在在哪而定)

#只禁用ssh登陆
#通过修改/etc/ssh/sshd_config

AllowUsers username1 username2 #指定允许ssh登陆的用户

```
