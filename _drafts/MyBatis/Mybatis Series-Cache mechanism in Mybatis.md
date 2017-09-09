
**目录**

<!-- MarkdownTOC -->

- 缓存机制
- 一级缓存
- 二级缓存
- 三级缓存

<!-- /MarkdownTOC -->

# <font color="#338DD" size="3" style="font-style:bold">缓存机制</font>
     大多ORM库为了减少数据库的压力和加速数据库访问速度，都会有相应的缓存机制，Mybatis也有相应的缓存机制。Mybatis的缓存层分为三层。


# <font color="#338DD" size="3" style="font-style:bold">一级缓存</font>

> update, delete ,save 凡是对数据进行修改的操作，一级缓存都会被清除。

# <font color="#338DD" size="3" style="font-style:bold">二级缓存</font>

> 二级缓存的生效条件是，sql会话必须提交。



# <font color="#338DD" size="3" style="font-style:bold">三级缓存</font>