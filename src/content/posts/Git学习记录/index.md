---
title: Git学习记录
published: 2026-04-28
pinned: false
description: "介绍Git的简单入门使用"
tags: []
category: Git
author: WangKaiCode
sourceLink: https://github.com/WangKaiCode/TechBlog/src/content/posts/
draft: false
date: 2026-04-28
image: ""
---



# What is Git?

> 什么是“版本控制”？
>
> 我为什么要关心它呢？ 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。 
>
> 什么是Git?
>
> Git 是一个免费且开源的分布式版本控制系统，设计用于高效处理从小型到大型项目的一切事务。
>
> 参考文章：[Git book 中文版](https://git-scm.com/book/zh/v2)


## 下载Git

参考文章[Git - 安装 Git](https://git-scm.com/book/zh/v2/起步-安装-Git)

## Git初始化



### 配置用户名和邮箱地址

```bash
git config --global user.name "Your name"
git config --global user.email email@example.com
```

### 查看配置信息

```bash
git config --list --show-origin
```

### 配置GitHub连接和代理



```cmd
//http || https
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890
```





[[从克隆项目到修改并上传到自己 GitHub 仓库的流程（包括私钥配置）](https://www.cnblogs.com/win1998/p/18475990)](https://www.cnblogs.com/win1998/p/18475990)

