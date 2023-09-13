---
title: C++ Primer Plus(第六版)笔记
tags:
  - C++
  - 技术书籍阅读
categories:
  - 阅读
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-30 21:28:02
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/动漫/IMG_20201114_162223_264.jpg
---

# C++ primer Plus 第六版

## 3 处理数据

### 3.3 浮点数



#### float

1、c++的**float**：

- 可以表示整数之间的值
- 有缩放因子，表示的范围大
- 运算慢、精度降低
- 只保证6位有效位

### 3.4 运算符

#### 类型转换

1、c++**类型转换**：

- 赋值给另一种类型的变量时
- 表达式包含不同类型时
- 传参给函数时

2、数值转换**潜在的问题**：高精度类型转低精度类型可能会损失**精度**

3、列表初始化不允许**窄缩**(narrowing)

## 4 复合类型

### 4.1 数组

**数组初始化**

1、只有在**定义数组**时可以使用初始化

2、只对数组的**部分初始化**时，其他元素将被设置位0

3、列表初始化：

- 可省略等号
- 大括号内可为空（全为0）
- 禁止缩窄转换

```c++
double earning[4] {};
long plifs[] {25, 92, 3.0};  // not allowed
```

### 4.2 字符串

**C-风格字符串**

1、以空字符（null character, 写作‘\0’, ASCLL码为0）结尾，空字符需要占一位。

```c++
char xianyue[5] = {'x', 'i', 'a', 'n', 'y', 'u', 'e', '\0'};  // a string!
char xianyue[5] = "xianyue"  // 隐式空字符
```

2、“S”不是字符常量，表示字符‘S’和‘\0’组成的字符串。实际上，“S”表示的是字符串所在的内存地址。

**字符串相关函数**

1、**strlen()**：返回存储在数组中的**字符串**（不包括空字符）的长度

2、**sizeof()**：返回**整个数组**的长度

**字符串输入**

1、**cin**使用空白（**空格**、**制表符**、**换行符**）来确定字符串的结束位置。这意味着**cin**在获取**字符数组**时只读取一个单词，剩余字符仍留在输入队列中

2、**getchar()**，从缓冲区拿取一个字符。

3、面向行的输入：

- **cin.getline(数组名, 读取字符数)**，以换行符确定结尾（不保存换行符，存储时以空字符替代换行符）
- **cin.get(数组名, 读取字符数)**，不再丢弃换行符

4、空行

### 4.3 string

string 可以自动调整长度

```c++
#include <string>
std::string str;
```

不能将一个数组赋值给另一个数组，但是可以将一个**string**对象赋值给另一个**string**对象

6、原始字符串：字符表示的就是自己，用“(  )”来定界，“ 和 ( 间可以添加其他字符，作为强定界符

```c++
R"("str"\n)"
```

### 4.4 结构体

```c++
// 定义
struct inflatable{
    char name[20];
    float volume;
    double price;
}

// 声明,可以省略 struct
inflatable hat;
struct inflatable hat;

// 初始化，用逗号分隔值列表
inflatable a = {"xianyue", 1.88, 29.99};
// C++11
inflatable a {"xianyue", 1.88, 29.99};
// {}为空将导致每个字节都被设为0
inflatable a = {};
```

不允许**缩窄**转换。
