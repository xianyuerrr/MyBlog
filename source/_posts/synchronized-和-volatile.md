---
title: synchronized 和 volatile
tags:
  - Java
  - 多线程
  - 面试
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-08-22 12:19:11
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/72361485_p0.jpg
---
# synchronized 和 volatile

关键字 synchronized 和 volatile 是多线程中经常用到的两个关键字。

## 关键字 synchronized

关键字 synchronized 解决的是多个线程之间访问资源的同步性，该关键字可以保证被它修饰的方法或者代码块在任意时刻只能有一个线程执行。

关键字 synchronized 最主要的三种使用方式是：修饰实例方法、修饰静态方法、修饰代码块。

修饰实例方法：给当前对象实例加锁，进入同步代码之前需要获得当前对象实例的锁。

修饰静态方法：给当前类加锁，进入同步代码之前需要获得当前类的锁。

修饰代码块：指定加锁对象，给指定对象加锁，进入同步代码块之前需要获得指定对象的锁。

## 关键字 volatile

关键字 volatile 解决的是变量在多个线程之间的可见性，该关键字修饰的变量会直接在主内存中进行读写操作，保证了变量的可见性。

除了保证变量的可见性以外，关键字 volatile 还有一个作用是确保代码的执行顺序不变。为了提高执行程序时的性能，编译器和处理器会对指令进行重排序优化，因此代码的执行顺序和编写代码的顺序可能不一致。添加关键字 volatile 可以禁止指令进行重排序优化。

只有当一个变量满足以下两个条件时，才能使用关键字 volatile。

对变量的写入操作不依赖变量的当前值，或者能确保只有单个线程更新变量的值。

该变量没有包含在具有其他变量的不变式中。

## 关键字 synchronized 和 volatile 的区别

1. 关键字 volatile 是线程同步的轻量级实现，不需要加锁，因此性能优于关键字 synchronized。
2. 关键字 synchronized 可以修饰方法和代码块，关键字 volatile 只能修饰变量。

3. 关键字 synchronized 可能发生阻塞，关键字 volatile 不会发生阻塞。

4. 关键字 synchronized 可以保证数据的可见性和原子性，关键字 volatile 只能保证数据的可见性，不能保证数据的原子性。

5. 关键字 synchronized 解决的是多个线程之间访问资源的同步性，关键字 volatile 解决的是变量在多个线程之间的可见性。
