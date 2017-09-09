
<!-- MarkdownTOC -->

- [为甚么要学习Lingo软件](#为甚么要学习lingo软件)
- [Lingo基本语法](#lingo基本语法)

<!-- /MarkdownTOC -->


<a name="为甚么要学习lingo软件"></a>
# <span style="font-size:16px;color:#338DCD">为甚么要学习Lingo软件</span>

> Lingo软件主要擅长于解决线性规划问题，相对于其他软件来解决线性规划问题来说，Lingo软件
编程相对于简单，编程语言贴近数学模型，学习成本相对比较低。所以，建议大家学习一下Lingo软件。


<a name="lingo基本语法"></a>
# <span style="font-size:16px;color:#338DCD">Lingo基本语法</span>

>**<strong>注释</strong>**
 
    在Lingo中感叹号(!)表示注释的开始,末尾有那个分号(;)， 可跨多行

```lingo
  !集部分;
  sets:
    students:sex,age;
  endsets
```

>**<strong>集</strong>**
 
    Lingo中的集是一群相互联系的对象，和数学中的集合定义差不多。
    其中Lingo中有两种类型的集:
    原始集(primitive set)  和  派生集(derive set)。
    原始集是由一些最基本的对象组成的。
    派生集是用一个或多个其他集来定义的,它的成员来自于存在的集合。

LP(Linear Programming)数学模型:

   $$
   \min 2x_1+3x_2
   $$

   $$
   s.t    
   \begin{cases}
     x_1+x_2  \ge 350 \\
     x_1      \ge 100 \\
     2x_1+x_2 \le 600 \\
     x_1,x_2  \ge 0
   \end{cases}
   $$

Lingo编程实现模型:

```LinGo

   min=2*x1+3*x2;
   x1+x2>350;
   x1>100;
   2*x1+x2<600;

```