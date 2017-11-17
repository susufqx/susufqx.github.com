---
layout: post
title: "初学Objective-C"
date: 2015-05-22 01:11
categories: blog
tags:
- Objective-C
- Foundation
---
Objective-C是c语言的一个超集，可以在扩展名为m的Objective-C代码里任意调用C/C++的函数、方法或者类。

Objective-C不是类似于C语言一样的点语法，这一点很特殊，比Python或者Ruby都显得另类。

Objective-C代码不区分大小写，与C++类似，都是面向对象的语言，我的感觉是和C++很像，但是语法差异大。

#### 1.类的定义
在头文件里，这里建立头文件```Cattle.h```。
```
#import<Foundation/Foundation.h>//我不知道里面包含什么，但是必须引用

@interfaceCattle:NSObject//类定义的开始，类似于C++或者Java中的class，冒号后面是继承NSObject，这里有很多接口和函数，这样可以利于我们的使用，NSObject没有父类
{
  intlegsCount;//这个就是定义变量，和c/C++类似，这里我们定义cattle的leg的数量
}//后面没有分号
-(void)saySomething;//成员函数定义在花括号外面，-号表示这个方法必须实例化后调用，对应的+号表示这个方法不需要实例化，是类方法
-(void)setLegsCount:(int)count;//冒号后面表示这个方法需要调用参数，是count，类型是整形
@end//这里表示类的定义结束
```
#### 2.类的函数方法
由于我们建立了头文件```Cattle.h```，所以我们还得建立一个Cattle.m文件来定义类中的函数。
```
#import"Cattle.h"//此处我们只需要引用刚才建立的头文件即可

@implementationCattle//这里表示具体定义的开始，其实类似于C++中的类名::，只是不需要每个函数写一次
-(void)saySomething
{
  NSLog(@"Hello,I'macattle,Ihave%dlegs.",legsCount);//NSLog就是类似于printf或者cout<<的输出语句，其实它的定义在我们继承的基类NSObject里面，一般NS开头的方法应该都是NSObject里面的方法。这里的@其实怎么说呢，应该是说这里的字符不是String，而是NSString。所以加个@表示区分。
}
-(void)setLegsCount:(int)count
{
  legsCount=count;
}
@end//与之前一样，表示结束
```
#### 3.主函数
对应的我们建立一个主函数的文件```main.m```。
```
#import<Foundation/Foundation.h>
#import"Cattle.h"

int main(intargc,constchar*argv[])//主函数，这个和C++的主函数是一模一样的
{
  @autoreleasepool//此处mac的内存管理的一种方式，自动实现的
  {
    idcattle=[Cattlenew];//id是一种定义模式，我感觉类似于模板，其实这里可以用Cattle代替id，此处就是类的实例化，对象cattle的属性是类Cattle
    [cattlesetLegsCount:4];//所有方法的实现都必须使用[...]，这里典型的不是点语法，类函数的调用直接用了对象名空格方法名
    [cattlesaySomething];
  }
  return 0;//返回值0，与C++一样
}
```

这个实例是我几天前第一次接触Objective-C学习时碰到的，通过这个大概可以了解Objective-C的大体。我自己实例测试过，在主函数里随便使用C/C++的基本函数都可以正常编译。我自己目前的感觉，Objective-C就是一种另类的C++，思想有点类似，只是语法大相径庭。在有C++的基础上，学习Objective-C还是比较容易的。说白了，Objective-C的执行依旧是编译成c语言来执行，只不过多了一层外衣而已，毕竟很多东西的实现直接用c写那是一个相当难而且相当繁杂的任务。
