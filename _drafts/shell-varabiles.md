## <div style="color:#369">[万物皆于变与不变之间]  **Shell脚本之变量** </div>

&ensp;&ensp;&ensp;&ensp;变量这个东西，大概是大家学习一门语言首先接触的东西。
那么什么是变量呢，可以这样理解，变量就是一个指向真实数据的指针，我们可以对它进行创建，赋值，以及删除操作。不落俗套，shell脚本中的变量和众多的语言相似。


#### <div style="color:#369">变量类型</div>

&ensp;&ensp;&ensp;&ensp;**shell中的变量主要分为三类**

+ 一种是系统变量, 用来控制操作系统的一些行为
+ 第二种是特殊变量, shell脚本中已经定义的一些变量，用来访问当前运行脚本的一些属性和状态
+ 第三种是用户自定义变量, 用一些合法的字符串定义

&ensp;&ensp;&ensp;&ensp;函数名的合法字符为a-zA-Z,数字,下划线(_)
一般，shell变量名是大写字符组成

*合法变量*

```shell
_ALI
TOKEN_A
VAR_1
VAR_2
```

*非法变量名*

```shell
2_VAR
-VARIABLE
VAR1-VAR2
VAR_A!
```


#### <div style="color:#369">变量基础操作</div>

**定义变量**

```shell
variable_name=variable_value
```
例如:
```shell
NAME="Zara Ali"
```


#### <div style="color:#369">变量高级操作</div>

#### <div style="color:#369">变量被赋值路径字符串之后不能被重新赋值</div>


