---
layout: post
title: Golang对Google授权登录的学习
date: 2019-03-18 14:30
categories: Golang
header-img: /images/paris.jpg
tags:
- Golong
- Go语言笔记
- Go语言
- Google Auth
---

### 一、Google-api-go-client里的oauth2包
#### 1. 安装
其实google-api-go-client里有很多实用的包，但是我这里我们只讨论oauth2这部分。执行以下代码，就可以安装oauth：
```shell
go get google.golang.org/api/oauth2/v2
```

#### 2.简单使用
因为具体的实例当中，我这边只接受到一个id_token，所以这里我们只讨论和id_token相关的部分。另一个关键的token是access_token，等以后遇到我会添加上去。因此这边的讨论只涉及到id_token，主要是对token的验证。
