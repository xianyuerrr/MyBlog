---
title: 解决 Maven 在 IDEA 总是自动使用 1.5 版本
tags:
  - Java
  - Maven
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-1-06 23:22:53
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/壁纸/UpupooResource/1800010625/preview.jpg
---
# 解决IDEA maven 老是自动使用JDK1.5的问题

<img src="https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/202110011611542.png" alt="image-20211001161153403" style="zoom:50%;" />

<img src="https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/202110011613048.png" alt="image-20211001161332973" style="zoom: 50%;" />

如上图，一使用Maven这些module就自动使用 JDK1.5，

项目结构里 Language Level 也都自动变成了 5。很烦，一运行就会出现以下 Messages：

<img src="https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/202110011615495.png" alt="image-20211001161512457" style="zoom: 67%;" />

被这个东西烦到不行，于是乎进行了各种尝试，最终解决了问题。

我们对 Maven 的配置文件进行更改就可以了。



我们找到 Maven 的用户配置文件（就是下图标出的路径下的文件）并打开。

<img src="https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/202110011617970.png" alt="image-20211001161717900" style="zoom: 50%;" />

然后在 `<settings> </settings>` 标签内添加如下内容，即可将对应版本都更改为 JDK1.8：

```xml
    <profiles>
        <profile>
            <id>jdk-1.8</id>
                <activation>
                <activeByDefault>true</activeByDefault>
                <jdk>1.8</jdk>
            </activation>
            <properties>
                <maven.compiler.source>1.8</maven.compiler.source>
                <maven.compiler.target>1.8</maven.compiler.target>
                <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
            </properties>
        </profile>
    </profiles>
```


