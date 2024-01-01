---
title: Linux实战
tags:
  - Linux
categories:
  - Code
comments: true
toc: true
aplayer: false
dplayer: false
date: 2024-01-21 17:34:27
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/71720801_p0.png
---

# Linux 软件安装

## 软件包管理器
包管理器是方便软件安装、卸载，解决软件依赖关系的重要工具。

- CentOS、RedHat使用yum包管理器，软件安装包格式为rpm
- Debian、Ubuntu使用apt包管理器，软件安装包格式为deb


## rpm
```shell
rpm [-] soft
-q 查询软件包
-i 安装软件包
-e 卸载软件包
-a 所有软件包
```

rpm包的问题：
- 需要自己解决依赖问题
- 软件来源不可靠


## yum
yum源：
- Centos yum源：http://mirror.centos.org/centos/7/
- 国内镜像：https://opsx.alibaba.com/mirror

yum配置文件：
- /etc/yum.repos.d/CentOS-Base.repo
- wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
- yum makecache

```shell
yum install soft 安装软件
yum remove soft 卸载软件
yum list soft 查看软件
yum update soft 升级软件
```


## 源代码安装
1. `wget url`，下载二进制包
2. `tar -zxf soft.tar.gz`，解压二进制包
3. `cd soft`，进入软件包目录
4. `cat README`，查看软件 README
5. `./configure --prefix=/usr/local/soft`，配置程序安装位置
6. `make -j2`，编译，-j2 表示使用两个逻辑 cpu 进行编译，一定程度上加快编译速度
7. `make install`，安装软件

## 内核升级
yum安装：
```shell
uname -r 查看内核版本
yum install kernel 安装内核
```

源代码编译：
- `yum install gcc gcc-c++ make ncurses-devel openssl-devel elfutils-libelf-devel`，安装依赖包
- `wegt -O kernel.xz https://www.kernel.org`，下载内核
- `tar xvf kernel.xz -C /usr/src/kernels`，解压内核
- `cd/usr/src/kernels/linux-5.1.10/ && make menuconfig | allyesconfig | allnoconfig`，配置内核编译参数
- `cp /boot/config-kernelversion.platform /usr/src/kernels/linux-5.1.10/.config`，使用当前系统内核配置
- `lscpu`，查看CPU
- `make -j2 all`，编译
- `make modules_install && make install`，安装内核


## grub配置

配置文件：
- `/etc/default/grub`，默认配置
- `/etc/grub.d/`，详细配置
- `/boot/grub2/grub.cfg`
- `grub2-mkconfig -o /boot/grub2/grub.cfg`，产生新配置文件

