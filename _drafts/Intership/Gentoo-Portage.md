
#Gentoo中的软件包的卸载

安装依赖检查工具,equery, equery是一个检查gentoo的portage依赖的工具,存在于app-portgage/gentoolkit包中

```
   emerge app-portage/gentoolkit

```



####方法一:


使用emerge --depclean packagename 

```

//查看软件包是否还存在依赖

equery --depends packagename 

//如果没有其他依赖,卸载软件
emerge --depclean packagename

```



#Gentoo添加sudo用户

*添加sudo命令*

```
 emerge app-admin/sudo

```

> sudo这个包会自动在/etc目录下建立一个sudoers文件,用来对sudo用户的配置


*配置*

```
 #  /etc/sudoers
 #  配置语法:
 #  登陆用户名 主机 = (可以指定被执行的用户) 可被执行的命令  

 git ALL = (ALL) ALL #允许git用户,从任何主机上使用sudo执行所有的命令
 

```
