###### ThinkPHP memory exhausted error

>代码 

```php
    <?php
      namespace Core\Model;

      use Think\Model;

      /**
       *  用户模型类,用来对用户的数据进行操作
       */
       class UserModel extends Model
       {

          public function add($user_data = array()){

          //提取用户基本用户数据
          $this->user_name = $user_data["user_name"];
          $this->user_pwd  = md5($user_data["user_pwd"]);
          $this->mail      = $user_data["user_mail"];
          $this->tele_num  = $user_data["tele_num"];
          $this->create();
          $res_check =  $this->add();//这行代码
   
          if (!$res_check) {
             return false;
           } else {
               $user_id = $this->field("user_id")->where("id = '".$exe_res."'")->find();
               return  $user_id;
            }

           $this->close();

          }

        }
    
```

> 这样也会造成内存耗尽以前的猜测又推翻了

```php

        $is_support = $this->table("register_type")->where("reg_type_id = '".$type_id."'")->find();

        dump("in registerTypeSupport ");
        dump($is_support);

        if ($is_support == null || $is_support == false) {
            return false;
        } else {
            return true;
        }



```

引起了ThinkPHP的内存耗尽错误,疑惑.
:(
Allowed memory size of 134217728 bytes exhausted (tried to allocate 40961 bytes)


