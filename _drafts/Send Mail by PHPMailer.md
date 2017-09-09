
#####  <center> Send Mail by PHPMailer</center> 

> 这几天项目中需要写一个邮箱激活注册的功能,其中之一就是要能够发邮件,没有经历去对PHP <font color='#6666'> mail() </font>内置函数进行封装,只好从万能的开源界找法子了,果断使用用PHPMailer.如果你不喜欢使用PHPMailer的话,你也可以使用其他类库如:
> SwiftMailer,ZendMail,eZComponents 等等

##### PHPMailer 的功能的简单介绍
&emsp;&emsp; __<span style="font-size:10px">PHPMailer的邮件发送功能主要分为两种:</span>__

- 使用本地的邮件服务器发送邮件,这需要你本地搭建一个邮件服务器(linux环境下自带了邮件服务器Sendmail直接使用即可,Window下就要下载相关的邮件服务器软件进行搭建了,如Foxmail) 
[*这里如何搭建邮件服务器就不赘述了*]
- 直接使用第三方邮件服务器,通过smtp,pop3进行连接进行邮件发送,有名的第三方邮件服务器有163邮箱,qq邮箱等(*我们使用这种方法进行发送邮件*)

   
