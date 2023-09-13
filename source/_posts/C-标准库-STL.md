---
title: C++ 标准库 STL
tags:
  - C++
  - STL
  - 数据结构
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-06-20 23:41:10
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/壁纸/431960_screenshots_20200313005358_1.jpg
---
# C++标准库STL

## 一、vector

向量，变长数组

可以以邻接表方式存储图（结点数太多的不行）

### 1、定义

```c++
#include <vector>
using namespace std;

// 定义
vector<typename> name;
vector<typename> arrayname[arraysize];
// 与vector<vector<int> >name;不同的是，这种写法的一维长度已经固定位arraysize，另一维才是变长的。

// typename可以是任何基本类型
// 也可以是STL标准容器，这种的要在定义时在 >> 符号之间加上空格（C++11之前的编译器会将其视为移位操作，导致编译错误）

// e.g.:
vector<int> name;
vector<node> name; // node为结构体
vector<vector<int>> name; // >>之间要加空格
vector<vector<int> > name;

```

### 2、访问

下标访问或通过迭代器访问

```c++
vector<int> vi;
vector<int>::iterator it = vi.begin();
for(vector<int>::iterator it=vi.begin();it!=vi.end();it++){
	printf("%d ",*it);
}
// vi[i] 和 *(vi.begin() + i) 是等价的
// 允许 i++， ++i
```

在STL容器中，只有**vector**和**string**允许使用vi.begin()+4这种**迭代器+整数**的写法。

### 3、常用函数

**1、push_back()**

`push_back(x)`就是在vector后面添加一个元素x

**2、pop_back()**

`pop_back(x)`用以删除vector的尾元素

**3、insert()**

`insert(it, x)`用来向vector的任意迭代器it处插入一个元素x

```c++
vi.insert(vi.begin()+2,-1);
```

## 二、set

### 1、定义

**内部自动有序**且**不含重复元素**的容器。

**set** 内的元素自动递增排序，且去除了重复元素

**延申**：如果需要处理**不唯一**的情况，则需要使用 **multiset**.

C++11 标准还增加了 **unordered_set**，以散列代替set内部的红黑树(Red Black Tree，一种自平衡二叉查找树)实现，用来处理**只去重但不排序**的需求，**速度**比set快很多



```c++
#include <set>
set<typename> name;
// e.g.
set<int> name;
set<node> name;
set<typename> Arrayname[arraySize];
```

### 2、访问

只能通过**迭代器(iterator)**访问

```c++
set<typename>::iterator it;
set<typename> st;
for (set<typename>::iterator it = st.begin(); it != st.end(); it++){
    printf("%d", *it)
}
// 不能使用 it < st.end() 的写法
// 除了vector 和 string 之外的STL容器都不支持 *(it+i) 的访问方式
```

### 3、常用函数

**1、insert()**

`insert(x)` 可将 x 插入 set 容器，并自动**递增排序**和**去重**，时间复杂度为 **O(logN)**

**2、find()**

`find(vlaue)` 返回 set 中对应值为 value 的迭代器，时间复杂度为 **O(logN)**

## 三、string

字符串容器，对字符串常用的功能进行了封装

```c++
#include <string.h> 与 <string>
// 是不同的
```

### 1、定义

```c++
string str;
string str = "xianyue";
```

### 2、访问

- 下标访问

  ```c++
  string str = "xianyue";
  for (int i=0; i < str.length(); i++) {
      printf("%c", str[i]);
  }
  ```

  如果要读入或者输出整个字符串，只能使用**cin**和**cout**：

  ```c++
  string str;
  cin >> str;
  cout << str;
  ```

  **printf**输出**string**

  ```c++
  string str = "xianyue";
  printf("%s\n", str.c_str());
  // 将string转成字符数组
  ```

- 迭代器访问

  ```c++
  string str = "xianyue";
  for (string::iterator it = str.begin(); it != str.end(); it++) {
      printf("%c", *t);
  }
  ```

  **string**和**vector**一样，支持直接对迭代器进行加减某个数字

### 3、常用函数

**1、operator+=**

**string**的加法，拼接字符串

```c++
string str1 = "xianyue", str2 = "rrr", str3;
str3 = str1 + str2;
cout<<str3;
```

**2、compare operator**

两个**string**可以直接使用 **==, !=, <, <=, >, >=** 比较大小，规则是字典序

**3、length() / size()**

**length()**返回string的长度，即存放的字符数，O(1)

**size()**和**length()**基本相同

**4、insert()**，O(N)

- **insert(pos, string)**，在pos位置插入字符串 string
- **insert(it, it2, it3)**，**it**为原字符串的欲插入位置，**it2**和**it3**是待插入字符串的首尾迭代器

**5、substr()**，O(len)

```c++
str.substr(pos, len);
// 返回从 pos 号位开始，长度为 len 的子串
```

**6、string::npos**，是一个**常数**，本身的值为 **-1**，由于是 **unsigned_int** 类型，所以也可以当作 **unsigned_int** 的最大值。可以作为 **find** 函数失配时的返回值。

**7、find()**，O(nm)

```c++
str.find(str2);
// 当 str2 是 str 的子串时，返回其在 str 中第一次出现的位置；
// 如果 str2 不是 str 的子串，返回 string::npos

str.find(str2, pos);
// 从 pos 号位开始匹配 str2，返回值与上相同
```

**8、replace()**，O(str.length)

```c++
str.replace(pos, len, str2);
// 把 str 从 pos 号位开始，长度为 len 的子串替换为 str2

str.replace(it1, it2, str2);
// 把 [it1, it2) 范围内的子串替换为 str2
```

## 四、map

**映射**，可以将任何基本类型映射到任何基本类型。内部是**红黑树**实现的（set也是），会以**键** **从小到大**的顺序自动排序。

如果一个键需要对应多个值，就只能用 **multimap**，C++11标准还增加了 **unordered_map**，以**散列**代替 map 内部的红黑树实现，**只映射不排序**，速度快得多

```c++
#include <map>
using namespace std;
```

### 1、定义

```c++
map<typename1, typename2> mp;

map<string, int> mp;
// 字符串到整型的映射，必须使用 string，而不能使用 char 数组

map<set<int>, string> mp;
```

### 2、访问

- 通过下标访问 `mp[key]`

- 通过迭代器访问

  ```c++
  map<typename1, typename2>::iterator it;
  it->first; // 访问 key
  it->second; // 访问 value
  ```

### 3、常用函数

**1、find()**

find(key) 返回键为 key 的映射的迭代器，O(logN)

```c++
map<typename1, typename2> mp;
map<typename1, typename2>::iterator it = mp.find(key);
```

## 五、queue

队列，**先进先出**。

**双端队列**：deque

**优先级队列**：priority_queue

### 1、定义

```c++
#include <queue>
using namespace std;

queue<typename> name;
```

### 2、访问

由于队列**先进先出**，所以只能通过 `front()` 来访问队首元素，或者是通过 `back()` 来访问队尾元素

### 3、常用函数

**1、push()**

`push(x)`，将 `x` 加入队列，O(1)

**2、front()、back()**

`front() / back()` 获取 队首 / 队尾 元素，O(1)

**3、pop()**

`pop()`，令队首元素出队，O(1)

**4、empty()**

`empty()`，检测队列是否为空，O(1)

**注意**：使用 `front() / pop()` 前， 必须使用 `empty()` 判断队列是否为空

## 六、priority_queue

优先级队列，底层是使用**堆**来进行实现的，队首元素一定是当前队列中优先级最高的

### 1、定义

```c++
#include <queue>
using namespace std;

priority_queue<typename> name;
//对于基础类型 默认是大顶堆
```

### 2、访问

优先级队列没有 `front()` 函数 和 `back()` 函数，只能通过 `top()` 函数来访问队首元素（**堆顶**）

### 3、常用函数

**1、push()**

`push(x)`，令 x 入队，O(logN)

**2、top()**

`top()`，获取队首元素，O(1)

**3、pop()**

堆顶出队

**4、empty()**

检测队列是否为空

### 4、优先级设置

**基本数据类型**

```c++
priority_queue<int> q; // 默认为大顶堆
priority_queue<int, vector<int>, less<int> > q;
//     这里一定要有空格，不然成了右移运算符↓
priority_queue<int, vector<int>, greater<int> > c;
//这样就是小顶堆
// vector<int> 是承载底层数据结构堆（heap）的容器
// less<int> 是对第一个参数的比较类
// less<int> 表示数字越大优先级越高
// greater<int> 表示数字越小优先级越高
```

**结构体**

```c++
struct fruit {
    string name;
    int price;
    // 重载运算符
    // 价格高的优先级高
    // 默认是值越小优先级越高
    friend bool operator < (const fruit &f1,const fruit &f2) {
        return f1.price < f2.price;
    }
};
priority_queue<fruit> q;
// or
struct cmp {
    // 价格高的优先级高
    bool operator () (const fruit &f1, const fruit &f2) {
        return f1.price > f2.price;
    }
};
priority_queue<fruit, vector<fruit>, cmp> q;
```

![image-20210402230545841](https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/20210402230553.png)

**注意**：使用 `top()` 函数前，必须使用 `empty()` 判断优先级队列是否为空

## 七、stack

栈，**后进先出**

### 1、定义

```c++
#include <stack>
using namespace std;

stack<typename> name;
```

### 2、访问

由于栈是一种后进先出的数据结构，所以只能通过`top()` 来访问**栈顶**元素

### 3、常用函数

**1、push()**

`push(x)` 将`x`入栈，O(1)

**2、top()**，获取栈顶元素，O(1)

**3、pop()**，弹出栈顶元素，O(1)

**4、empty()**：检测是否为空，O(1)

## 八、pair

把两个元素绑在一起，但又不想定义结构体时，**pair**是一个替代品，也就是说**pair**可以看作一个内部有两个元素的结构体。

**map**的内部实现涉及**pair**。可以作为**map** 的键值对来插入。

### 1、定义

```c++
#include <utility> // 可以使用 <map>
using namespace std;

pair<typename1, typename2> name;
pair<typename1, typename2> name(value1, value2);

// 临时构建
pair<type1, type2>(value1, value2);
// or
make_pair(value1, value2);
```

### 2、访问

pair只有两个元素，分别是 **first** 和 **second**，按正常结构体去访问就好

### 3、常用函数

**比较操作数**，以<first, second> 元组方式比较

## 九、algorithm头文件下的常用函数

```c++
#include <algorithm>
using namespace std;
```

**1、max()、min()、abs()**

```c++
max(x, y);
min(x, y);

abs(x);
// x 只能是整数，浮点数的绝对值要使用 math 头文件下的 fabs(x)
```

**2、swap()**

```c++
swap(x, y);
// 交换 x, y 的值
```

**3、reverse()**

```c++
reverse(it, it2);
// 将数组指针在 [it, it2) 之间的元素
// 或者容器的迭代器在 [it, it2) 范围内元素
// 进行反转
```

**4、next_permutation()**

给出一个序列在**全排列**中的下一个序列。到达最后一个时返回`flase`

```c++
int a[10] = {1, 2, 3};
do{
    printf("%d%d%d\n", a[0], a[1], a[2]);
} while(next_permutation(a, a+3));
```

**5、fill()**

可以把**数组**或**容器**中的某一段区间赋为某个值。和**memset**不太一样，**fill**可以赋范围内的所有值

```c++
fill(it, it2, value);
// it - (it2-1) 赋值为 vlaue
```

**6、sort()**

排序函数，效率较高。一般不推荐**C语言**中的`qsort()`，因为其比较繁琐。

**sort**规避了**经典快排**中可能出现的复杂度退化到 **O($n^2$)** 的极端情况。

**STL**标准容器中，只有 **vector**、**string**、**deque**是可以使用 **sort**。因为像是 **set**、**map**这种内部是使用**红黑树**实现的，元素本身就有序

```c++
sort(首元素地址, 尾元素的下一个地址, 比较函数(非必填));
// 默认进行递增排序

bool cmp(int a, int b) {
    return a>b;
    // a>b 时把 a 放在 b 前面
}

// struct 数组的排序
struct node{
    int x, y;
};
// 按 x 的值递减排序
node ssd[10];
bool cmp(node a, node b){
    return a.x > b.x;
}
```

**7、lower_bound() 和 upper_bound()**

需要在一个**有序**数组或者容器中使用。O(log(last-first))

```c++
lower_bound(first, last, val);
// 返回 [first, last) 内第一个值大于等于 val 的元素的位置
// 数组返回指针
// 容器返回迭代器

// 如果不存在这样的元素，返回可以插入该元素的 指针 或 迭代器
```



## 公共函数

**1、clear()**

`clear()`用来清空vector中的所有元素

**2、erase()**

erase()有两种用法：

- 删除单个元素：erase(it)，删除迭代器处的元素
- 删除一个区间内的所有元素：`erase(first,last)`，即删除(first,last )区间内的元素

**3、size()**

`size()`用来获得vector中元素的个数

## C++11

**emplace_front**、**emplace** 和 **emplace_back**

这些操作构造而不是拷贝元素到容器中，这些操作分别对应**push_front**、**insert** 和**push_back**，允许我们将元素放在容器头部、一个指定的位置和容器尾部

### 两者的区别 

当调用insert时，是将对象传递给insert，对象被拷贝到容器中，而当我们使用emplace时，是将参数传递给构造函，emplace使用这些参数在容器管理的内存空间中直接构造元素。
