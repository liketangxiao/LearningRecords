# Java 基础

## 数据类型

### 八种基本数据类型

- byte/8 char/16 short/16 int/32 float/32 long/64 double/64 boolean/\~
- 基本数据类型都对应着一种包装类型, 可以完成自动装箱(valueOf)和拆箱(intValue)

### 缓存池

-    new是创建一个新的对象, 自动装箱会调用valueOf(0), 判断缓存池中有就直接返回值
-   Java8中特别的一点, Integer的缓存IntegerCache上界可以通过jvm -XX:AutoBoxCacheMax=&lt;size>指定

### String

-   final修饰不可变, 不可被继承, 同时包装类也不能被继承
    -   计算hash值不变, 避免重复计算
    -   要在String pool字符串常量池进行引用, 只能保持不可变
    -   保证传输过程中数据安全和线程中数据安全
-   java9之前使用char数组保存制服, Java9使用byte数组进行保存, 使用coder指定编码

-   String Pool创建过的String能再缓存池中找到返回引用
    
-   String.intern()可以将字符串添加到String pool保证引用相同的内存对象
    
-   String StringBuffer StringBuilder

    -   线程安全String, StringBuilder用synchronized同步

        

## 参数传递

-   本质上是值传递, 对象传递的时对象的地址

## 类型转换

-   不能隐式地向下转型, 但使用+=/++可以将隐式的进行传递

## 关键字

-   static
    -   静态变量,静态语句块,静态方法,静态内部类,静态导包

-   final
    -   修饰变量,方法,类

-   switch Java7之后支持String参数, 但不支持long

## Object方法

-   equals hashcode toString finalize
-   本地方法 clone wait notify notifyall getClass

## 继承

-   访问权限
    -   默认, private, protected, public
-   抽象类和接口
    -   抽象类不能被实例化
    -   Java8之后接口可以有默认的实现方法用default关键字,为了解决添加一个方法需要实现类都添加该方法
-   super
    -   指定调用父类的方法, 子类默认会调用父类的默认构造方法, 调用其他构造方法需指定

## 反射

-   Java.lang.reflect包下面包含了三个类Feild, Method, Constructor
-   Class对象,获取运行时类的信息,变量,方法,构造函数
-   动态代理

## 异常

-   Error
-   Exception
-   包括受检异常可以捕获或者抛出, 不受检异常此时程序运行错误
-   统一异常处理@ControlerAdvice @ExceptionHandler

## 注解

-   注解本质是一个继承了Annotation的特殊接口, 用于一些工具在编译、运行时进行解析和使用，起到说明、配置的功能。

-   其具体实现类是Java运行时生成的动态代理类


## 泛型

-   规定了类型,保证编译期的类型安全

-   限定通配符<? extends T><? super T>

-   非限定通配符<?>

