####<center><strong>WordPress Series- Problems and Pits</strong></center>

>这篇文章记录了我在研究WordPress中的遇到过的小问题，因为问题比较小，解决方法可能也就一句话，我就用一篇文章来记录他们。

---


1. ######**WordPress文章链接形式设置为伪静态形式，造成链接失效**

   在WordPress中链接的默认形式为日期+文章标题的形式，比如你的一篇文章标题为:**Hello WordPress**</br>
   那么WordPress会自动帮你生成这种形式的链接:[http://youhostname/year/month/day/Hello WordPress]()</br>
   这种链接形式是采用的伪静态，看网上有博文说，wordpress的伪静态是通过Apache的rewrite来实现的，博主也给出了解决方案，但是我在我的wordpress文件夹里并没有发现有.htaccess文件，可能因为这个文件的缺失，才导致伪静态失效的吧。

---
   **解决方法：**在wordpress的管理后台，选择永久链接选项，选择原文链接形式或者数字链接形式皆可以。(原文链接形式-[http://youhostname/?p=123](),数字链接形式-[http://youhostname/archives/123]())
  