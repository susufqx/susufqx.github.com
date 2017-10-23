---
layout: post
title:  "Meteor框架下使用Angular4作为前端"
date:   2017-10-17 02:04
categories: blog
tags:
    - Meteor
    - Angular4
    - JavaScript
    - FullStack
    - TypeScript
---

>这是一篇介绍Meteor和Angular4如何结合使用的教程，由于Meteor官方网站提供的是与Angular1结合的案列，所以本着自己研究和分享的态度，决定写一篇自己使用Meteor结合Angular4的文章，具体的实现在GitHub上，https://github.com/susufqx/meteor-angular4-boilerplate。

### 一、meteor框架

Meteor是一个开源的使用Node.JS的支持全栈开发的框架。具体信息和文档可以搜索meteor官网进行查看。

我们可以如此安装meteor，在Linux/OSX下:
```
$ curl https://install.meteor.com/ | sh
```
Windows的用户得去官网下载安装,再次不在累述。

既然需要添加angular4到meteor中去，我们首先得创立一个meteor应用。进入需要安装的目录，然后打开终端:
```
$ meteor create meteor-angular4-app
```
这样我们的```app```已经创立好了，```$cd meteor-angular4-app```，我们可以进入到```app```的文件夹，然后执行```$meteor run```就运行了该程序，浏览器输入"localhost:3000"来查看。

### 二、angular4和meteor

angular4是目前angular最新的版本，对于移动app和web都有很良好的支持。其实meteor的官方网站上有meteor配合angular的案列和使用方法，可是那还是angular1的版本，与现在的angular大相径庭。angular的开发者们为了使得该框架更加便于程序员们使用，从beta版的angular2时代起就选择了TypeScript作为主要开发语言。beta版本的angular与angular1同时存在了很久，直到2016年才发布第一个正式版，不久就进一步优化，发布了如今的angular4。对于写后端尤其是java的程序员来说，angular4简直就是得心应手。

网上很少有meteor和angular4搭配使用的例子，或许是meteor的使用者太少，也有因为angular4太新，原先采用angular1的个人或者团队很难愿意彻底使用新的框架重写他们的代码。

我是因为学习的需要，个人在之前的实习时曾经使用meteor作为开发框架，确实很好用，前后端一并开发，语言统一，有些代码可以共同使用，省去了不少事。可是meteor的默认前端是使用的balze.js，一种更为冷门的前端框架（姑且这么叫做框架）。blaze很简单，不复杂，但是写起JavaScript代码来，却并不简便，甚至很为繁琐，有些编程思想很为过时，对于前端要求高的应用来说，我觉得简直是一种灾难。对于数据的调用，是非常不方便。所以为了使用meteor这么好的全栈框架，也为了使用angular4这么好的前端，我决定两者搭配混合使用。

在meteor导入angular4之前，我们必须删除blaze，否则两个前端同时存在，会出现异常。打开终端，执行：
```
$ cd meteor-angular4-app
$ meteor remove blaze-html-templates
```
这样我们就删除了blaze模板。

由于angular4使用的是TypeScript，是严格的ES2015及其之后的标准，所以对于某些import和语法结构，需要```typings```来支持，否则某些编辑器会出现报错现象。打开终端,
```
$ npm install typings
$ cd meteor-angular4-app
$ typings install registry:env/meteor --global
```
这样，typings的指令和app所需要的文件就安装好了。

然后我们需要对该app配置tsconfig.json文件，打开终端,进入meteor文件夹，创立新文件命名为```tsconfig.json```,里面放入如下内容：
```
{
  "compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "baseUrl": ".",
    "declaration": false,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "lib": [
      "dom",
      "es2015"
    ],
    "module": "commonjs",
    "moduleResolution": "node",
    "sourceMap": true,
    "target": "es5",
    "skipLibCheck": true,
    "stripInternal": true,
    "noImplicitAny": false,
    "types": [
      "meteor-typings",
      "@types/underscore"
    ]
  },
  "include": [
    "client/**/*.ts",
    "server/**/*.ts",
    "universal/**/*.ts"
  ],
  "exclude": [
    ".meteor",
    "node_modules"
  ],
  "compileOnSave": false,
  "atom": {
    "rewriteTsconfig": false
  },
  "files":[
    "typings/index.d.ts"
  ]
}
```
当然里面内容可以根据实际情况进行修改。

接下来我们导入meteor对于angular2的编译包，因为目前尚未找到angular4的包，可是2与4的编译基本类似，所有再次我们使用angular2的。执行，
```
$ meteor add angular2-compilers
$ meteor add dynamic-import
```

### 三、npm导入angular4的依赖包
由于angular4使用的是npm包管理，于是我们只要添加对应的包即可安装angular4。注意，在meteor的应用下，所有的npm命令前面推荐添加上meteor，也就是```meteor npm ...```。

我们进入app，然后输入，
```
$ meteor npm install rxjs zone.js reflect-metadata bcrypt --save
$ meteor npm install @angular/{animations,common,compiler,core,forms,http,platform-browser,platform-browser-dynamic,platform-server,router} --save
$ meteor npm install @angular/{cli, complier-cli, language-service} --save-dev
$ meteor npm install @types/{jasmine, jasminewd2, node} --save-dev
$ meteor npm install autoprefixer, meteor-typings --save-dev
```
当然，我们也可以在```package.json```文件中手动添加包，然后只要执行```meteor npm install```即可。

至此，angular4在meteor中的环境基本搭建完成，下面我们需要简单地添加一些必要文件，因为angular4属于前端，因此所有文件均在```client```文件夹下。

### 四，构建基本angular4的文件
由于只在client文件夹内构件文件，因此打开```client```文件夹，然后首先建立目录```imports/app```，此处```imports```一定不能省略，否则会报错！

我们回到```client```文件夹下面，创立最基本的两个文件```index.html```和```index.ts```,
其中```index.html```内容如下：
```
<head>
  <meta charset="utf-8">
  <title>Meteor-Angular4</title>
  <base href="/">
</head>
<body>
  <meteor-app></meteor-app>
</body>
```
其中```index.ts```内容如下：
```
import 'zone.js';
import 'reflect-metadata';

import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { enableProdMode } from '@angular/core';
import { Meteor } from 'meteor/meteor';
import { AppModule } from './imports/app/app.module';

Meteor.startup(() => {
  enableProdMode();
  platformBrowserDynamic().bootstrapModule(AppModule);
});
```
然后我们进入```imports/app```文件夹内，创建```app.module.ts```，```app.component.ts```和```app.component.html```三个文件，这三个文件是Angular4 app的基本文件，名字就不需要改动了。

其中```app.module.ts```内容如下：
```
// the modules
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule }   from '@angular/forms'; // <-- NgModel lives here
// the components
import { AppComponent } from './app.component';

@NgModule({
  declarations : [
    AppComponent
  ],
  imports : [
    BrowserModule,
  ],
  bootstrap : [
    AppComponent
  ]
})

export class AppModule {}
```
其中```app.component.ts```内容如下：
```
import { Component } from "@angular/core";
import template from './app.component.html';

@Component({
  selector: 'meteor-app',
  template
})

export class AppComponent {
  title = "Welcome to  Meteor Angular4";
}
```
其中```app.component.html```内容如下：
```
<h1 class="text-center">{{title}}</h1>
```
文件内的具体内容可以根据需要改变，至此，Meteor搭配Angular4的基本配置全部完成，我们可以打开应用了。进入Meteor主文件夹，运行
```
$ meteor run
```
我们打开"127.0.0.1:3000",如果显示"Welcome to  Meteor Angular4"就表示我们的配置成功！
