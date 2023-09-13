---
title: 找回.py文件右键的Edit with IDLE选项
tags:
  - Python
categories:
  - Code
comments: true
toc: true
date: 2020-03-26 16:58:07
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/Pictures/pixiv/3/73286489.jpg
---



# 找回.py文件右键的Edit with IDLE选项

&emsp;&emsp;通常我们安装Python之后会在**.py**文件的右键菜单中找到**Edit with IDLE**这个选项。今天突然发现右键的**Edit with IDLE**先是点击之后不能打开**.py**文件了，后来干脆就直接没了。虽然平时用的比较少，但是这个IDLE还是很方便的，必须给弄回来。

&emsp;&emsp;在一通搜索和尝试之后，只发现了修改注册表的方法有用，但是显得有些麻烦，后来发现可以编写一个**.reg**文件来完成这件事情。

&emsp;&emsp;将下面内容保存到一个**.reg**文件中，注意修改最后一行中Python的安装路径。（注意：注册表中的路径用的是\\\\来表示\\，别写错了）

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py]

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell]

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle]
"MUIVerb"="&Edit with IDLE"
"Subcommands"=""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell]

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell\edit37]
"MUIVerb"="Edit with IDLE 3.7"

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell\edit37\command]
@="\"D:\\python\\pythonw.exe\" -m idlelib \"%L\" %*"
```

&emsp;&emsp;注释版：

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py]
# 在“HKEY_CLASSES_ROOT\SystemFileAssociations”项下创建了一个名为“.py”的项

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell]
# 在“.py”项下创建了一个名为“shell”的项

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle]
"MUIVerb"="&Edit with IDLE"
"Subcommands"=""
# 在“shell”项下创建了一个名为“editwithidle”的项。
# 在“editwithidle”项中创建了：一个名为"MUIVerb"的字符串值，值为"&Edit with IDLE"；一个名为"Subcommands"的空字符串值

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell]
# 在“editwithidle”项中创建了一个名为“shell”的项

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell\edit37]
"MUIVerb"="Edit with IDLE 3.7"
# 在“shell”项下创建一个名为“edit37”的项
# 在“edit37”项下创建一个名为"MUIVerb"，值为"Edit with IDLE 3.7" 的字符串值

[HKEY_CLASSES_ROOT\SystemFileAssociations\.py\shell\editwithidle\shell\edit37\command]
@="\"D:\\python\\pythonw.exe\" -m idlelib \"%L\" %*"
# 在“edit37”项创建一个名为“command”的项
# 将“command”项中的默认值修改为“python安装路径\pythonw.exe\" -m idlelib \"%L\" %*"
```

其中**MUIVerb**的值是用来控制显示内容的，可以按照自己的想法去改。
