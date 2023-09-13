---
title: Python 字符串常用函数
tags:
  - Python
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-30 21:10:35
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/动漫/2d1118d9d54a486a.png
---

# Python字符操作

## ASCII

```python
ord('a') # 97
ord('z') # 122
ord('A') # 65
ord('Z') # 90
```

## 判断字符串

```javascript
s.isalnum() #所有字符都是数字或者字母
s.isalpha() #所有字符都是字母
s.isdigit() #所有字符都是数字
s.islower() #所有字符都是小写
s.isupper() #所有字符都是大写
s.istitle() #所有单词都是首字母大写，像标题
s.isspace() #所有字符都是空白字符、\t、\n
```

## 大小写转换

```javascript
s.upper() #把所有字符中的小写字母转换成大写字母
s.lower() #把所有字符中的大写字母转换成小写字母
s.capitalize() #把第一个字母转化为大写字母，其余小写
s.title() #把每个单词的第一个字母转化为大写，其余小写
```

 

