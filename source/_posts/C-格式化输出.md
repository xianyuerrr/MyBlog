---
title: C++ 格式化输出
tags:
  - C++
  - 输入输出
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-30 21:31:43
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/申鹤.jpg
---
# c++格式化输出

http://c.biancheng.net/view/275.html

1、在头文件 **iomanip** 中定义

保留**ans**位小数

```c++
#include <iomanip>
cout << setiosflags(ios::fixed) << setprecision(2) << ans << endl;
```

| 流操纵算子          | 作  用                                                       |        |
| ------------------- | ------------------------------------------------------------ | ------ |
| *dec                | 以十进制形式输出整数                                         | 常用   |
| hex                 | 以十六进制形式输出整数                                       |        |
| oct                 | 以八进制形式输出整数                                         |        |
| fixed               | 以普通小数形式输出浮点数                                     |        |
| scientific          | 以科学计数法形式输出浮点数                                   |        |
| left                | 左对齐，即在宽度不足时将填充字符添加到右边                   |        |
| *right              | 右对齐，即在宽度不足时将填充字符添加到左边                   |        |
| setbase(b)          | 设置输出整数时的进制，b=8、10 或 16                          |        |
| setw(w)             | 指定输出宽度为 w 个字符，或输人字符串时读入 w 个字符         |        |
| setfill(c)          | 在指定输出宽度的情况下，输出的宽度不足时用字符 c 填充（默认情况是用空格填充） |        |
| setprecision(n)     | 设置输出浮点数的精度为 n。  在使用非 fixed 且非 scientific 方式输出的情况下，n 即为有效数字最多的位数，如果有效数字位数超过 n，则小数部分四舍五人，或自动变为科学计 数法输出并保留一共 n 位有效数字。  在使用 fixed 方式和 scientific 方式输出的情况下，n 是小数点后面应保留的位数。 |        |
| setiosflags(flag)   | 将某个输出格式标志置为 1                                     |        |
| resetiosflags(flag) | 将某个输出格式标志置为 0                                     |        |
| boolapha            | 把 true 和 false 输出为字符串                                | 不常用 |
| *noboolalpha        | 把 true 和 false 输出为 0、1                                 |        |
| showbase            | 输出表示数值的进制的前缀                                     |        |
| *noshowbase         | 不输出表示数值的进制.的前缀                                  |        |
| showpoint           | 总是输出小数点                                               |        |
| *noshowpoint        | 只有当小数部分存在时才显示小数点                             |        |
| showpos             | 在非负数值中显示 +                                           |        |
| *noshowpos          | 在非负数值中不显示 +                                         |        |
| *skipws             | 输入时跳过空白字符                                           |        |
| noskipws            | 输入时不跳过空白字符                                         |        |
| uppercase           | 十六进制数中使用 A~E。若输出前缀，则前缀输出 0X，科学计数法中输出 E |        |
| *nouppercase        | 十六进制数中使用 a~e。若输出前缀，则前缀输出 0x，科学计数法中输出 e。 |        |
| internal            | 数值的符号（正负号）在指定宽度内左对齐，数值右对 齐，中间由填充字符填充。 |        |
