# 盲源分离算法 (blind singal processing,BSP)

&ensp;&ensp; 盲信号处理(blind singal processing, BSP) 就是在传输信道特性未知，输入信息位置或仅有少量先验知识的情况下，从系统的输出信号中分离或估计源信号的波形 盲信号处理可以分为相互关联而研究目标有所区别的子领域，如:

-   盲源分离(blind source speparation,BSS)
-   盲信号提取(blind singal extraction,BSE)
-   盲反卷积（blind deconvolution）
-   盲均衡(blind equalization)、盲辨识(blind identification)。


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


## 盲信号提取技术

-   基于峰度的顺序提取方法
-   线性混合模型的多个源同时抽取算法
-   基于二阶统计量的相关源的盲信号提取
-   基于四阶累计量的盲信号提取方法


## 盲信号处理算法的基本理论

&ensp;&ensp; 盲信号处理算法主要包括两大任务：

1.  构造目标函数
2.  应用合适的数值优化方法使得目标函数达到最大值或最小值。


## 盲信号处理的数学模型

&ensp;&ensp; 根据源信号信号不同的混合方式，盲信号处理可分为: 线性瞬时混合模型、线性卷积模型和非线性混合模型。


### 线性瞬时混合模型

&ensp;&ensp; 线性混合信号系统数学模型为:


<div class="figure">
<p><img src="ltximg/BSP_da989f80eca58d5a7e6beb1b360c34d57f8c2336.png" alt="BSP_da989f80eca58d5a7e6beb1b360c34d57f8c2336.png" /></p>
</div>

其中:

<img src="ltximg/BSP_063d2ea37444c33880b9b757a1fa2cee855425ab.png" alt="BSP_063d2ea37444c33880b9b757a1fa2cee855425ab.png" /> 是 <img src="ltximg/BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" alt="BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" /> 维观测信号矢量：

<img src="ltximg/BSP_ddd17bfadab8badad5f85a06ae9640e2b058d4a3.png" alt="BSP_ddd17bfadab8badad5f85a06ae9640e2b058d4a3.png" /> 是 <img src="ltximg/BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" alt="BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" /> 维未知源信号矢量;

<img src="ltximg/BSP_709af9ee3c84af53a48779d3bc58fb1b754965d5.png" alt="BSP_709af9ee3c84af53a48779d3bc58fb1b754965d5.png" /> 是 <img src="ltximg/BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" alt="BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" /> 维加性观测噪声; <img src="ltximg/BSP_e3e2119223514d0d4138267860fe21ec674b7336.png" alt="BSP_e3e2119223514d0d4138267860fe21ec674b7336.png" /> 为 <img src="ltximg/BSP_f773b4f636fa4e98ba7f9c4494e6b7c36c3e317d.png" alt="BSP_f773b4f636fa4e98ba7f9c4494e6b7c36c3e317d.png" /> 维未知混合矩阵。 每个观测向量 <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 只是源向量 <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" /> 的线性组合。

&ensp;&ensp; 其中盲信号分离的任务就是依据某一准则求出分离矩阵 <img src="ltximg/BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" alt="BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" /> , 通过 <img src="ltximg/BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" alt="BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" /> 从观测信号 <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 中恢复出 <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" />, 设 <img src="ltximg/BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" alt="BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" /> 为源信号的估计矢量， 则盲信号分离系统的数学模型为:


<div class="figure">
<p><img src="ltximg/BSP_c74d8f49f9fae0c56b295495afc3d171bb9934ed.png" alt="BSP_c74d8f49f9fae0c56b295495afc3d171bb9934ed.png" /></p>
</div>

&ensp;&ensp; 其中:

<img src="ltximg/BSP_96ee5d355b6d7a668587207071ef85be6b7c1627.png" alt="BSP_96ee5d355b6d7a668587207071ef85be6b7c1627.png" /> 为源信号的估计矢量； <img src="ltximg/BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" alt="BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" /> 为 <img src="ltximg/BSP_9879f547ed871eb818544cf8860b473824302a7b.png" alt="BSP_9879f547ed871eb818544cf8860b473824302a7b.png" /> 维分离矩阵; <img src="ltximg/BSP_a2b343fe2a09ba18dca7d2a770594ba330ad2b96.png" alt="BSP_a2b343fe2a09ba18dca7d2a770594ba330ad2b96.png" /> 为 <img src="ltximg/BSP_bd22f7988285158de8130152577a4e0e0febbdb6.png" alt="BSP_bd22f7988285158de8130152577a4e0e0febbdb6.png" /> 置换矩阵; <img src="ltximg/BSP_35dc26ab0b4d9c0abc05693f77907ecb1a6d91b2.png" alt="BSP_35dc26ab0b4d9c0abc05693f77907ecb1a6d91b2.png" /> 为 <img src="ltximg/BSP_bd22f7988285158de8130152577a4e0e0febbdb6.png" alt="BSP_bd22f7988285158de8130152577a4e0e0febbdb6.png" /> 对角矩阵。


### 线性卷积混合模型

&ensp;&ensp; 更一般的情形，观测信号为源信号不同时延的线性组合即源型号的卷积混合，多通道卷积混合信号的数学模型为:


<div class="figure">
<p><img src="ltximg/BSP_5ce54f76f606707f9e6d7e5ae9ed9cacc5639bcf.png" alt="BSP_5ce54f76f606707f9e6d7e5ae9ed9cacc5639bcf.png" /></p>
</div>

&ensp;&ensp; 其中: <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 、 <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" /> 的物理意义与瞬时混合系统相同; <img src="ltximg/BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" alt="BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" /> 为 <img src="ltximg/BSP_f773b4f636fa4e98ba7f9c4494e6b7c36c3e317d.png" alt="BSP_f773b4f636fa4e98ba7f9c4494e6b7c36c3e317d.png" /> 维未知混合矩阵， 由于 <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 为 <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" /> 与 <img src="ltximg/BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" alt="BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" /> 的 卷积，所以 <img src="ltximg/BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" alt="BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" /> 又称为 混合-冲激响应矩阵。

&ensp;&ensp; 盲解卷积是在已知 <img src="ltximg/BSP_7ef2c21f6c11fdf164f75f0925bdb7d60218b9c0.png" alt="BSP_7ef2c21f6c11fdf164f75f0925bdb7d60218b9c0.png" />, 但未知 <img src="ltximg/BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" alt="BSP_80d38f33913f8318337fa30a1f5e02c936544891.png" /> 和 <img src="ltximg/BSP_4a38d101504c4cf8a34cc3d7571c49f8c340b28f.png" alt="BSP_4a38d101504c4cf8a34cc3d7571c49f8c340b28f.png" /> 的情况下估计 <img src="ltximg/BSP_2e2cfab9775af53b83d7534e9a97ce1eeaf70848.png" alt="BSP_2e2cfab9775af53b83d7534e9a97ce1eeaf70848.png" /> 。 设 <img src="ltximg/BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" alt="BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" /> 为源信号的 估计矢量，则解盲卷积系统的数学模型为：


<div class="figure">
<p><img src="ltximg/BSP_48bc2191110c4972fa7b501432840f5616db1cfa.png" alt="BSP_48bc2191110c4972fa7b501432840f5616db1cfa.png" /></p>
</div>

其中: <img src="ltximg/BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" alt="BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" /> 为 <img src="ltximg/BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" alt="BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" /> 维矢量; <img src="ltximg/BSP_eff73c3873cfd81e4c0b4862f036f32313eb3051.png" alt="BSP_eff73c3873cfd81e4c0b4862f036f32313eb3051.png" /> 为 <img src="ltximg/BSP_9879f547ed871eb818544cf8860b473824302a7b.png" alt="BSP_9879f547ed871eb818544cf8860b473824302a7b.png" /> 。


### 非线性混合模型

&ensp;&ensp; 线性混合模型的一个自然拓广就是非线性混合模型，非线性混合模型为:


<div class="figure">
<p><img src="ltximg/BSP_b0d15284adaebafa3c3f10c60a2c237c6e0f1687.png" alt="BSP_b0d15284adaebafa3c3f10c60a2c237c6e0f1687.png" /></p>
</div>

&ensp;&ensp; 其中: <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 是 <img src="ltximg/BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" alt="BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" /> 维观测信号矢量; <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" /> 是 <img src="ltximg/BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" alt="BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" /> 维未知源信号矢量; <img src="ltximg/BSP_709af9ee3c84af53a48779d3bc58fb1b754965d5.png" alt="BSP_709af9ee3c84af53a48779d3bc58fb1b754965d5.png" /> 是 <img src="ltximg/BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" alt="BSP_24a8fd5260b6f3162649874964e8dd9a82666bac.png" /> 维加性噪声，且与信号统计独立; <img src="ltximg/BSP_6710a411500fa49e62c0f5c0d0fc579b23336cb8.png" alt="BSP_6710a411500fa49e62c0f5c0d0fc579b23336cb8.png" /> 为未知的可逆实值非线性混合函数。 &ensp;&ensp; 非线性盲信号处理就是通过观测信号 <img src="ltximg/BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" alt="BSP_58c64462a74b8dfd4fd4eebb2c8904afedad9d5d.png" /> 来找到一组映射 <img src="ltximg/BSP_52add99f9f5613baf4e7ff6ab5183e708a89c188.png" alt="BSP_52add99f9f5613baf4e7ff6ab5183e708a89c188.png" /> 使得通过 <img src="ltximg/BSP_832b85d783d81a7c0cc6f690c6403df6ef9fabc8.png" alt="BSP_832b85d783d81a7c0cc6f690c6403df6ef9fabc8.png" /> 尽可能恢复源信号 <img src="ltximg/BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" alt="BSP_95ac53a2e3a53b9562c61c665940a3c97147101c.png" /> , 数学模型为：


<div class="figure">
<p><img src="ltximg/BSP_bd7c286e55ec674ffea33d2cac659b250b2d8d20.png" alt="BSP_bd7c286e55ec674ffea33d2cac659b250b2d8d20.png" /></p>
</div>

其中: <img src="ltximg/BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" alt="BSP_818fc322d0ddea3053e4c659f1c379708a65681d.png" /> 为 <img src="ltximg/BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" alt="BSP_3c490df69ad88165ff2475dc00845d614664ae01.png" /> 维输出。


## 盲信号分离方法


### 独立分量分析 (independent component analysis, ICA)

&ensp;&ensp; 在利用独立分量分析法解决盲源分离问题时，为得到确定的解，需要进行如下约束:

1.  各源信号 <img src="ltximg/BSP_057f583ebfc103622f6f04428e24c9d34191bdb4.png" alt="BSP_057f583ebfc103622f6f04428e24c9d34191bdb4.png" /> 为 0 均值、实随机变量，且各源信号之间统计独立。

2.  源信号的维数和观测信号维数相同，即 <img src="ltximg/BSP_8e22b738b86a7e58f5cec62ef29ce771d6cd42f7.png" alt="BSP_8e22b738b86a7e58f5cec62ef29ce771d6cd42f7.png" /> 。

3.  源信号 <img src="ltximg/BSP_795e810c919c589923bc3534651675157e67dc4c.png" alt="BSP_795e810c919c589923bc3534651675157e67dc4c.png" /> 中至少有一个为高斯分布。

4.  噪声很小可以忽略。

&ensp;&ensp; 独立分量分析的目的是通过学习求得 <img src="ltximg/BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" alt="BSP_8dd3782f08f0a21155296eb2f0f1c72897615c4b.png" /> ，使得输出各分量 <img src="ltximg/BSP_fbe1184bdff9ad22e3acfc6b8e6666875720ea93.png" alt="BSP_fbe1184bdff9ad22e3acfc6b8e6666875720ea93.png" /> 尽可能统计独立。


### 独立分量分析目标函数——峰度

&ensp;&ensp; 中心极限定理表明，在一般的条件下，当独立随机变量的个数增加时，其和的分布趋于高斯分布。 所以两个 变量和的分布总比其中任一变量趋于高斯，故可以用非高斯性来度量独立性。常用的非高斯度量有峰值和负熵。负熵可以通过KL散度（Kullback-Leiblerdi-vergence,KL散度） 来度量。

&ensp;&ensp; 对于0均值实信号而言，峰值即为其四阶统计量，其经典定义为:


<div class="figure">
<p><img src="ltximg/BSP_33eaf97073d672a5c3aacfaf6d5a8d17f2f8a605.png" alt="BSP_33eaf97073d672a5c3aacfaf6d5a8d17f2f8a605.png" /></p>
</div>

其中: <img src="ltximg/BSP_da46e9a1e6be3426f6a8ecacf2f42c9d5cdeed79.png" alt="BSP_da46e9a1e6be3426f6a8ecacf2f42c9d5cdeed79.png" /> 表示统计期望值。对上式归一化，即：


<div class="figure">
<p><img src="ltximg/BSP_08cf49481bfec37dee77b35a477c7e521dc5062f.png" alt="BSP_08cf49481bfec37dee77b35a477c7e521dc5062f.png" /></p>
</div>

&ensp;&ensp; 当信号方差为1时，有:


<div class="figure">
<p><img src="ltximg/BSP_e6bc3a71425bb938c7b79dd332e8cc9ddf4ad87f.png" alt="BSP_e6bc3a71425bb938c7b79dd332e8cc9ddf4ad87f.png" /></p>
</div>

这说明峰度可以化成标准的四阶矩形式，对于高斯变量的四阶矩是 <img src="ltximg/BSP_c6ec2ad40346afb4a54531481daec879ff0969ed.png" alt="BSP_c6ec2ad40346afb4a54531481daec879ff0969ed.png" />, 因此高斯变量的峰度为0。 峰度为负则随机变量称为亚高斯信号，峰度为正则随机变量称为超高斯信号。一般的，通信信号为亚高斯信号，语音信号 为超高斯信号。
