- [cpp中的回调函数 （译文）](#org5b8e5df)
  - [什么是回调函数？我们为什么要使用它？](#orgc122c29)
  - [C++11中的回调是什么？](#orgf18043f)
  - [详说几种编写回调的集中重要方法](#org2297705)
    - [函数指针](#org4a12fd8)
    - [调用回调函数](#org185a965)
- [引用](#org989877f)



<a id="org5b8e5df"></a>

# cpp中的回调函数 （译文）


<a id="orgc122c29"></a>

## 什么是回调函数？我们为什么要使用它？

&ensp;&ensp;html 一个回调方法是可以被一个类或者函数可以接受并可调用的方法。它可以用来根据回调定制当前逻辑。 我们使用回调函数的其中一个原因是: 回调函数可以用来写一些独立于被调用函数的通用代码，并且可以被不同的回调方法使用。 标准 `algorithm` 库中的许多函数都使用了回调。比如， `for_each` 算法在遍历过程中就对遍历器中的每一个元素使用了一个 `unary(一元)` 回调函数。

```cpp
template<class InputIt, class UnaryFunction>
UnaryFunction for_each(InputIt first, InputIt last, UnaryFunction f) 
{
   for (; first != last; ++first) {
      f(*first);
   }
   return f;
}
```

可以用来进行第一次增加并且然后通过传递一个合适的可调用函数来输出一个 `vector` ,比如:

```cpp
std::vector<double> v{1.0,2.2,4.0,5.5,7.2};
double r = 4.0;
std::for_each(v.begin(), v.end(), [&](double &v) { v += r;});
std::for_each(v.begin(), v.end(), [](double v) { std::cout << v << " ";});
```

上面的代码会输出:

```results
5 6.2 8 9.5 11.2
```

回调函数的另一个应用是通知某些事件的调用者，这保证了一定量的静态/编译事件灵活性。 个人来说，我使用一个使用了两个不同的回调函数的本地优化库。

-   当需要一个函数值和一个基于 `vector` 类型的输入值的梯度时， 第一个回调会被调用。（回调函数中的逻辑： 函数值确定/梯度推导）

-   第二个回调函数会在算法的每一步调用一次来接收算法一定的覆盖范围的相关信息。（通知回调）

所以, 库的设计者并不决定,通过通知回调而传递给程序员的信息将会做什么，并且他不需要担心如何决定函数值，因为他们会在回调函数的逻辑中实现。 这些都是库使用者所考虑的事情，而我只需要保持库小并且更加通用。

另外，回调可以让程序动态运行。

想像一下，一些有些类型的游戏引擎类具有被出发的功能。每次，用户在他的键盘上按下一个按钮，一系列控制你游戏的功能就被触发。使用回调，你可以在运行时决定或者再次决定采用什么动作。

```cpp
void player_jump();
void player_crouch();

class game_core
{
   std::array<void(*)(), total_num_keys> actions;

   void key_pressed(unsigned key_id)
   {
      if(actions[key_id]) actions[key_id]();

   }

   //update keybind from menu
   void update_keybind(unsigned key_id, void(*new_action)())
   {
    actions[key_id] = new_action;
   }
};
```

这里的 `key_pressed` 函数使用了保存在 `actions` 数组中的的回调用来获取当按下一些特定的键所执行的行为。当玩家选择改变跳动作的按钮，引擎可以调用。

```C++
game_core_instance.update_keybind(newly_selected_key, &player_jump);
```

并且当这个按钮下次在游戏中按下的时候,调用 `key_pressed` （调用 `player_jump` ） 的行为会改变。


<a id="orgf18043f"></a>

## C++11中的回调是什么？

&ensp;&ensp; 可以到cppreference中 [C++ concepts: Callable](http://en.cppreference.com/w/cpp/concept/Callable) 查看更标准的描述。 因为，一些不同的东西都可以转换为 `callable` , 所以在 `C++(11)` 中，函数性回调可以以不同的 方式实现：

-   函数指针（包括只想成员函数的指针）
-   `std::function` 对象
-   Lambdah表达式
-   绑定表达式
-   函数对象（拥有重载方法的类调用 `operator()` ）

*Note:指向数据成员的指针也是可调用的，但是没有函数被调用*


<a id="org2297705"></a>

## 详说几种编写回调的集中重要方法

-   在这篇文章中编写一个回调函数表示声明并且定义一个回调类型的语法。
-   调用一个回调函数表示调用这些对象的语法。
-   使用一个回调函数表示给一个使用回调的函数传递参数的语法。

*Note:从 `C++17` 起， 如 `f(...)` 的调用可以写成 `std::invoke(f,...)`, 后者也可以处理指向成员方法的指针*


<a id="org4a12fd8"></a>

### 函数指针

&ensp;&ensp; 函数指针是最简单的回调实现方式（就通用性而言，就可读性而言，有些人人认为是最差的）。 让我们定义一个简单的函数 `foo` :

```cpp
int foo(int x) {return 2+x;}
```

1.  定义一个函数指针 / 类型符号

    &ensp;&ensp; 一个函数指针类型定义方式如下：
    
    ```cpp
    return_type (*)(paramter_type1, paramter_type_2, paramter_type_3)
    // i.e, a pointer to foo has the type
    int (*)(int)
    ```
    
    &ensp;&ensp; 一个有名称的函数指针的定义方式如下：
    
    ```cpp
    return_type (* name) (parramter_type_1, paramater_type_2, parameter_type_3)
    // i.e f_int_t is a type: function pointer taking one int argument, return int
    typedef int (*f_int_t)(int);
    //foo_p is a pointer to function taking int returning int
    //initialized by pointer to function foo taking int returning int
    f_init_t foo_p = &foo;
    f_int_t foo_p = &foo;
    ```
    
    &ensp;ensp; 使用 `using` 声明可以让函数指针的定义可读性更强， 因为上面的 `typedef` 定义方式也可以写为：
    
    ```cpp
    using f_int_t = int(*)(int);
    ```
    
    如此定义，使得 `f_int_t` 是一种新类型和函数指针类型更加容易辨识变得更加清楚（至少对于我来说是这样的）。 并且声明使用一个函数指针的回调的函数的方式如下：
    
    ```cpp
    //foobar having a callback argument named moo of type 
    //pointer to function reutrning int taking int as its argument
    int foobar (int x, int(*moo)(int));
    //if f_int is the function pointer typedef from above we can alsow write foolbar as
    ```


<a id="org185a965"></a>

### 调用回调函数

&ensp;&ensp; 调用回调函数的语法如下:

```cpp
int foobar (int x, int (*moo)(int))
{
   reutrn x+moo(x);
}
// analog
int foobar (int x, f_int_t moo)
{
  return x + moo(x); //function pointer moo called using argument x
}
```



<a id="org989877f"></a>

# 引用

[StackOverflow:Callback functions in c++](https://stackoverflow.com/questions/2298242/callback-functions-in-c)
