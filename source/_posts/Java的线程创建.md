---
title: Java的线程创建
tags:
  - Java
  - 多线程
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-10-31 23:14:28
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Pictures/pixiv/1/68294854.jpg
---
# Java 的线程创建

## 1. 线程创建

**方法一：** 实现**Runnable**接口

```java
import com.sun.tools.javac.Main;

/**
 * @auther xianyue
 * @date 2020/10/30 - 星期五 - 23:43
 **/
public class Demo2 implements Runnable{
//    实现**Runnable**接口
    public static void main(String[] args) {

        Demo01 th1 = new Demo01();
        th1.start();

        for (int i = 0; i < 10; i++) {
            System.out.println("我在学习多线程"+i);
        }
    }

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("线程运行了"+ (i+10));
        }
    }
}
//    运行结果如下：
//    我在学习多线程0
//            我在学习多线程1
//    线程运行了10
//            我在学习多线程2
//    线程运行了11
//            线程运行了12
//    我在学习多线程3
//            线程运行了13
//    我在学习多线程4
//            线程运行了14
//    我在学习多线程5
//            线程运行了15
//    我在学习多线程6
//            线程运行了16
//    线程运行了17
//            线程运行了18
//    我在学习多线程7
//            线程运行了19
//    我在学习多线程8
//            我在学习多线程9
```

## 方法二： 继承 Thread 类

Thread类实现了Runnable接口

```java
/**
 * @auther xianyue
 * @date 2020/10/30 - 星期五 - 23:35
 **/
public class Demo01 extends Thread{
    //    继承Thread类
    @Override
    public void run() {
        super.run();
        for (int i = 0; i < 10; i++) {
            System.out.println("线程运行了"+ (i+10));
        }
    }

    public static void main(String[] args) {
        Demo01 th1 = new Demo01();
        th1.start();

        for (int i = 0; i < 10; i++) {
            System.out.println("我在学习多线程"+i);
        }
    }
}
//    运行结果如下：
//    我在学习多线程0
//            我在学习多线程1
//    线程运行了10
//            我在学习多线程2
//    线程运行了11
//            我在学习多线程3
//    线程运行了12
//            我在学习多线程4
//    线程运行了13
//            我在学习多线程5
//    线程运行了14
//            我在学习多线程6
//    线程运行了15
//            我在学习多线程7
//    线程运行了16
//            线程运行了17
//    我在学习多线程8
//            线程运行了18
//    我在学习多线程9
//            线程运行了19
//
//进程已结束，退出代码 0


```

## 方法三：实现 Callable 接口

```java
import com.sun.tools.javac.Main;

import java.util.concurrent.Callable;

/**
 * @auther xianyue
 * @date 2020/10/30 - 星期五 - 23:43
 **/
public class Demo2 implements Callable {
//    实现**Runnable**接口
    public static void main(String[] args) {

        Demo01 th1 = new Demo01();
        th1.start();

        for (int i = 0; i < 10; i++) {
            System.out.println("我在学习多线程"+i);
        }
    }

    @Override
    public Object call() throws Exception {
        return null;
    }
}
//    运行结果如下：
//    我在学习多线程0
//            线程运行了10
//    我在学习多线程1
//            线程运行了11
//    我在学习多线程2
//            线程运行了12
//    我在学习多线程3
//            线程运行了13
//    我在学习多线程4
//            线程运行了14
//    我在学习多线程5
//            线程运行了15
//    线程运行了16
//            线程运行了17
//    线程运行了18
//            线程运行了19
//    我在学习多线程6
//            我在学习多线程7
//    我在学习多线程8
//            我在学习多线程9
```

不论以什么方式实现多线程，都要重写**Run()**方法，编写线程所执行的内容。

```
*斜体文本*
_斜体文本_
**粗体文本**
__粗体文本__
***粗斜体文本***
___粗斜体文本___
```
