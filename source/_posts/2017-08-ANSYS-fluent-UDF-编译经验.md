---
title: ANSYS fluent UDF 编译经验
date: 2017-08-25 15:11:45
categories:
- Geek
tags:
- CFD
- ANSYS fluent
---

理论上fluent的UDF编译是支持任何C/C++编译器的，但如果用GCC等编译器，恐怕是要修改Makefile文件的，这意味着每个案例都要修改，多没生产力。所以Windows平台就不折腾了，VS挺好。

<!-- more -->

从理论上来讲，ANSYS和VS的版本搭配是无所谓的，只要能够正确指定Visual Studio命令行编译程序路径、include、lib库路径，就能成功实现UDF编译。以ANSYS 16.2和Visual Studio 2017为例，配置编译UDF所需要的**环境变量**。

# 编译器路径

在系统或者用户的**PATH**环境变量中添加如下值，编译器版本按fluent版本设置，一般为64位。

``` cmd
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.10.25017\bin\HostX64\x64
```

# 库路径

Visual Studio 2017中，C/C++的标准库很分散，需要添加到环境变量的路径很多。在系统或者用户的变量中新建环境变量**INCLUDE**，添加如下值，版本号试VS版本而定。

``` cmd
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.10.25017\include
C:\Program Files (x86)\Windows Kits\10\Include\10.0.15063.0\shared
C:\Program Files (x86)\Windows Kits\10\Include\10.0.15063.0\ucrt
C:\Program Files (x86)\Windows Kits\10\Include\10.0.15063.0\um
C:\Program Files (x86)\Windows Kits\10\Include\10.0.15063.0\winrt
```

在系统或者用户的变量中新建环境变量**LIB**，添加如下值，版本号视VS版本而定。

``` cmd
C:\Program Files (x86)\Windows Kits\10\Lib\10.0.15063.0\um\x64
C:\Program Files (x86)\Windows Kits\10\Lib\10.0.15063.0\ucrt\x64
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.10.25017\lib\x64
```

# 测试

启动cmd，测试`nmake`或`cl`命令，获得如下结果，环境变量配置成功。

{% asset_img test_command.png "成功配置VS命令行编译" %}

测试成功后，重启系统，ANSYS fluent重新读取环境变量后，能正常编译UDF，成功编译的输出消息如下。

{% asset_img success_information.png "成功编译UDF" %}