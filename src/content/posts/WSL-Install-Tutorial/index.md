---
title: WSL安装教程
published: 2025-08-20
pinned: true
description: A simple tutorial of the WSL.
tags: [WSL, docker]
category: Linux
licenseName: "Unlicensed"
author: WangKaiCode
sourceLink: "https://github.com/WangKaiCode"
draft: false
date: 2025-08-20
pubDate: 2025-08-20
---

# WSL小白安装教程

## 概述

### [什么是适用于 Linux 的 Windows 子系统？](https://learn.microsoft.com/zh-cn/windows/wsl/about)

> 适用于 Linux 的 Windows 子系统（WSL）是 Windows 的一项功能，可用于在 Windows 计算机上运行 Linux 环境，而无需单独的虚拟机或双重启动。 WSL 旨在为想要同时使用 Windows 和 Linux 的开发人员提供无缝高效的体验。



## 安装

### 启动WSL功能

> 在 Windows 底部的搜索框搜索“启用或关闭 Windows 功能”，勾选“适用于 Linux 的 Windows 子系统” 和 ”虚拟机平台”，需要重启电脑。

### 安装WSL

#### 系统一键默认安装

##### 更新WSL

```powershell
wsl --update
```

> 将 WSL 版本更新为最新版本。 选项包括：
>
> `--web-download`：从 GitHub 下载最新更新，而不是 Microsoft 商店。

```powershell
wsl --install
```

> 安装 WSL 和 Linux 的默认 Ubuntu 分发版。 [了解详细信息](https://learn.microsoft.com/zh-cn/windows/wsl/install)。 还可以使用此命令通过运行 `wsl --install <Distribution Name>`来安装其他 Linux 分发版。 对于有效的发行版名称列表，请运行 `wsl --list --online`。
>
> 等待几分钟，会跳出输入账号密码的界面。首次启动需要设置用户名，输入用户名后进行密码设置，设置好后可以看到Ubuntu启动成功。
>
> 注意：在windows的PowerShell界面使用 `wsl` 命令，而在Linux发行版中使用 `wsl.exe`命令。

### 手动安装

参考这篇文章操作[自定义WSL的安装位置，别再装到C盘啦 - 知乎](https://zhuanlan.zhihu.com/p/263089007)

> 手动下载适用于 Linux 的 Windows 子系统发行版包，把它的后缀改为`.zip`，然后解压到想要安装WSL的目录下，我们可以得到一些文件，双击红框框出的那个ubuntu.exe（其他发行版的话也有类似的程序）,等待一段时间就成功安装到当前目录啦~。
>
> 需要注意的是安装目录的磁盘不能开**压缩内容以便节省磁盘空间**选项，否则会报错`0xc03a001a` 。

## WSL迁移到其他盘

### 查看自己的wsl和ubuntu版本

```powershell
wsl -l -v	
```

### 关闭wsl服务；

```powershell
wsl --shutdown 
```

### 将原位置的ubuntu导出到指定位置；

```powershell
wsl --export <Distribution Name> <FileName>
```

> 将指定分发的快照导出为新的分发文件。 默认为 tar 格式。 文件名可以是`-`，用于标准输入。

### 原WSL注销ubuntu；

```powershell
wsl --unregister <Distribution Name>
```

### 在指定位置导入ubuntu；

```powershell
wsl --import <Distribution Name> <InstallLocation> <FileName>
```

## Windows和WSL文件相互访问

> 1. Windows 访问 WSL 文件：通过 `\\wsl$\<DistroName>` 路径。这里我的是Ubuntu
> 2. WSL 访问 Windows 文件：通过 `/mnt/c/`、`/mnt/d/` 等路径。
> 3. 在 Windows 文件资源管理器左侧可以找到 Linux 的标志，点击 Linux 就可以操作 Linux 文件。

## 彻底卸载

### 查看WSL当前的所有子系统列表

```cmd
wsl --list
```

### 卸载不用的子系统

> 虽然可以通过 Microsoft 应用商店安装 Linux 分发版，但无法通过应用商店卸载它们。
>
> 若要注销和卸载 WSL 分发版使用下列命令：

```cmd
wsl --unregister <DistributionName>
```

> 将 `<DistributionName>` 替换为您目标的 Linux 发行版名称，会使该发行版从 WSL 中注销，以便您可以重新安装或清理它。 **谨慎：** 注销后，与该分发关联的所有数据、设置和软件都将永久丢失。 从应用商店重新安装将安装分发版的干净副本。 例如， `wsl --unregister Ubuntu` 将从 WSL 中可用的分发中删除 Ubuntu。 运行 `wsl --list` 将显示它不再列出。

### 验证

> 再次执行`wsl --list`查看删除的系统是否还存在。

### 卸载适用于 Linux 的 Windows 子系统及其他WSL组件（如WSL 更新或 WSLG 预览版）

> 注意：目前WSL已被微软官方定义为系统组件，并且不提供用户直接右键卸载的方式，所以不建议新手小白强行卸载，下面给出修复重置和强行卸载两种方式。

#### **修复重置（新手适用）**

> 如果因为WSL故障，所以想要重装WSL的话，可以通过这种方式。
>
> 从“设置”>“应用”>“已安装的应用”>“系统组件”找到适用于 Linux 的 Windows 子系统，然后选择重置或者修复。

#### 强行卸载

> 本方法需要用到`geek`这个软件，因为`WSL`属于”系统组件“，无法通过系统的设置将其卸载。

## 本文参考文章

1. [WSL卸载已安装的的子系统详细教程](https://blog.csdn.net/qq_73162098/article/details/145244997)
2. [完全卸载WSL服务详细教程（全网最详细，看完包懂）-CSDN博客](https://blog.csdn.net/qq_73162098/article/details/145329101)
3. [Windows Subsystem for Linux 文档 | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows/wsl/)
4. [如何查看WSL默认安装位置以及挪动其到指定安装路径-CSDN博客](https://blog.csdn.net/tassadar/article/details/142407262)
5. [Windows 10 WSL&Ubuntu 22.04 安装并迁移到 F 盘-CSDN博客](https://blog.csdn.net/qq_23865133/article/details/149807165)
6. [WSL迁移到D/E盘(共需六步完成)_wsl迁移到d盘-CSDN博客](https://blog.csdn.net/weixin_42705114/article/details/131106845)
7. [在如今最好的 Linux 发行版上使用 Linux——WSL 使用 Q&A - 翎钰的小窝](https://blog.lkyu.cf/posts/WSLQA)
8. [自定义WSL的安装位置，别再装到C盘啦 - 知乎](https://zhuanlan.zhihu.com/p/263089007)
9. [WSL2 镜像模式网络配置指南](https://shuo-liu16.github.io/2025/04/14/WSL2镜像模式网络/)