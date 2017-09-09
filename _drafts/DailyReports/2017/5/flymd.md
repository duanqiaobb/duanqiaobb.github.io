- [盲源分离算法 (blind singal processing,BSP)](#org080a47f)
  - [盲信号分离的相关算法](#orgabf6f93)
  - [盲信号提取技术](#org2a122dc)
  - [盲信号处理算法的基本理论](#org74758bf)
  - [盲信号处理的数学模型](#org12c9c4d)
    - [线性瞬时混合模型](#orgdac6ab1)


<a id="org080a47f"></a>

# 盲源分离算法 (blind singal processing,BSP)

&ensp;&ensp; 盲信号处理(blind singal processing, BSP) 就是在传输信道特性未知，输入信息位置或仅有少量先验知识的情况下，从系统的输出信号中分离或估计源信号的波形 盲信号处理可以分为相互关联而研究目标有所区别的子领域，如盲源分离(blind source speparation,BSS)、盲信号提取(blind singal extraction,BSE)、盲反卷积（blind deconvolution） 盲均衡(blind equalization)、盲辨识(blind identification)。


<a id="orgabf6f93"></a>

## 盲信号分离的相关算法

-   基于反馈神经网络的盲源分离
-   基于高阶统计的联合对角化盲源分离方法
-   主分量法，独立分量分析法，基于最小互信息量的独立分量分析方法
-   基于熵最大思想的盲源分离方法
-   基于独立分量分析的快速分离算法FastICA
-   自然梯度算法
-   时频分析方法
-   非独立分量的FastICA算法
-   状态空间法


<a id="org2a122dc"></a>

## 盲信号提取技术

-   基于峰度的顺序提取方法
-   线性混合模型的多个源同时抽取算法
-   基于二阶统计量的相关源的盲信号提取
-   基于四阶累计量的盲信号提取方法


<a id="org74758bf"></a>

## 盲信号处理算法的基本理论

&ensp;&ensp; 盲信号处理算法主要包括两大任务：

1.  构造目标函数
2.  应用合适的数值优化方法使得目标函数达到最大值或最小值。


<a id="org12c9c4d"></a>

## 盲信号处理的数学模型

&ensp;&ensp; 根据源信号信号不同的混合方式，盲信号处理可分为: 线性瞬时混合模型、线性卷积模型和非线性混合模型。

fLyMd-mAkEr
<a id="orgdac6ab1"></a>

### 线性瞬时混合模型

&ensp;&ensp; 线性混合信号系统数学模型为:

\begin{equation}
x(k) = As(k)+n(k)
\end{equation}

其中: \(x(k) = [x_1(k),x_2(k),...,x_m(k)]^T\) 是 \(M\) 维观测信号矢量： \(s(k) = [s_1(k), s_2(k), ..., s_N(k)]^T\) 是 \(N\) 维未知源信号矢量;

