---
title: sleep 和 wait
tags:
  - Java
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-10-02 12:23:35
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/83964151_p0.jpg
---


# sleep 和 wait 的区别

**sleep()是Thread的静态本地方法**，**wait()是Object的成员方法**，二者是有本质区别。

**相同点**： 一旦执行，都可以使得**当前的线程进入等待状态**。

**不同点**：

1. 声明的位置不同，sleep()声明在Thread 类，wait()声明在Object 类；
2. sleep函数必须指定睡眠时间，wait可以指定也可以不指定；
3. sleep() 会让当前正在运行的、占用CPU时间片的线程**挂起指定时间**，休眠时间到自动苏醒进入可运行状态；wait() 方法用来**线程间通信**，如果设置了时间，就等待指定时间；如果不设置，则该对象在其它线程被调用 notify() / notifyAll() 方法后进入可运行状态，才有机会竞争获取对象锁。
4. 适用场景不同，sleep()可以在任何需要的场景下调用，wait()必须在**同步代码块**中或者**同步方法中的监视器**中。
5. 如果两方法都是使用在同步代码块或同步方法中，**sleep()不会释放锁**，wait()会释放锁，并进入线程等待池。

sleep()线程**控制自身流程**，让当前线程休眠，不涉及对象类，也不需要获取对象锁，所以是 **Thread** 的方法。wait()用来**线程间通信**，使拥有该对象锁的线程等待直到指定时间或notify()，需要获得对象锁，所以是 **Object** 的方法。


