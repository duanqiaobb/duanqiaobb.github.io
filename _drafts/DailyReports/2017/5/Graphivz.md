<div style="color:#369">Graphivz的几个使用示例</div>

![img](data/2017/graphviz_example2.png)

<div style="color:#369">修改节点的颜色</div>

![img](data/2017/graphviz_example3.png)

<div style="color:#369">以图片为节点</div>

![img](data/2017/graphivz_example4.png)

&ensp;&ensp;设置节点为图片的时候， `shape` 必须设置为 `none`

<div style="color:#369">子图的绘制</div>

![img](data/2017/graphviz_example5.png)

&ensp;&ensp; 子图的名称必须设置为 `cluster` 开头,否则 `graphviz` 无法识别。

<div style="color:#369">数据结构的可视化</div>

-   hash表的数据结构

![img](data/2017/graphviz_example6.png)

<div style="color:#369">对上图进行circor布局重绘</div>

![img](data/2017/graphviz_example7.png)

<div style="color:#369">节点式的hash表实例</div>

![img](data/2017/graphivz_example8.png)

<div style="color:#369">软件模块组成图</div>

-   Apache httpd模块关系

![img](data/2017/graphivz_example9.png)

![img](data/2017/graphviz_example10.png)

<div style="color:#369">状态机</div>

1.  有限自动机示意图

```dot
digraph automata_0 {
  size = "8.5, 11";
  fontsize = 10;
  node [shape=circle, fontsize = 10];
  edge [fontsize= 10];

  0 [style=filled, color=lightgrey];
  2 [ shape = doublecircle];
  0 -> 2 [label="a"];
  0 -> 1 [label="other"];
  1 -> 2 [label="a"];
  1 -> 1 [label="other"];
  2 -> 2 [label="a"];
  2 -> 1 [label="other"];

  "Machine: a" [ shape = plaintext];
}
```

![img](data/2017/graphivz_example11.png)

<div style="color:#369">OSGI中模块的生命周期图</div>

<div style="color:#369">抽象语法树</div>

<div style="color:#369">简单的UML类图</div>

![img](data/2017/graphivz_example14.png)

<div style="color:#369">状态图</div>

<div style="color:#369">时序图</div>
