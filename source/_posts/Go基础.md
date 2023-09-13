---
title: Go基础
tags:
  - Go
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-11-05 16:28:58
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/91601935_p0.jpg
---
# Go

## 基础

### 特征

```
- 自带 gc
- 思想简单，没有继承、多态、类等
- 语法层支持并发
```

### 规范

**命名**

Go的函数、变量、常量、自定义类型、包`(package)`的命名方式遵循以下规则：

    1）首字符可以是任意的Unicode字符或者下划线
    2）剩余字符可以是Unicode字符、下划线、数字
    3）字符长度不限

以大写字母开头时，对象就可以被外部包的代码所使用；否则，对外部的包是不可见的。

**25个关键字**

    break、default、func、interface、select、case、defer、go、map 、struct、chan、else、goto、package、switch、const、fallthrough、if、range、type、continue、for、import、return、var

**37个保留字**

    Constants:    true  false  iota  nil
    
    Types:    int  int8  int16  int32  int64  
             uint  uint8  uint16  uint32  uint64  uintptr
             float32  float64  complex128  complex64
             bool  byte  rune  string  error
    
    Functions:   make  len  cap  new  append  copy  close  delete
                 complex  real  imag
                 panic  recover

**权限**

    1）声明在函数内部，是函数的本地值，类似private
    2）声明在函数外部，是对当前包可见(包内所有.go文件都可见)的全局值，类似protect
    3）声明在函数外部且首字母大写是所有包可见的全局值,类似public

### 类型

**值类型**

    bool
    int(32 or 64), int8, int16, int32(rune), int64
    uint(32 or 64), uint8(byte), uint16, uint32, uint64
    float32, float64
    string
    complex64, complex128
    array    -- 固定长度的数组
    
    默认值：
    数值类型为 0，
    布尔类型为 false，
    字符串为 ""（空字符串）。

**引用类型**

    slice   -- 序列数组(最常用)
    map     -- 映射
    chan    -- 管道

**内置函数**

    append          -- 用来追加元素到数组、slice中,返回修改后的数组、slice
    close           -- 主要用来关闭channel
    delete            -- 从map中删除key对应的value
    panic            -- 停止常规的goroutine  （panic和recover：用来做错误处理）
    recover         -- 允许程序定义goroutine的panic动作
    real            -- 返回complex的实部   （complex、real imag：用于创建和操作复数）
    imag            -- 返回complex的虚部
    make            -- 用来分配内存，返回Type本身(只能应用于slice, map, channel)
    new                -- 用来分配内存，主要用来分配值类型，比如int、struct。返回指向Type的指针
    cap                -- capacity是容量的意思，用于返回某个类型的最大容量（只能用于切片和 map）
    copy            -- 用于复制和连接slice，返回复制的数目
    len                -- 来求长度，比如string、array、slice、map、channel ，返回长度
    print、println     -- 底层打印函数，在部署环境中建议使用 fmt 包

**内置接口**

    type error interface { //只要实现了Error()函数，返回值为String的都实现了err接口
    
            Error()    String
    
    }

### init 和 main

`init`函数

1. init函数是用于程序执行前做包的==初始化==的函数，比如初始化包里的变量等
2. 每个包可以拥有==多个==init函数
3. 包的每个源文件也可以拥有多个init函数
4. init函数==不能被其他函数调用==，而是==在main函数执行之前==，自动被调用



执行顺序：

1. ==同一文件==的`init()`调用顺序是==从上到下==的。
2. 对==同一package==中不同文件是按文件名字符串比较“==从小到大==”顺序调用各文件中的`init()`函数。
3. 对于不同`package`，如果不相互依赖的话，按照main包中”先`import`的后调用”的顺序调用其包中的`init()`，如果`package`存在依赖，则先调用最早被依赖的`package`中的`init()`，最后调用`main`函数。、
4. 如果`init`函数中使用了`println()`或者`print()`你会发现在执行过程中这两个不会按照你想象中的顺序执行。这两个函数官方只推荐在测试环境中使用，对于正式环境不要使用。



相同点：两个函数在定义时不能有任何的参数和返回值，且是自动调用。

不同点：init可以应用于任意包中，且可以重复定义多个；main函数只能用于main包中，且只能定义一个。

### 命令

```
go env用于打印Go语言的环境信息。

go run命令可以编译并运行命令源码文件。

go get可以根据要求和实际情况从互联网上下载或更新指定的代码包及其依赖包，并对它们进行编译和安装。

go build命令用于编译我们指定的源码文件或代码包以及它们的依赖包。

go install用于编译并安装指定的代码包及它们的依赖包。

go clean命令会删除掉执行其它命令时产生的一些文件和目录。

go doc命令可以打印附于Go语言程序实体上的文档。我们可以通过把程序实体的标识符作为该命令的参数来达到查看其文档的目的。

go test命令用于对Go语言编写的程序进行测试。

go list命令的作用是列出指定的代码包的信息。

go fix会把指定代码包的所有Go语言源码文件中的旧版本代码修正为新版本的代码。

go vet是一个用于检查Go语言源码中静态错误的简单工具。

go tool pprof命令来交互式的访问概要文件的内容。
```

### package

-  文件夹名与包名没有直接关系，并非需要一致。
-  同一个文件夹下的文件只能有一个包名，否则编译报错。

当前的调试部分可以使用 **go run filename.go** 来执行。

可以生成一个 **build.sh** 脚本，用于在指定位置产生已编译好的 可执文件:

```
#!/usr/bin/env bash

CURRENT_DIR=`pwd`
OLD_GO_PATH="$GOPATH"  #例如: /usr/local/go
OLD_GO_BIN="$GOBIN"    #例如: /usr/local/go/bin

export GOPATH="$CURRENT_DIR" 
export GOBIN="$CURRENT_DIR/bin"

#指定并整理当前的源码路径
gofmt -w src

go install test_hello

export GOPATH="$OLD_GO_PATH"
export GOBIN="$OLD_GO_BIN"
```

### 变量

**方式一**，指定类型

```shell
var identifier type # 不初始化，系统赋为默认值
var identifier type = value
# 一次声明多个
var identifier1, identifier2 type
var identifier1, identifier2 type = value1, value2
# 数值型默认为 0
# bool 默认为 false
# string 默认为 ""
# 其它 默认为 nil
```

**方式二**，根据值自行判断类型

```shell
var v_name = value
```

**方式三**，`:=`，如果已经使用 var 声明过，使用此方式会产生编译错误

```shell
v_name := value
# intVal := 1
# 相当于 : 
# var intVal
# intVal = 1
```

**多变量声明**

```shell
var (
    vname1 v_type1
    vname2 v_type2
)
# 一般用于声明全局变量
```

### 常量

常量中的数据类型只可以是==布尔型==、==数字型==（整数型、浮点型和复数）和==字符串型==。

```shell
const identifier [type] = value
# 可以省略类型说明符 type

# 显式类型定义： 
const b string = "abc"
# 隐式类型定义： 
const b = "abc"

# 多个相同类型的声明
const c_name1, c_name2 = value1, value2
```

常量可以用作**枚举**：

```shell
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```

常量表达式中，函数必须是==内置函数==，否则编译不过



**iota**

iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中==每新增一行常量声明==将使 iota 计数一次(iota 可理解为 ==const 语句块中的行索引==)。

iota 可以被用作枚举值：

```shell
const (
    a = iota
    b = iota
    c = iota
)
# 可简写为：
const (
    a = iota
    b # 与上方最近的语句内容相同
    c
)
```



### 数组

```shell
var variable_name [SIZE] variable_type
var balance [10] float32

var balance = [5] float32 {1000.0, 2.0, 3.4, 7.0, 50.0}
var balance = [...] float32 {1000.0, 2.0, 3.4, 7.0, 50.0}

# 将索引为 1 和 3 的元素初始化
var balance = [5] float32 {1:2.0,3:7.0}

# 多维数组
var variable_name [SIZE1][SIZE2]...[SIZEN] variable_type
var threedim [5][10][4] int
```
