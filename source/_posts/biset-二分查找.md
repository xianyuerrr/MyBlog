---
title: biset 二分查找
tags:
  - Python
  - 二分
  - 数据结构
categories:
  - Code
comments: true
toc: true
date: 2020-04-10 16:54:22
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Pictures/pixiv/1/69082679.jpg
---

# Python： [`bisect`](https://docs.python.org/zh-cn/3.7/library/bisect.html#module-bisect) --- 数组二分查找算法

## 查找

`bisect_left`(*a*, *x*, *lo=0*, *hi=len(a)*)

从idx开始都是 大于等于 target 的（左侧都小于）

数组名，值，区间 [lo, hi)

在 *a* 中找到 *x* 合适的插入点以维持有序。参数 *lo* 和 *hi* 可以被用于确定需要考虑的子集；默认情况下整个列表都会被使用。如果 *x* 已经在 *a* 里存在，那么插入点会在已存在元素之前（也就是左边）。如果 *a* 是列表（list）的话，返回值是可以被放在 `list.insert()` 的第一个参数的。

返回的插入点 *i* 可以将数组 *a* 分成两部分。左侧是 `all(val < x for val in a[lo:i])` ，右侧是 `all(val >= x for val in a[i:hi])` 。



`bisect_right`(*a*, *x*, *lo=0*, *hi=len(a)*)

从idx开始往右都是 大于 target 的（左侧都小于等于）

`bisect`(*a*, *x*, *lo=0*, *hi=len(a)*)

类似于 [`bisect_left()`](https://docs.python.org/zh-cn/3.7/library/bisect.html#bisect.bisect_left)，但是返回的插入点是 *a* 中已存在元素 *x* 的右侧。

返回的插入点 *i* 可以将数组 *a* 分成两部分。左侧是 `all(val <= x for val in a[lo:i])`，右侧是 `all(val > x for val in a[i:hi])` for the right side。

## 插入

`insort_left`(*a*, *x*, *lo=0*, *hi=len(a)*)

将 *x* 插入到一个有序序列 *a* 里，并维持其有序。如果 *a* 有序的话，这相当于 `a.insert(bisect.bisect_left(a, x, lo, hi), x)`。要注意搜索是 O(log n) 的，插入却是 O(n) 的。

`insort_right`(*a*, *x*, *lo=0*, *hi=len(a)*)

`insort`(*a*, *x*, *lo=0*, *hi=len(a)*)

类似于 [`insort_left()`](https://docs.python.org/zh-cn/3.7/library/bisect.html#bisect.insort_left)，但是把 *x* 插入到 *a* 中已存在元素 *x* 的右侧。