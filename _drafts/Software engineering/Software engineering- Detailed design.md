
**目录**


<!-- MarkdownTOC -->

- [概述](#概述)
- [过程设计工具](#过程设计工具)
- [过程设计中程序复杂度的度量](#过程设计中程序复杂度的度量)

<!-- /MarkdownTOC -->

---


<a name="概述"></a>
# <font color="#338DD" size="3" style="font-style:bold">概述</font>

    详细设计阶段是逻辑上将系统的每个功能都设计出来，并保证设计出的处理过程应该尽可能的简明易懂。
 
> 结构化程序设计
    
    定义: 如果一个程序的代码块仅仅通过顺序、选择和循环这3种基本控制进行连接，并且只有一个入口和一个出口，则称这
    个程序是结构化的。

    结构化程序设计的3种基本结构: 顺序、选择、循环。


<a name="过程设计工具"></a>
# <font color="#338DD" size="3" style="font-style:bold">过程设计工具</font>


> 程序流程图
  
   	定义: 程序流程图又称为程序框图，它是使用最广泛的描述过程设计的方法。


> 盒图
    
    定义：盒图又称为N-S图，是一种严格遵循结构程序设计精神的图形工具。

> PAD图
  
    定义: PAD图又名问题分析图, Problem analysis diagram, PAD图使用二维树形结构的图来表示程序的控制流。

> 判定表

    定义: 判定表能够简洁而无歧义的描述复杂的条件组合与应做的动作的对应关系。


> 判定树
  
    定义：判定树是判定表的变种，它也能清晰的表示复杂的条件组合与应做的动作之间的对应关系，同时判定树比
    判定表的形式简单，让人很容易看出其含义。

> 过程设计语言(PDL)

    定义: 过程设计语言，Process Design Language, 又称为伪码。它具有严格的关键字外部语法，用于定义控制结构和数据
    结构。


<a name="过程设计中程序复杂度的度量"></a>
# <font color="#338DD" size="3" style="font-style:bold">过程设计中程序复杂度的度量</font>

> 流图

    定义： 流图实际上是程序流程图的简化版，它仅仅描绘程序的控制流程，完全不表现对数据的具体操作以及分支和循环
    的具体条件。

    流图包含3个元素：结点，区域，控制流。其中结点又分为普通结点，和判定结点。 


  **计算环形复杂度的方法：**
    
环形复杂度，这里用$V(G)$表示;
    
$$
V(G) = E - N + 2 = P + 1 = 流图中的区域数  (E\Rightarrow流图中的边数，N\Rightarrow流图中的结点数,
P\Rightarrow 流图中的判定结点数)
$$

在程序过程设计中，模块规模 V(G) $\leq$ 10 为宜。

