> 今天在进行Matlab编程的时，用之前写的代码在自己机子上运行失败，报错为Could not start Excel server for import, 十分郁闷。于是在网上找了些资料，总算解决了问题，现在将几种解决方法写下来，希望能够帮助遇到同样问题的朋友。

<span style="color:#338DCD">**情况一： 软件版本兼容问题**</span>

   首先考虑是Matlab和Excel的兼容问题，我遇到的就是两个软件的兼容性问题，我Matlab装的是2010a版本,而Excel则是2016版本，两者不兼容。</br></br>
   <u>**解决办法很粗暴:**  就是讲Excel-2016版本卸载，然后重新装office-2007版本，然后程序就运行畅通无阻了。</u>

<span style="color:#338DCD">**情况二： Excel软件设置问题**</span>

   MathLab是通过调用Windows下的Dom Server来进行Excel文件读取的，所以确定Excel软件的是允许和其他软件进行数据交换的。</br>
   <u>**解决方法:** 打开excel->excel选项->高级->最下面的常规-> "忽略使用动态数据交换（DDE）的其他应用程序"。 查看是否勾选这个选项，如果勾选这个选项，就把他取消勾选。</u>


   <span style="color:#338DCD">**情况二： Excel软件权限问题**</span>

   有时候可能是因为执行Excel需要特殊的权限才导致出错。</br>
   <u>**解决方法:** 
   找到Excel软件的快捷方式，右键点击属性->选择兼容性->取消勾选"以管理员的身份运行该软件"
   </u>
  

