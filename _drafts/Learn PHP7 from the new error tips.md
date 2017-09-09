####  <center><font color="blue" >Learn PHP7 from the new error tips</font></center>

**在做项目的时候遇到以前从未遇到的错误**

> Code PHP:

    protected static $REG_FAILED = -1;
    protected static $REG_SUCCESS = 1;
    protected static $REG_ERROR_INSERT = 2;

    protected $UserCate = array("user" ,"student" ,"school","company");


   
    protected $registStatusTips = array(
        "$REG_FAILED"       => "register failed, Perhaps you have some infomation incorrected.",
        "$REG_SUCCESS"      => "reigster success, you can login now.",
        "$REG_ERROR_INSERT" => "register failed, sorry some error occurs internally!"
    );
    
> Simplist PHP Code:
 
    <?php
      class Test{

			protected  $REG_FAILED       = -1;
			protected  $REG_SUCCESS      = 0;
			protected  $REG_ERROR_INSERT = 1;
			
			protected $register = array(
			$REG_FAILED => "sorry 1",
			$REG_SUCCESS => "sorry 2",
			$REG_ERROR_INSERT =>" sorry 3",
			);
			
			public function _construct(){
			
			var_dump($regist);
			}
		}

      $test = new Test();


    ?>
   
__注意: 同样的代码在PHP5和PHP7下报错是不同的.__
> PHP7 报错如下:
    Fatal error: Constant expression contains invalid operations in C:\Users\Adminis
    trator\test.php on line 12

> PHP5 报错如下:
    Parse error: syntax error, unexpected T_VARIABLE, expecting ')' in C:\Users\Admi
    nistrator\test.php on line 10   

__如果代码是这样的话__

> Code PHP:

    <?php

        $status1 =  -1;
        $status2 = 0;
        $status3 = 1;
        $res = array( $status1 => "sorry 1",
                      $status2 => "sorry 2",
                      $status3 => "sorry 3");
        var_dump($res);

---

> *PHP手册中关于数组的定义是这样写的:*
> key 可以是 integer  或者 string 。value 可以是任意类型。 
> >**<font color="yellow"> 很明显PHP手册中写的十分清楚,但是为甚么会出现这种情况呢?于是,开始了探究。。。。。</font>**



