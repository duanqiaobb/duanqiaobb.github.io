######  Restful API bugs in ThinkPHP framework

> 项目中用ThinkPHP 框架写Restful 风格式的接口,突然有点强烈想吐槽ThinkPHP中的Restful实现。好丑的说，对于有强迫症的我很难受好不好。ThinkPHP中的对Restful的路由和其他路由也不一样,会发生冲突。

> 下面我罗列一下我在开发中遇到的奇奇怪怪的问题。有些问题我不知道是不是bug,现在也没时间去看源码去找原因。这些问题随手记下来只有两个目的,一来,希望如果有知道的朋友,能告诉我为什么会这样,错在哪;二来,记录下来,等有时间了研究源码找找原因。

+ 问题1

     操作名+提交类型,这种写法时而奏效,时而不奏效
``` php
    public function userTelExist_get()
    {
         $user = new UserController;
         //手机号的格式要求
         $user_phone = I("get.phone", null, "/^1(3[0-9]|4[57]|5[0-35-9]|8[0-9]|70)\\d{8}$/");

         if (empty($user_phone)) {
                  $this->response_data["statusCode"] = 2;
                  return $this->response($this->response_data, 'json');
        }
         $this->response_data["statusCode"] = $statusCode?1:0;

         return $this->response($this->response_data, 'json');
    }
```
  
> #####接下来看我的访问方式

> 通过浏览器访问

+ **`http://localhost/api/android/userNameExist`**

>![error access with userNameExist](http://7xu6c5.com1.z0.glb.clouddn.com/userTelExist-error.png)

> **`http://localhost/api/android/userNameExist_get`**

>![successful access with userNameExist](http://7xu6c5.com1.z0.glb.clouddn.com/userTleExist-get-ok.png)

+ **`http://localhost/api/android/userNameExist.html`**

>![successful access with userNameExist](http://7xu6c5.com1.z0.glb.clouddn.com/userTelExist-html-ok.png)


> 然而我用API测试工具 PostMan 测试的时候是可以访问的       

对于第一种情况userNameExist不能访问,而userNameExist_get和userNameExist.html能访问,这是我的粗心
>**忽略了手册上的一句话:**

操作名_提交类型 <u>当前资源后缀和defaultType属性相同的时候</u>，例如read_post

> 而为什么测试工具能访问,而通过浏览器不能访问呢。
原因是PostMan会给http请求头上默认加上 Content-Type: text/html的头,如图
![image]()
而chrome浏览器是加的text/xml头。所以浏览器要使用.html文件后缀名,标识资源名称才能访问

总结: 这告诉我们看手册要细心,不过从中也学到了一点,也还不错。

+ 在网址后传参m会被经过路由,m参数会读取不出来
   http://localhost/api/android/user/register_by_mail/activate?m=41a20e3249ad74d401cafacef07c5c6c&k=9f4016408e8a6c1bddb95a015049a50c

 从get数组中的数据:
   array(1) {
     ["k"]=>
         string(32) "9f4016408e8a6c1bddb95a015049a50c"
    }

> 定制了路由,如果Restful匹配后不会经过路由

