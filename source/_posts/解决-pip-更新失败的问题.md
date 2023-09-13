---
title: 解决 pip 更新失败的问题
tags:
  - Python
  - pip
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-12-26 23:28:02
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/壁纸/UpupooResource/2000032802/preview.jpg
---
# pip更新失败找不到

## 问题描述

当我们的pip版本不够新的时候，安装完库会出现下图的情况：

![image-20201226104158100](https://img-blog.csdnimg.cn/20201226110404933.png)

我们可以执行下面的命令去更新pip：

```
pip install --upgrade pip
```

但是烦人的是，有时更新会出错，比如下图的错误：

![image-20201226104458073](https://img-blog.csdnimg.cn/2020122611042436.png)

在卸载旧版本的pip之后，出现了拒绝访问的错误，然后新版本的pip没安装成功。当我们再想使用pip的时候，就会出现下图的情况：

![image-20201226104653406](https://img-blog.csdnimg.cn/20201226110436897.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70)

显示“No module named 'pip'”，由于旧的卸载了，新的还没装上去，所以pip已经没了。

## 解决方法

```
python -m ensurepip
python -m pip install --upgrade pip
```

执行第一句之后：

![image-20201226105041459](https://img-blog.csdnimg.cn/20201226110447479.png)

执行第二句之后：

![image-20201226105110442](https://img-blog.csdnimg.cn/20201226110456416.png)

完成！
