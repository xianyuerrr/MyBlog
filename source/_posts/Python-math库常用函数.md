---
title: Python math库常用函数
tags:
  - Python
  - math
categories:
  - Code
comments: true
toc: true
date: 2020-4-06 16:48:08
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/图片/Game/明日方舟/81050878.jpg
---

# Python-math库 常用函数

```python
from math import *
```

## 常量

1. `e`：数学常数 *e* = 2.718281...，精确到可用精度
2. `pi`：数学常数 *π* = 3.141592...，精确到可用精度
3. `inf`：浮点正无穷大，相当于 `float('inf')` 
4. `nan`：浮点“非数字”（NaN）值，相当于 `float('nan')`
5. `tau`：数学常数 *τ*，等于 2*π*

## 数论与表示函数

1. `ceil(x)`：上取整
2. `floor(x)`：下取整
3. `factorial(x)`：阶乘
4. `comb(n, k)` ：$C_{n}^{k}$
5. `perm(n, k=None)`：$A_{n}^{k}$
6. `gcd(a, b)`：最大公约数
7. `fsum(iterable)`：精确浮点值，比 **sum** 更精确
8. `fabs(x)`：绝对值
9. `prod(iterable, *, start=1)`：计算输入的 *iterable* 中所有元素的积。 积的默认 *start* 值为 `1`。
10. `fmod(x, y)`：取余。 [`fmod()`](https://docs.python.org/zh-cn/3.8/library/math.html#math.fmod) 在使用浮点数时是首选， `x % y` 在使用整数时是首选。
11. `copysign(x, y)`：基于 ***x* 的绝对值**和 ***y* 的符号**的浮点数
12. `frexp(x)`：以 `(m, e)` 对的形式返回 *x* 的尾数和指数。 *m* 是一个浮点数， *e* 是一个整数。正好是 `x == m * 2**e` 
13. `isclose(a, b, *, rel_tol=le-09, abs_tol=0.0)`：a, b是否接近。

## 幂函数与对数函数

1. `exp(x)`：$e^{x}$
2. `log(x, y=e)`：以 $y$ 为底 $x$ 的对数
3. `log1p(x)`： $x+1$ 的自然对数（$e$ 为底）
4. `log2(x)` ：以 $2$ 为底 $x$ 的对数，通常比 `log(x, 2)` 更准确
5. `log10(x)` ：以 $10$ 为底 $x$ 的对数，通常比 `log(x, 10)` 更准确
6. `pow(x, y)`：$x^{y}$ ，与内置的 `**` 运算符不同， [`math.pow()`](https://docs.python.org/zh-cn/3/library/math.html#math.pow) 将其参数转换为 [`float`](https://docs.python.org/zh-cn/3/library/functions.html#float) 类型。使用 `**` 或内置的 [`pow()`](https://docs.python.org/zh-cn/3/library/functions.html#pow) 函数来计算精确的整数幂。
7. `sqrt(x)`：$\sqrt{x}$

## 三角函数

1. `acos(x)`：以弧度为单位返回 *x* 的反余弦值
2. `asin(x)`：以弧度为单位返回 *x* 的反正弦值
3. `atan(x)`：以弧度为单位返回 *x* 的反正切值
4. `atan2(y, x)`：以弧度为单位返回 `atan(y / x)` 
5. `sin(x)`：返回 *x* 弧度的正弦值
6. `cos(x)`：返回 *x* 弧度的余弦值
7. `tan(x)`：返回 *x* 弧度的正切值
8. `dist(p, q)`：返回 *p* 与 *q* 两点之间的欧几里得距离。`sqrt(sum((px - qx) ** 2.0 for px, qx in zip(p, q)))`
9. `hypot(*coordinates)`：欧几里得范数。`sqrt(sum(x**2 for x in coordinates))`

## 角度转换

1. `degrees(x)`：将角度 *x* 从弧度转换为度数
2. `radians(x)`：将角度 *x* 从度数转换为弧度