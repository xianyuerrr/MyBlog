---
title: heapq 堆队列
tags:
  - Python
  - 堆
  - 数据结构
categories:
  - Code
comments: true
toc: true
date: 2020-04-014 16:56:01
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/图片/Game/明日方舟/EmpWsPbUYAAfFP0.jpg
---
# Python 堆队列 – heapq

## 介绍

这个模块提供了堆队列算法的实现，也称为**优先队列算法**。

附上[Python3文档](https://docs.python.org/zh-cn/3/library/heapq.html)。

**heapq**是一个二叉树，它的每个父节点的值都只会小于或等于所有孩子节点（的值）。 它使用了数组来实现：从零开始计数，对于所有的 *k* ，都有 `heap[k] <= heap[2*k+1]` 和 `heap[k] <= heap[2*k+2]`。 为了便于比较，不存在的元素被认为是无限大。 堆最有趣的特性在于最小的元素总是在根结点：`heap[0]`。

**特点**：

- 使用了**从零开始**的索引
- 堆为**最小堆**

## 常用函数

- `heappush(heap, item)`：保持堆的不变性。
- `heappop(heap)`：弹出并返回 **heap** 中最小的元素，保持堆的不变性。
- `heappushpop(heap, item)`：将 **item** 放入堆中，然后弹出并返回 **heap** 的最小元素，虽然先调用 [`heappush()`](https://docs.python.org/zh-cn/3/library/heapq.html#heapq.heappush) 再调用 [`heappop()`](https://docs.python.org/zh-cn/3/library/heapq.html#heapq.heappop) 也可以，但是这个更快。
- `heapify(x)`：将 **list** x 转换成堆，原地，线性时间
- `heapreplace(heap, item)`：弹出并返回 **heap** 中最小的一项，同时推入新的 **item**。比 [`heappop()`](https://docs.python.org/zh-cn/3/library/heapq.html#heapq.heappop) 加 [`heappush()`](https://docs.python.org/zh-cn/3/library/heapq.html#heapq.heappush) 更高效。

## 三个基于堆的通用功能函数

- `merge(*iterables, key=None, reverse=False)`：将多个已排序的输入合并为一个已排序的输出。类似于 `sorted(itertools.chain(*iterables))` 但返回一个可迭代对象，不会一次性地将数据全部放入内存，并假定每个输入流都是已排序的（从小到大）。

  具有两个可选参数，它们都必须指定为关键字参数。

  *key* 指定带有单个参数的 [key function](https://docs.python.org/zh-cn/3/glossary.html#term-key-function)，用于从每个输入元素中提取比较键。 默认值为 `None` (直接比较元素)。

  *reverse* 为一个布尔值。 如果设为 `True`，则输入元素将按比较结果逆序进行合并。

- `nlargest`(*n*, *iterable*, *key=None*)[¶](https://docs.python.org/zh-cn/3/library/heapq.html#heapq.nlargest)

  从 *iterable* 所定义的数据集中返回前 *n* 个最大元素组成的列表。 如果提供了 *key* 则其应指定一个单参数的函数，用于从 *iterable* 的每个元素中提取比较键 (例如 `key=str.lower`)。 等价于: `sorted(iterable, key=key, reverse=True)[:n]`。

- `nsmallest`(*n*, *iterable*, *key=None*)

  从 *iterable* 所定义的数据集中返回前 *n* 个最小元素组成的列表。 如果提供了 *key* 则其应指定一个单参数的函数，用于从 *iterable* 的每个元素中提取比较键 (例如 `key=str.lower`)。 等价于: `sorted(iterable, key=key)[:n]`。


