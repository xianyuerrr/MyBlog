---
title: Array、ArrayList、LinkedList、Vector
tags:
  - Java
  - 数据结构
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-02 12:45:33
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/75866237_p0.jpg
---


## Array、ArrayList、LinkedList、Vector

### Array 与 ArrayList

1. Array 可以存储基本数据类型和对象，ArrayList 只能存储对象
2. Array 是固定大小的，而 ArrayList 大小是自动扩展的
3. ArrayList 内置方法多，比如 addAll、removeAll、iteration 等方法只有 ArrayList 有

### Arraylist 与 LinkedList

1. 都不是线程安全的
2. ArrayList 为**动态数组**，而 LinkedList 为**双向链表**
3. ArrayList 会存在一定的空间浪费，因为每次扩容都是之前的 1.5 倍；LinkedList 中的每个元素都要存放 前驱、后继、数据 三部分，所以每个元素的存储都比 ArrayList 花费更多的空间
4. ArrayList 比 LinkedList 在**随机访问**的时候效率要高
5. 增加和删除操作，LinkedList 要比 ArrayList 效率要高
6. ArrayList 适合多读少增删的场景；LinkedList 适合多增删少读写的场景

### ArrayList 与 Vector

1. Vector 使用 Synchronized 来实现线程同步，**线程安全**；但正因此，ArrayList 在**性能**方面要优于 Vector
2. 都需要动态的调整容量，Vector 扩容每次会增加 1 倍，而 ArrayList 只会增加 50%。

