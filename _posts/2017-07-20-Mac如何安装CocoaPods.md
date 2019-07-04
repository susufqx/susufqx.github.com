---
layout: post
title: "Mac如何安装CocoaPods"
date: 2016-07-20 23:04
categories: Technology
header-img: /images/paris.jpg
tags:
  - iOS
  - CocoaPods
  - Mobile
---

### 一、CocoaPods 是什么

几乎每一种语言都会存在一个包管理工具，就像 Node.JS 的 npm，J2EE 的 Maven 等。iOS 开发自然也有相应的工具，那就是 CocoaPods。

CocoaPods 的源代码就在 Github 上面，现在已经是 iOS 开发必不可少的或者说已经是标准管理工具了。当我们需要使用第三方开源库的时候，CocoaPods 的作用就出来了。

### 二、为什么要使用 CocoaPods

在 CocoaPods 之前，当我们开发项目需要用到第三方开源库的时候，则是需要：

- 把开源库的源代码复制到项目中

- 添加一些依赖框架和动态库

- 设置-ObjC，-fno-objc-arc 等参数

- 管理他们的更新

在使用 CocoaPods 之后，我们只需要把用到的开源库放到一个名为 Podfile 的文件中，然后执行 pod install 就可以了，Cocoapods 就会自动将这些第三方开源库的源码下载下来，并且为我们的工程设置好响应的系统依赖和编译参数。

### 三、CocoaPods 的原理

CocoaPods 的原理是将所有的依赖库都放到另一个名为 Pods 的项目中，然后让主项目依赖 Pods 项目，这样，源码管理工作都从主项目移到了 Pods 项目中。Pods 项目最终会编译成一个名为 libPods.a 的文件，主项目只需要依赖这个.a 文件即可。
