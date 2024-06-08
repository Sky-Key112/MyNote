# C#入门

## C#可空类型（Nullable）
C# 单问号 `?` 与 双问号 `??`
1. `?` 单问号为可空类型，代表该变量可以为`NULL`.(Nullable 类型)
2. `??`双问号为运算符，表示为空则使用后续的值（设置默认值）


``` C# 
int? i = 3;
等价于
Nullable<int> i = new Nullable<int>(3);

int i; //默认值0
int? ii; //默认值null
```


## 委托与事件

- `委托`(`Delegate`)

本质上是一个类型安全的函数指针，它允许你将方法作为参数传递，或者将方法赋值给变量。委托定义了一个方法签名，任何与这个签名匹配的方法都可以赋值给这个委托的变量。
```C#
    public delegate void MyDelegate(string message);  

    public static void DisplayMessage(string message)  
    {  
        Console.WriteLine(message);  
    } 

    MyDelegate myDel = DisplayMessage; 

    myDel("Hello from delegate!"); // 直接调用  

```
跟其他语言的函数指针很类似

- `事件` (`Event`)

事件是委托的封装，它提供了对委托调用的额外控制。事件只能被声明它的类内部触发，但可以在外部订阅（即添加方法到事件的调用列表中）

