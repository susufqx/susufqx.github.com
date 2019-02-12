---
layout: post
title:  "Mac如何安装CocoaPods"
date:   2016-07-20 23:04
categories: Technology
header-img: /images/paris.jpg
tags:
    - iOS
    - CocoaPods
    - Mobile
---
### 一、CocoaPods是什么

几乎每一种语言都会存在一个包管理工具，就像Node.JS的npm，J2EE的Maven等。iOS开发自然也有相应的工具，那就是CocoaPods。

CocoaPods的源代码就在Github上面，现在已经是iOS开发必不可少的或者说已经是标准管理工具了。当我们需要使用第三方开源库的时候，CocoaPods的作用就出来了。

### 二、为什么要使用CocoaPods

在CocoaPods之前，当我们开发项目需要用到第三方开源库的时候，则是需要：
* 把开源库的源代码复制到项目中

* 添加一些依赖框架和动态库

* 设置-ObjC，-fno-objc-arc等参数

* 管理他们的更新

在使用CocoaPods之后，我们只需要把用到的开源库放到一个名为Podfile的文件中，然后执行pod install就可以了，Cocoapods就会自动将这些第三方开源库的源码下载下来，并且为我们的工程设置好响应的系统依赖和编译参数。

### 三、CocoaPods的原理
CocoaPods的原理是将所有的依赖库都放到另一个名为Pods的项目中，然后让主项目依赖Pods项目，这样，源码管理工作都从主项目移到了Pods项目中。Pods项目最终会编译成一个名为libPods.a的文件，主项目只需要依赖这个.a文件即可。
