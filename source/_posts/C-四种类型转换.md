---
title: C++ 四种类型转换
tags:
  - C++
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-04-09 23:31:15
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/壁纸/431960_screenshots_20200318202345_1.jpg
---
# C++四种类型转换

## static_cast

是“静态转换”的意思，也就是在**编译期间**转换，转换失败的话会抛出一个编译错误。



 用于良性转换，一般不会导致意外发生，风险很低。

需要注意的是，static_cast **不能用于无关类型之间的转换**，因为这些转换都是有风险的，例如：

- 两个具体类型指针之间的转换，例如`int *`转`double *`、`Student *`转`int *`等。不同类型的数据存储格式不一样，长度也不一样，用 A 类型的指针指向 B 类型的数据后，会按照 A 类型的方式来处理数据：如果是读取操作，可能会得到一堆没有意义的值；如果是写入操作，可能会使 B 类型的数据遭到破坏，当再次以 B 类型的方式读取数据时会得到一堆没有意义的值。
- int 和指针之间的转换。将一个具体的地址赋值给指针变量是非常危险的，因为该地址上的内存可能没有分配，也可能没有读写权限，恰好是可用内存反而是小概率事件。



 也不能用来去掉表达式的 const 修饰和 volatile 修饰

## const_cast

用于 const 与非 const、volatile 与非 volatile 之间的转换。换句话说，const_cast 就是用来将 const/volatile 类型转换为非 const/volatile 类型。

使用 const_cast 进行强制类型转换可以**突破 C/C++ 的常数限制**，修改常数的值，因此有一定的危险性；但是程序员如果这样做的话，基本上会意识到这个问题，因此也还有一定的安全性。



## reinterpret_cast

高度危险的转换，这种转换仅仅是对二进制位的重新解释，不会借助已有的转换规则对数据进行调整，但是可以实现最灵活的 C++ 类型转换。

reinterpret 是“重新解释”的意思，顾名思义，reinterpret_cast 这种转换**仅仅是对二进制位的重新解释**，不会借助已有的转换规则对数据进行调整，非常简单粗暴，所以风险很高。

reinterpret_cast 可以认为是 **static_cast 的一种补充**，一些 static_cast 不能完成的转换，就可以用 reinterpret_cast 来完成

## dynamic_cast

dynamic_cast 与 static_cast 是相对的，dynamic_cast 是“动态转换”的意思，static_cast 是“静态转换”的意思。dynamic_cast 会在程序运行期间借助 RTTI 进行类型转换，这就要求基类必须包含虚函数；static_cast 在编译期间完成类型转换，能够更加及时地发现错误。

dynamic_cast 用于在类的**继承层次**之间进行类型转换，它既允许向上转型（Upcasting），也允许向下转型（Downcasting）。向上转型是无条件的，不会进行任何检测，所以都能成功；向下转型的前提必须是安全的，要借助 RTTI 进行检测，所有只有一部分能成功。



```c++
// C++风格调用
xxx_cast<new_type>(data);

// 老式的C风格
(new_type)data;
```
