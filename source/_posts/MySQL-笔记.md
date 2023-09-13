---
title: MySQL 笔记
tags:
  - MySQL
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2020-12-01 17:28:00
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/OneDrive/图片/pixiv/77045517_p0.jpg
---
# MySql 笔记

## 基础

### DB、DBMS、SQL

**数据库**：
		DataBase，简称 DB。顾名思义，存储数据的仓库，实际上就是一堆文件。这些文件中存储了具有特定格式的数据。

**数据库管理系统**：
		DataBase Management System，简称 DBMS。专门用来管理数据库中数据的，数据库管理系统可以对数据库当中的数据进行增删改查。

常见的数据库管理系统：
			MySQL、Oracle、SQL Server、DB2等...

**SQL**：结构化查询语言
		SQL 是一套标准，程序员通过编写 SQL 语句，使 DBMS 负责执行 SQL 语句，最终来完成数据库中数据的增删改查操作。

三者之间的关系？
		DBMS -- 执行 --> SQL -- 操作 --> DB

### 常用命令

```
# Win 开启服务
net stop 服务名称;

# Win 关闭服务
net start 服务名称;

# MySQL 登录
mysql -uroot -p
```
### SQL 语句的分类

	DQL：
		数据查询语言（凡是带有select关键字的都是查询语句）
		select...
	
	DML：
		数据操作语言（凡是对表当中的数据进行增删改的都是DML）
		insert delete update
		insert 增
		delete 删
		update 改
	
		这个主要是操作表中的数据data。
	
	DDL：
		数据定义语言
		凡是带有create、drop、alter的都是DDL。
		DDL主要操作的是表的结构。不是表中的数据。
		create：新建，等同于增
		drop：删除
		alter：修改
		这个增删改和DML不同，这个主要是对表结构进行操作。
	
	TCL：
		是事务控制语言
		包括：
			事务提交：commit;
			事务回滚：rollback;
	
	DCL：
		是数据控制语言。
		例如：授权grant、撤销权限revoke....

### 单行处理函数

- upper 转换大写
- lower 转换小写
- substr 取子串
- concat 字符串拼接
- length 去空格
- str_to_date 将字符串转换成日期
- date_format 格式化日期
- format 设置千分位
- round 四舍五入
- rand 生成随机数
- ifnull
