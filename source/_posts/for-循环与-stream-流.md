---
title: for 循环与 stream 流
tags:
  - 位运算
  - Java
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2022-03-16 18:14:39
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/85499466_p0.jpg
---

# 异或运算性质

1. `x ^ 0 = x`
2. `x ^ x = 0`
3. `y ^ x ^ x = y ^ (x ^ x)`

根据以上三条性质可得：`y ^ x ^ x = y ^ 0 = y`

由题可得：除了某个元素只出现一次以外，其余每个元素均出现两次。

所以对整个非空数组的元素进行异或运算，所得结果就等于要求的只出现一次的元素的值。



# 实现

## for 循环实现

```java
class Solution {
  public int singleNumber(int[] nums) {
​    int res = 0;
​    for (int num : nums) {
​      res ^= num;
​    }
​    return res;
  }
}
```

执行时间：1ms



## stream 实现

```java
class Solution {
  public int singleNumber(int[] nums) {
​    // 异或运算
​    int res = Arrays.stream(nums).reduce(0, (x, y) -> x ^ y);
​    return res;
  }
}
```

执行时间：3ms



# 总结思考

可以发现：for 循环比 stream 运算要快上很多。

for 循环是比较底层的操作，优化很多。对于int[] 类型的数组中的运算受到 JIT 友好以及缓存友好这两个因素决定。

而 stream 的优势是并行处理。数据量越大，stream 的优势越明显，数据量小，还是 for 循环性能好。
