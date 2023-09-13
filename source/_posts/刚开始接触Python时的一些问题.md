---
title: 刚开始接触Python时的一些问题
tags:
  - Python
categories:
  - Code
comments: true
toc: true
date: 2019-10-06 16:40:08
cover: https://cdn.jsdelivr.net/gh/xianyuerrr/PicGo/img/图片/Game/明日方舟/企鹅物流日常.jpg
---

# 刚开始接触Python时的一些问题

## 新版本不是最好的

&emsp;&emsp;查看你的Python版本，最好不要安装太老的版本，同时，也不要以为最新版就是最好的。

```python
python --version
# 或者
python -V
```

&emsp;&emsp;尽量不要使用最新版的Python，在使用的过程中可能会遇到一些奇怪的问题，毕竟第三方库的数量极其庞大，短时间内不能保证所有库都适配。由于版本较新，遇到问题了在网上也不太容易找到解决办法。

## 运行项目

&emsp;&emsp;按住Shift点击右键会出现如下界面，点击**“在此处打开PowerShell窗口”**可以直接在当前目录打开PowerShell窗口。

<img src="https://img-blog.csdnimg.cn/20201109214244759.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="30%" width="30%" alt="截图" align=center/>

&emsp;&emsp;可以使用以下命令运行项目

```python
python -m Project_name
# Project_name是想要运行的项目名 
```

&emsp;&emsp;截图：

<img src="https://img-blog.csdnimg.cn/20201109214709987.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="80%" width="80%" alt="截图" align=center />

&emsp;&emsp;但是对于很多项目，如果是新装的Python，在运行使用了第三方库的项目时大多都会出现以下错误:

1.  找不到第三方库

<img src="https://img-blog.csdnimg.cn/20201109214948851.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="80%" width="80%" alt="截图" align=center />



&emsp;&emsp;这种情况一般安装全部此项目所使用的第三方库之后就会消失，可以使用以下命令安装：

```python
pip install package
# package是你当前需要安装的第三方库的名字
```

2. numpy出错（这代表着一类问题，有些类库出问题时可以使用类似方法解决）

<img src="https://img-blog.csdnimg.cn/20201109215440534.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="100%" width="100%" alt="截图" align=center />

&emsp;&emsp;上图显示是numpy出问题了，使用以下命令查看numpy版本，是1.19.4版本，尝试降低版本再次尝试。(新版本不一定最好)

```python
pip show numpy
```

<img src="https://img-blog.csdnimg.cn/20201109215440453.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="100%" width="100%" alt="截图" align=center />

&emsp;&emsp;卸载numpy1.19.4版本，安装numpy1.19.3版本

```python
pip uninstall numpy
pip install numpy==1.19.3 # 这种方式可以指定安装库的版本
```

<img src="https://img-blog.csdnimg.cn/20201109215440461.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="100%" width="100%" alt="截图" align=center />

## 第三方库下载慢

 &emsp;&emsp;Python安装库默认是从官网下载的，对于部分人来说，从官网下载实在是过于缓慢。这个时候，切换一个源就可以使下载速度提升一个档次。可以使用清华大学的开源镜像站。

&emsp;&emsp;（1）想要临时使用镜像站

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
// 注意：some-package指的是想要安装的库，使用时需要进行更改
```

 &emsp;&emsp;（2）设为默认

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

&emsp;&emsp;之后再进行第三方库的下载安装时就默认从镜像站进行下载了。

&emsp;&emsp;换源命令执行成功的截图：

<img src="https://img-blog.csdnimg.cn/20201109220010780.png#pic_center"  height="100%" width="100%" alt="截图" align=center />

## 路径问题（找不到文件）

&emsp;&emsp;项目路径问题：

<img src="https://img-blog.csdnimg.cn/20201109215440533.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="100%" width="100%" alt="截图" align=center />

&emsp;&emsp;上图的错误是一个**FileNotFoundError**，说明无法找到那个**txt**文本，但是这个文件确实是在目录下的，如下：

<img src="https://img-blog.csdnimg.cn/20201109215440505.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODc0ODM0,size_16,color_FFFFFF,t_70#pic_center"  height="100%" width="100%" alt="截图" align=center />

&emsp;&emsp;根据报错信息，我们可以知道是**Logistic_classify.py**的**line 27**出错了，我们可以在Logistic_classify.py头部添加以下代码来修正运行时的目录，使其能够找到**horseColicTraining.txt**文件（不止这一种方式可以解决此问题）：

```python
import os
os.chdir(os.path.dirname(__file__))
```
