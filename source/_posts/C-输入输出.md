---
title: C++ 输入输出
tags:
  - C++
  - 输入输出
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-06 23:33:51
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Pictures/pixiv/1/61351818.jpg
---

# C++输入输出

```c++
#include <cstdio>
// 或者是
#include <stdio.h>
```



## scanf

```c++
scanf("格式控制", 变量地址);
```

![image-20210321182129026](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/20210321182136.png)

![image-20210321182359421](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/20210321182359.png)

## printf

```c++
printf("格式控制", 变量名称);
```

![image-20210321182608018](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/20210321182608.png)

![image-20210321182624557](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/20210321182624.png)

1. **%md**

   可以使不足 **m** 位的 **int** 型变量以 **m** 位进行右对齐输出，高位用空格不起补齐。长度超过 **m** 位则不起作用

2. **%0md**

   与 **%md** 类似，只不过补空格变成了补 **0**

3. %.mf

   让浮点数保留 **m** 位小数输出（使用四舍五入成双规则） 



## getchar

输入单个字符

## putchar

输出单个字符

## gets

输入一行字符串（识别 ‘\n’作为输入结束）

**注意**：scanf 完一个整数后，如果要使用 gets，需要先用 **getchar** 接收换行符



## puts

输出一行字符串，并紧跟一个换行

## cin

```c++
#include <iostream>
using spacename std;
int a;
char b[10];
cin >> a;
cin.getline(b, 10);
```

## cout

```c++
#include <iostream>
using spacename std;
int a;
cout << a << '\n';
cout << a << endl;
```
