### <div style="color:#369"> 周报 </div>

###### <div style="color:#369"> 上周成果 </div> 

+ 测试出了第一种方法(利用加了水印的图片的频域和水印图像的频域做差，得出原图)的不可性 

**解释:**
&ensp;&ensp;这种方法从理论上是不可行的，因为本来利用频域进行水印叠加，本来就是利用了频域的相关变化对空域的变化的影响特别小的特点。所以, 不管是用水印从加了水印的图片, 或者是没有加了水印的图片，分离原图时，用加了水印的图片的频域和原水印的频域作差，得到的图片两者没有肉眼可见的区别，无法辨识。



+ 了解了几种其他的逆水印的方法

 1. 盲源分析

 2. 基于IWT和SVD的数字图像逆水印算法

 3. 基于排序和直方图修改的可逆信息隐藏

 4. 基于八邻域像素的可逆信息隐藏的方法

 5. 基于奇异值分解的近无损的可逆信息隐藏的相关方法

 6. 基于路径搜索的可逆信息隐藏的方法



###### <div style="color:#369"> 问题和收获 </div>

&ensp;&ensp;&ensp;&ensp;在图片处理中的对加水印图和原图的频域相互做残差时，运行出现错误

```shell
└─[134] *** Error in `/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3': free(): invalid next size (normal): 0x00000000011bf620 ***
 ======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7f1e2a2037e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x7fe0a)[0x7f1e2a20be0a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7f1e2a20f98c]
/usr/local/lib/libopencv_core.so.3.2(_ZN2cv3Mat10deallocateEv+0xc9)[0x7f1e2ad0a8b9]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3(_ZN2cv3Mat7releaseEv+0x4f)[0x405d1f]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3(_ZN2cv3MatD1Ev+0x18)[0x405b24]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x408665]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x40825a]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x407c12]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x406d7b]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3(_ZNSt6vectorIN2cv3MatESaIS1_EED1Ev+0x36)[0x406416]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x4043a4]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x404a91]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x4050d8]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f1e2a1ac830]
/mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3[0x402189]
======= Memory map: ========
00400000-0040e000 r-xp 00000000 08:04 664586                             /mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3
0060e000-0060f000 r--p 0000e000 08:04 664586                             /mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3
0060f000-00610000 rw-p 0000f000 08:04 664586                             /mnt/D/Developer/WorkPlace/Personal-Workplace-Temp/Algorithm/C++/WaterMark/bin/ff2t3
00e3b000-01375000 rw-p 00000000 00:00 0                                  [heap]
7f1e1c000000-7f1e1c021000 rw-p 00000000 00:00 0
7f1e1c021000-7f1e20000000 ---p 00000000 00:00 0
7f1e20c46000-7f1e21cec000 rw-p 00000000 00:00 0
7f1e21cec000-7f1e21cf2000 r-xp 00000000 08:01 2097758                    /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.3
7f1e21cf2000-7f1e21ef2000 ---p 00006000 08:01 2097758                    /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.3
7f1e21ef2000-7f1e21ef3000 r--p 00006000 08:01 2097758                    /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.3
7f1e21ef3000-7f1e21ef4000 rw-p 00007000 08:01 2097758                    /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.3
7f1e21ef4000-7f1e21f17000 r-xp 00000000 08:01 2097435                    /usr/lib/x86_64-linux-gnu/libgraphite2.so.3.0.1
7f1e21f17000-7f1e22116000 ---p 00023000 08:01 2097435                    /usr/lib/x86_64-linux-gnu/libgraphite2.so.3.0.1
7f1e22116000-7f1e22118000 r--p 00022000 08:01 2097435                    /usr/lib/x86_64-linux-gnu/libgraphite2.so.3.0.1
7f1e22118000-7f1e22119000 rw-p 00024000 08:01 2097435                    /usr/lib/x86_64-linux-gnu/libgraphite2.so.3.0.1
7f1e22119000-7f1e2211e000 r-xp 00000000 08:01 2101116                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f1e2211e000-7f1e2231d000 ---p 00005000 08:01 2101116                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f1e2231d000-7f1e2231e000 r--p 00004000 08:01 2101116                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f1e2231e000-7f1e2231f000 rw-p 00005000 08:01 2101116                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f1e2231f000-7f1e22321000 r-xp 00000000 08:01 2104349                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f1e22321000-7f1e22521000 ---p 00002000 08:01 2104349                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
```


##### <div style="color:#369"> 造成该问题的原因 </div>

&ensp;&ensp;&ensp;&ensp;此错误是由内存错误, 可能造成这个问题的原因

+ 用`free()`释放, 没有`malloc()`分配内存的指针
+ 用`delecte()`删除一个没有被`new`创建的对象
+ 重复用`free()/delete()`方法释放指针内存或者删除对象
+ 内存溢出
+ 相关内存不能访问

