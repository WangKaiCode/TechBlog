---
title: Debian初始化配置
published: 2026-04-28
pinned: false
description: Debian初始化配置，方便后续使用
tags:
  - Debian
category: Linux
author: WangKaiCode
sourceLink: https://github.com/WangKaiCode/TechBlog/src/content/posts/
draft: false
date: 2026-04-28
image: ""
---
>**由于Debian系统正常安装完成后在使用上还有诸多不便，现将其列举如下，同时计划使用AI配合编写脚本实现自动化配置。**
# 1. 用户加入sudo用户组
首先切换到`root`用户，执行下面的命令。
```
usermod -aG sudo 用户名
```
修改完后重启系统。
登录用户后查看是否修改成功，输入下面的命令，检查是否有sudo用户组。
```
groups
```

# 2. 更改软件源
> 这一步可以参考中科大的Debian镜像源设置 [Debian - USTC Mirror Help](https://mirrors.ustc.edu.cn/help/debian.html#__tabbed_3_1) 

修改`/etc/apt/sources.list`
```
# 默认注释了源码仓库，如有需要可自行取消注释
deb http://mirrors.ustc.edu.cn/debian trixie main contrib non-free non-free-firmware
# deb-src http://mirrors.ustc.edu.cn/debian trixie main contrib non-free non-free-firmware
deb http://mirrors.ustc.edu.cn/debian trixie-updates main contrib non-free non-free-firmware
# deb-src http://mirrors.ustc.edu.cn/debian trixie-updates main contrib non-free non-free-firmware

# backports 软件源，请按需启用
# deb http://mirrors.ustc.edu.cn/debian trixie-backports main contrib non-free non-free-firmware
# deb-src http://mirrors.ustc.edu.cn/debian trixie-backports main contrib non-free non-free-firmware

deb http://mirrors.ustc.edu.cn/debian-security/ trixie-security main contrib non-free non-free-firmware
# deb-src http://mirrors.ustc.edu.cn/debian-security/ trixie-security main contrib non-free non-free-firmware
```
# 3. 系统和软件更新
```
sudo apt-get update

sudo apt upgrade
```
# 4. 配置中文字体

# 5. 如有需要，配置代理环境 


