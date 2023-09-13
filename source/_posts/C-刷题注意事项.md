---
title: C++ 刷题注意事项
tags:
  - C++
  - 刷题
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-04-02 21:59:06
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/75273474_p0.jpg
---
1. 大数组定义位置

   ![image-20210321201227726](https://raw.githubusercontent.com/xianyuerrr/PicGo/main/img/20210321201227.png)

2. 以数组作为参数时，数组的第一维不需要填写长度。如果是二维，**第二维需要填写长度**

3. 函数

   1. memset

      对数组中的每一个函数赋相同值

      ```c++
      #include <cstring> or #include <string.h>
      memset(数组名, 值, sizeof(数组名));
      // 只建议赋值为 0, 1（因为 memset 是按字节赋值）
      // 如果要赋其他值，使用 fill（速度略慢）
      ```

   2. 

4. 在**定义指针变量**时，应该赋初值进行**初始化**，防止指针地址随机到系统工作区间

5. 由于浮点数在计算机中的存储并不总是精确的，所以在比较时需要引入一个极小数 **eps** 来对这种误差进行修正（通常取 $eps=10^{-8}=1e^{-8}$）

   ```c++
   #include <cmath>
   const double eps = 1e-8;
   const double Pi = acos(-1.0);
   #define Equ(a, b) ((fabs((a)-(b))) < (eps))
   #define More(a, b) (((a)-(b)) > (eps))
   #define Less(a, b) (((a)-(b)) < (eps))
   #define MoreEqu(a, b) (((a)-(b)) > (-eps))
   #define LessEqu(a, b) (((a)-(b)) < (eps))
   ```

   

6. **codeup**1000题代码格式

   1. while-EOF 型

      ```c++
      #include <cstdio>
      int main () {
          int a, b;
          while (scanf("%d%d", &a, &b) != EOF) {
              printf("%d\n", a + b);
          }
          return 0;
      }
      ```

   2. while-break型

      ```c++
      #include <cstdio>
      int main () {
          int a, b;
          // 以 a, b 都为0为例
          while (scanf("%d%d", &a, &b) != EOF) {
              if (a == 0 && b ==0) break;
              printf("%d\n", a + b);
          }
          return 0;
      }
      or
      int main () {
          int a, b;
          while (scanf("%d%d", &a, &b), a || b) {
              printf("%d\n", a + b);
          }
          return 0;
      }
      ```

   3. while(T - - )型

      ```c++
      int main () {
          int T, a, b;
          scanf("%d", &T);
          while (T--) {
              scanf("%d%d", &a, &b);
              printf("%d\n", a + b);
          }
          return 0;
      }
      ```

