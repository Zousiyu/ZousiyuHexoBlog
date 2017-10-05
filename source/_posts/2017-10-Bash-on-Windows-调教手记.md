---
title: Bash on Windows 调教手记
date: 2017-10-05 11:55:47
updated: 2017-10-05 11:55:47
categories:
- Geek
tags:
- Linux
- OS
---

<!-- more -->

# 安装Bash on Windows
启用开发者选项和Linux子系统选项，重启电脑，在命令行内输入`bash`即可自动安装Linux子系统。

{% asset_img setup1.png "启用开发者选项" %}

{% asset_img setup2.png "启用Liunx子系统选项" %}

# 利用X server开启图形界面
这里开启图像界面只针对软件，图形桌面环境体验并不好，不如实体机安装Ubuntu，不建议开启图形化桌面环境。

## 安装X server服务
相同作用的软件应该不少，这里选用[VcXsrv](https://sourceforge.net/projects/vcxsrv/)，软件采用默认设置即可。

接下来编辑一下`bashrc`，这里使用`nano ~/.bashrc`命令手动编辑文件，也可以用其他命令。

{% asset_img bashrc.png "bashrc设置" %}

## GUI测试
安装gedit或者其他有GUI的软件，使用命令行打开。如图，测试成功。

{% asset_img geditc.png "GUI测试" %}

## 中文界面处理
有些软件有中文界面，但是这个Linux子系统没有中文字体，我们需要安装中文字体到这个子系统里面即可正确显示中文。

选用思源黑体[Source Han Sans](https://github.com/adobe-fonts/source-han-sans/tree/release)，使用`sudo cp -r source-han-sans/ /usr/share/fonts/truetype/`直接将**整个字体目录**复制到系统字体目录，重新打开软件，即可正常显示中文。这里测试的软件是nemo。

{% asset_img nemo.png "GUI测试" %}