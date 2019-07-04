---
layout: post
title: Golang结构体使用String()定制输出格式
date: 2019-01-31 17:37
categories: Golang
header-img: /images/paris.jpg
tags:
- Golong
- Go语言笔记
- Go语言
---

Golang里不少地方都需要使用到指针类型，这一点和C很像，只是Golang里的指针相对来说比较简单。不过当我们在项目里的时候，由于处理的需要和方便，很多时候我们对于参数和返回值，都是采用指针类型的声明，尤其是对于结构体来说。举个例子：

```shell
type Example struct {

}
```
