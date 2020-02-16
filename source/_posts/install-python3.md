---
title: 在麒麟操作系统上安装 Python 3
date: 2020-02-15 22:18:01
tags: Python
categories: 工作记录
---
最近在麒麟操作系统 4.4.131 上安装了 Python3.6，遇到了一些问题，因此在这里记录一下安装过程。因为麒麟操作系统 4.4.131 基于 ubuntu 16.04 进行改造，而 ubuntu 16.04 官方并没有提供相应的安装包，因此可以使用第三方的软件仓库：https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa。

<!-- more -->

deadsnakes 网站上有详细的使用说明，但由于没有适配麒麟操作系统，在执行命令 `sudo add-apt-repository ppa:deadsnakes/ppa` 会有如下的报错：

```python
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Kylin/juniper
```

因此，可以查看网站里面的 `Technical details about this PPA`, 手动添加第三方的 PPA（个人软件包存档，Personal Package Archive），方法如下：

```bash
# 1. 在 /ect/apt/source.list 文件里添加以下两行内容：
# 这里选择的是 Xenial (16.04)
$ sudo vim /etc/apt/sources.list
deb http://ppa.launchpad.net/deadsnakes/ppa/ubuntu xenial main 
deb-src http://ppa.launchpad.net/deadsnakes/ppa/ubuntu xenial main

# 2. 添加密钥
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys F23C5A6CF475977595C89F51BA6932366A755776
```
仓库添加好以后，便可以正常安装指定版本的 Python3：

```bash
$ sudo apt-get update
$ sudo apt-cache search python3.6
$ sudo apt-cache search python3.7
$ sudo apt-get install python3.6 python3.6-dev ...

```
