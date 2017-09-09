###### Initialing model class by using D() function in ThinkPHP

> 今天用ThinkPHP中的D()方法实例化Core模块下的UserModel类,出现了一个Bug

>php代码:
```php
    public function aliasExists($alias)
    {
        $user =  D("User");
        $check_res = $user->userNameRegistered($alias);
        return $check_res;
    }
```php

```shell
    :(
Think\Model:userNameRegistered方法不存在！
错误位置
FILE: D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\Model.class.php 　LINE: 241
TRACE
#0 D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\Model.class.php(241): E('Think\Model:use...')
#1 D:\WorkPlace\Follow-me\application\Core\Controller\UserController.class.php(628): Think\Model->__call('userNameRegiste...', Array)
#2 D:\WorkPlace\Follow-me\application\Core\Controller\UserController.class.php(628): Think\Model->userNameRegistered('duanduanwer23')
#3 D:\WorkPlace\Follow-me\application\Api\Controller\AndroidController.class.php(89): Core\Controller\UserController->aliasExists('duanduanwer23')
#4 D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\Controller\RestController.class.php(79): Api\Controller\AndroidController->userNameExist_get()
#5 [internal function]: Think\Controller\RestController->__call('userNameExist', '')
#6 D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\App.class.php(180): ReflectionMethod->invokeArgs(Object(Api\Controller\AndroidController), Array)
#7 D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\App.class.php(202): Think\App::exec()
#8 D:\WorkPlace\Follow-me\ThinkPHP\Library\Think\Think.class.php(120): Think\App::run()
#9 D:\WorkPlace\Follow-me\ThinkPHP\ThinkPHP.php(97): Think\Think::start()
#10 D:\WorkPlace\Follow-me\index.php(8): require('D:\WorkPlace\Fo...')
#11 {main}
ThinkPHP3.2.3 { Fast & Simple OOP PHP Framework } -- [ WE CAN DO IT JUST THINK ] 
```shell

**但是我将实例化方法改了一下指定了一下模块名称D()"Core/User",报错解决了**
>修改后的php代码代码如下

```php
    public function aliasExists($alias)
    {
        $user =  D("Core/User");
        $check_res = $user->userNameRegistered($alias);
        return $check_res;
    }
```php

> 然而在官方手册中是这样说的:
    D方法的参数就是模型的名称，并且和模型类的大小写定义是一致的，例如： 参数实例化的模型文件（假设当前模块为Home） 
User 对应的模型类文件的 \Home\Model\UserModel.class.php 
UserType 对应的模型类文件的 \Home\Model\UserTypeModel.class.php 

如果在Linux环境下面，一定要注意D方法实例化的时候的模型名称的大小写。
D方法可以自动检测模型类，如果存在自定义的模型类，则实例化自定义模型类，如果不存在，则会实例化系统的\Think\Model基类，同时对于已实例化过的模型，不会重复去实例化。

>由此看来ThinkPHP中的D()方法实例化,是不会自动识别当前模块的,需要指定模块


