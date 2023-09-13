---
title: C++ 容器
tags:
  - C++
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-03-22 21:56:31
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/92923145_p0.jpg
---
C++容器

1、字符串

```c++
#include <string>
```

2、常用函数

1. **strlen()**：返回存储在数组中的**字符串**（不包括空字符）的长度

   ```c++
   strlen(字符数组)
   ```

   

2. **sizeof()**：返回**整个数组**的长度

3. **strcmp()**：比较两个字符串的大小

   ```c++
   strcmp(字符数组1, 字符数组2);
   ```

4. **strcpy()**：把一个字符串复制给另一个字符串

   ```c++
   strcpy(字符数组1, 字符数组2);
   ```

   这里的复制包括 ‘\0’

5. **strcat()**：字符串拼接

   ```c++
   strcat(字符数组1, 字符数组2);
   // 将 2 拼接到 1 后面
   ```

6. **sscanf()** 格式输出（左 -> 右）和 **sprintf()** 格式输出（右 -> 左）：

   ```c++
   sscanf(str, "%d", &n);
   sprintf(str, "%d", n);
   ```
