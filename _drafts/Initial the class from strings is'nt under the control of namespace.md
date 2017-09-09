###### Initial the class from strings is'nt under the control of namespace
 ---
>> 开发环境: 
         <font color="222222">php5.3
                              ThinkPHP 3.2.2
         </font>

> 今天在写项目时用字符串实例化对象出现了一个问题，感到疑惑不解



> UserController.class.php


  >  <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px"> Snippet1</button> 

        //调用代码片段
        $classname = "Core\Model\StudentUserModel";
        $user = new $classname();

  >  <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px">Result1</button> 

       :(
       Class 'StudentUserModel' not found
       错误位置
       FILE: D:\WorkPlace\Follow-me\application\Core\Controller\UserController.class.php 　LINE: 115

  >  <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px"> Snippet2</button> 

        use Core\Model\StudentModel;
        //调用代码片段
        $classname = "StudentUserModel";
        $user = new $classname();

  >  <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px">Result2</button> 

       :(
       Class 'StudentUserModel' not found
       错误位置
       FILE: D:\WorkPlace\Follow-me\application\Core\Controller\UserController.class.php 　LINE: 115

   >  <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px"> Snippet3</button>

        //调用代码片段
        $classname = "\Core\Model\StudentUserModel";
        $user = new $classname();

  >   <button style="color: #fff;background: #4E5A91;border:0;border-radius: 2px">Result3</button>
        运行正确
        

 ---
 ###### <font color="333"> 猜测是字符串实例化的时候命名空间约束失效</font>       