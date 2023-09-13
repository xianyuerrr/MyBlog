---
title: TopK问题
tags:
  - 面试
  - 算法
categories:
  - 算法
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-12-02 13:43:51
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/78531987_p0.png
---
# TOPK

整体排序

1、冒泡，O（N2）

2、堆排序，O（NLogN）

3、快排，O（NLogN）

4、计数排序（数据范围不能太大，空间换时间），O（N）

局部排序

1、局部冒泡（找完最大K个就停止），O（KN）

2、小根堆，依次遍历，把最大的K个数放进去，O（NLogK）

3、局部快排（可随机选取pivot）只排序包含第K大的那一侧，平均 O（N）

