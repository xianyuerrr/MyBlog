---
title: 对象相等的判断，== 和 equal
tags:
  - Python
  - Java
categories:
  - Code
  
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-11-20 23:25:15
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/%E5%9B%BE%E7%89%87/Game/%E6%98%8E%E6%97%A5%E6%96%B9%E8%88%9F/77875196.jpg
---

# 值相等与对象相同

## Python

在***python***中，我们使用 **==** 来进行判断两个对象的值是否相等，使用**is**来判断两个对象是否是同一个对象。is 是种很特殊的语法，在其它的语言一般不会见到这样的用法。

```python
# int型比较
a = 1
b = 1

print(a == b)
# 结果为True
print(a is b)
# 结果为True
```

```python
# str型比较
str1 = 'abc'
str2 = 'abc'

print(str1 == str2)
# 结果为True
print(str1 is str2)
# 结果为True
```

```python
# 自定类型比较
class my_obj:
	atr1 = 0
	atr2 = 1
	
obj1 = my_obj()
obj2 = my_obj()
 
print(obj1 == obj2)
# 结果为False
print(obj1 is obj2)
# 结果为False
```

## Java

在***java***中，我们使用 **==** 来判断两个对象是否是同一个对象，而使用**equals**方法来判断两个对象的值是否相等。

```java
public class Test03 {
    public static void main(String[] args) {
        int a = 1;
        int b = 1;
        System.out.println('a' + " = " + 'b' + ":" + (a == b));
        System.out.println('a' + "的地址：" + System.identityHashCode(a));
        System.out.println('b' + "的地址：" + System.identityHashCode(b));

        String str1 = "csdn";
        String str2 = "csdn";
        // str1 和 str2 在常量池中，只有一份，是同一个对象
        String str3 = new String("csdn");
        System.out.println("str1" + "和" + "str2" + "是同一个对象：" + (str1 == str2));
        System.out.println("str1" + " = " + "str2" + ':' + str1.equals(str2));
        System.out.println("str1" + "和" + "str3" + "是同一个对象：" + (str1 == str3));
        System.out.println("str1" + " = " + "str3" + ':' + str1.equals(str3));
    }
}


// 输出结果如下：
// a = b:true
// a的地址：664223387
// b的地址：664223387
// str1和str2是同一个对象：true
// str1 = str2:true
// str1和str3是同一个对象：false
// str1 = str3:true
```

