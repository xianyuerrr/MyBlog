---
title: Maven学习
tags:
  - Java
  - Maven
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2022-02-23 16:37:30
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/86068944_p0.jpg
---
# Maven 学习

## Maven 项目构建命令

```
#编译
mvn compile
# 清理
mvn clean
# 测试
mvn test
# 打包
mvn package
# 安装到本地仓库
mvn install
```



## 依赖传递冲突问题

路径优先：相同资源，层级越深，优先级越低

声明优先：同层依赖，前面的会覆盖后面的

特殊优先：同级配置了相同资源的不同版本时，后面的覆盖前面的

## 依赖范围

![image-20220223202114355](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Roaming/Typora/typora-user-images/image-20220223202114355.png)

## 依赖范围的传递性

![image-20220223212613952](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Roaming/Typora/typora-user-images/image-20220223212613952.png)

## 项目构建生命周期

Maven对项目构建的生命周期分为三套：

- clean，清理
- default，核心工作（编译、测试、打包、部署）
- site，产生报告，发布站点

![image-20220223215124231](C:/Users/30786/AppData/Roaming/Typora/typora-user-images/image-20220223215124231.png)

