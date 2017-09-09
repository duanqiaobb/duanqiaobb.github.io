##### <div style="color:#369">Gentoo 图形界面配置 </div>


##### <div style="color:#369"> 启动 KDE 图形界面环境 </div>

```shell
  emerge --ask twm xterm

```


```shell
  nano ~/.xinitrc

  //.xinitrc文件添加如下命令
  exec startkde
```

```
   startx
```



##### <div style="color:#369">masked by: package.mask, ~amd64 keyword </div>

```shell
//编辑/etc/portage/make.conf,添加
ACCEPT_KEYWORDS="~amd64"

```

##### <div style="color:#369">masked by: package.mask, ~amd64 keyword </div>
