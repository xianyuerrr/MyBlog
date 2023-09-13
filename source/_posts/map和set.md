---
title: map和set
tags:
  - Java
  - 数据结构
  - 面试
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-10-02 13:11:47
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/93024214_p0.jpg
---
# 映射和集合

Map 接口定义映射，存储一组键值对的映射关系。

Set 接口定义集合，存储一组互不相同的元素，该接口继承了 Collection 接口。

## Map 接口的概念和常用方法

Map 接口存储一组键值对的映射关系，映射中的每个键对应一个值。映射中**不能有重复的键**，否则会出现一个键对应多个值的情况，这违背了映射的定义。

## Map 接口的实现类

### HashMap

HashMap 类是散列映射，通过散列函数计算键对应的存储位置，因此可以快速地完成放置键值对、删除键值对、根据键获得值的操作。

JDK 1.8 之前的 HashMap 的底层通过**数组和链表**实现，如果出现冲突则通过**拉链法**解决冲突。JDK 1.8 在解决冲突时的实现有较大变化，当链表长度大于阈值（默认为 8）时，将链表转化为**红黑树**，以减少搜索时间。

![image-20210915110838014](https://raw.githubusercontent.com/xianyuerrr/PicGo/main/img/20210915110838.png)



**默认加载因子为什么选择 0.75：**

空间利用率与查询成本的一个折中。加载因子过高，空间利用率提高，但哈希冲突的概率增加；加载因子过低，哈希冲突概率降低，但会频繁扩容，空间利用率降低。

0.75 是居于数学分析（泊松分布）和行业规定一起得到的一个结论。

**为什么链表转红黑树的阈值设为 8：**

为什么不一开始直接使用红黑树

1. 红黑树结点所占空间是普通节点的两倍，但查找复杂度低，只有当节点特别多时，红黑树的优点才能够凸显出来。
2. 阈值为 8，是数据分析统计得到的结果。链表长度到达 8 的概率是非常低的。
3. 链表转为红黑树，除了要求链表长度大于 8，还要 HashMap 的**数组长度大于 64**。当红黑树的节点小于或等于 6 个以后，又会恢复为链表形态

**扩容：**

1. 初始值 16，负载因子 0.75，阈值 = 负载因子 `*` 容量；
2. 键值对数目大于阈值 或 初始化时，调用 `resize()` 进行扩容；
3. 每次扩容都是之前的两倍；
4. 由于hash值范围太大，不能直接在内存建立这么大的数组，所以需要取余。
5. 扩容时判断 `e.hash & oldCap` 是否为 0。若为 0，则位置不变，若为 1，则位置变为 原位置 + 旧容量。因为当前位置是 hash值对 oldCap 取余得到的，而 oldCap 是 2 的幂次，`e.hash % oldCap` 相当于 `e.hash & (oldCap - 1)`，此时容量变为原来的两倍，则运算变为 `e.hash & (2*oldCap - 1)` 。其实与之前的 `&` 运算只多了一个二进制位的运算，这个多出来的位，正是 oldCap 的二进制中 1 的位置。所以只需要判断 `e.hash & oldCap` 即可得到新的位置。

**能否使用任意类作为 key**

可以，但需要注意：

1. 重写 `equals()` 方法时，也应该重写 `hashCode()` 方法
2. key 最好使用不可变类型，不会出现**放入和获取时哈希值不同**的情况。对应的哈希值可以被缓存起来，性能好

### HashTable

Hashtable 类是**散列表**，其功能和 HashMap 相似。以下是 HashMap 和 Hashtable 的部分区别。

### HashMap 与 HashTable 的区别

**HashMap 不是线程安全的**，Hashtable 的大多数方法用关键字 synchronized 修饰，因此 **Hashtable 是线程安全**的。

在不需要保证线程安全的情况下，HashMap 的效率高于 Hashtable。

**HashMap 允许键或值为 null**，只能有一个键为 null，可以有一个或多个键对应的值为 null，Hashtable 不允许键或值为 null。

从 JDK 1.8 开始，HashMap 在链表长度大于阈值（默认为 8）时，将链表转化为红黑树以减少搜索时间，Hashtable 没有这样的机制。

### ConcurrentHashMap





![image-20210915125504735](https://raw.githubusercontent.com/xianyuerrr/PicGo/main/img/20210915125504.png)



### TreeMap

TreeMap 是有序映射，键可以使用 Comparable 接口或 Comparator 接口排序。

TreeMap 的底层实现是红黑树，通过红黑树维护映射的有序性。由于要维护映射的有序性，因此 TreeMap 的各项操作的平均效率低于 HashMap，但是 TreeMap 可以按照顺序获得键值对。

Set 接口的定义和常用方法
Set 接口存储一组互不相同的元素，一个集合中不存在两个相等的元素。

Set 接口继承了 Collection 接口，没有引入新的方法或常量，只是规定其实例不能包含相等的元素。

## Set 接口的实现类

### HashSet

HashSet 类是散列集合，其**底层实现基于 HashMap**，就是 HashMap 套了个外壳，构造方法里创建的就是 HashMap 对象。

它把你要存的值当做 `HashMap`的 key，而 value 值是一个 `final`的`Object`对象，只起一个占位作用。而`HashMap`本身就不允许重复键，正好被`HashSet`拿来即用。

```java
if (p.hash == hash &&
        ((k = p.key) == key || (key != null && key.equals(k))))
```

首先通过 hash 算法算出的值必须相等，算出的结果是 int，所以可以用 == 符号判断。并且待插入的 key == 当前索引已存在的 key，或者 待插入的 key.equals(当前索引已存在的key)，注意`==` 和 equals 是**或**的关系。== 符号意味着这是同一个对象， equals 用来确定两个对象内容相同。

根据**散列约定，如果两个对象相同，它们的散列码一定相同**，因此如果在子类中重写了 **equals** 方法，必须在该子类中重写 **hashCode** 方法，以保证两个相等的对象对应的散列码是相同的。

### TreeSet

TreeSet 类是有序集合，其**底层实现基于 TreeMap**。和 TreeMap 相似，TreeSet 可以使用 Comparable 接口或 Comparator 接口对元素排序。

### LinkedHashSet

LinkedHashSet 就是套壳儿 LinkedHashMap
