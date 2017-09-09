###### The Comparasion between php5.3 and php7

* 类变量赋值

```php
    

class test2
{

    private $variable = 24 * 60;


    public function test2()
    {

            echo $this->variable;
    }
}

   
   $test = new test2();
   $test->test2();
```

```shell
    PHP 5.3.29 (cli) (built: Aug 15 2014 19:03:18)
    Copyright (c) 1997-2014 The PHP Group
    Zend Engine v2.3.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend Guard Loader v3.3, Copyright (c) 1998-2010, by Zend Technologies
```

>>运行结果

```sh
D:\WorkPlace\Follow-me\application\Core\Test>php test2.php
PHP Parse error: 
 syntax error, unexpected '*', expecting ',' or ';' in D:\WorkPlace\Follow-me\application\Core\Test\test2.php on line 6

Parse error: syntax error, unexpected '*', expecting ',' or ';' in D:\WorkPlace\ Follow-me\application\Core\Test\test2.php on line 6


```


```shell
D:\WorkPlace\Follow-me\application\Core\Test>php -version
PHP 7.0.1 (cli) (built: Dec 16 2015 13:36:28) ( NTS )
Copyright (c) 1997-2015 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2015 Zend Technologies
```

>>运行结果

```sh
D:\WorkPlace\Follow-me\application\Core\Test>php test2.php
PHP Deprecated:  Methods with the same name as their class will not be constructors in a future version of PHP; test2 has a deprecated constructor in D:\WorkPlace\Follow-me\application\Core\Test\test2.php on line 3

Deprecated: Methods with the same name as their class will not be constructors in a future version of PHP; test2 has a deprecated constructor in D:\WorkPlace\Follow-me\application\Core\Test\test2.php on line 3
14401440
```

