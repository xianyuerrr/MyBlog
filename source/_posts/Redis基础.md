---
title: Redis基础
tags:
  - Redis
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2021-12-28 15:14:31
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/95024771_p0.png
---
# Redis 基础

## 基本介绍

Redis 是一个开源的**内存中**的数据结构存储系统，可以用作数据库、缓存和消息中间件 MQ。

Redis 很快，其基于内存操作，CPU 不是其性能瓶颈，其瓶颈是内存和网络带宽，所以其使用的是单线程（没必要用多线程）。

```
# 测试连接
ping

# 新建 kv 对
set key value
setex(set with expire) key time value
setnx(set if not exist) key value
# 新建多个 KV 对，原子性操作
mset [key1 value1 key2 value2]
msetnx [key1 value1 key2 value2]

# key 是否存在
exists key

# 得到 key 对应的 value
get key
mget [key1 value1 key2 value2]

# 移动 key 到 1 号数据库
move key 1

# 列出所有 key
keys *

# 设置 key 过期时间
expire key

# 查看 key 类型
type key

# 清除当前数据库内容
FlushDb
# 清除数据库内容（共 16 个）
FlushAll
```

## 数据类型

### String

```
strlen key
append key str

# 自增
incr key
# 自减
decr key
# 自增 step
incrby step key
# 自减 step
decrby step key
# 切片 [start, end]
getrange key start end
setrange key start end
```

## List

```
# 添加元素
LPush RPush

# 移除元素
LPop RPop

# 移除 n 个元素
LRem list n value
RRem list n value

# 删除 list[start, end]
L

# 返回 list[start, end]
LRange list start end

# 返回 list 长度
LLen list
```

