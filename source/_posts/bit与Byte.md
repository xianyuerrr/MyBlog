---
title: bit与Byte
tags:
  - bit
  - Byte
  - 计网
categories:
  - 计算机
comments: true
toc: true
date: 2020-11-03 12:35:26
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/%E5%9B%BE%E7%89%87/%E5%8A%A8%E6%BC%AB/%E7%BD%91%E6%98%93%E4%BA%9101.jpg
---

# 计算机网络—bit与Byte

## bit

&emsp;&emsp;**速率**是衡量计算机网络性能的一个重要指标。速率指的是数据的传送速率，也称为**数据率**或**比特率**。

速率的单位是**bit/s**(比特每秒)(或者b/s，有时也写为bps，即bit per second)。当数据率较高时，常常在bit/s前面加上一个字母。比如 :

* $k(kilo) = 10^{3} = 千$
* $M(Mega) = 10^{6} = 兆$

* $G(Giga) = 10^{9} = 吉$ (我宿舍光猫上就是吉比特光猫)
* $T(Tera) = 10^{12} = 太$
* $P(Peta) = 10^{15} = 拍$
* $E(Exa) = 10^{18} = 艾$
* $Z(Zetta) = 10^{21} = 泽$
* $Y(Yotta) = 10^{24} = 尧$

现在人们谈到网络速率时，经常省略了速率单位中的**bit/s**，直接叫**100M**之类的，这就容易与字节**Byte**产生混淆。

## Byte

**字节**(Byte)，通常用作[计算机](https://zh.wikipedia.org/wiki/计算机)信息计量单位，是通信和数据存储的概念。

<center>1 byte  =  8 bit</center>

字节(Byte)可缩写成B，例如MB表示[Megabyte](https://zh.wikipedia.org/wiki/百万字节)；[比特](https://zh.wikipedia.org/wiki/位元)（Bit）可缩写成b，例如Mb表示[Megabit](https://zh.wikipedia.org/w/index.php?title=Megabit&action=edit&redlink=1)。

* $1MB = 2^{20}Byte = 8,388,608bit$
* $1Mb = 10^{6}bit$

在日常生活中，安装100M的宽带，100M指的是100Mbit/s，而我们手机上通常最高只能达到约 11.9MByte/s​ 的下载速度，四舍五入也就是12MByte/s。我们手机上显示的下载速度也是使用**MB**作为单位的。所以，不是运营商虚假描述，限制了带宽。是人们容易把这两个单位弄混。

