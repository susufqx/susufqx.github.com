---
layout: post
title:  "python中datetime的学习和理解"
date:   2018-08-20 09:21
categories: blog
header-img: /images/paris.jpg
tags:
    - Python
    - datetime
    - UTC
    - timestamp
    - timezone
---

### 一、datetime

我们这里讨论的datetime是python语言中的datetime模块，这是date和time模块的结合。它主要包含六个类(class):
* class timedelta
* class datetime
* class date
* class time
* class tzinfo
* class timezone

其中timezone是tzinfo的子类（subclass），我们这里不讨论那么细，具体学习可以参考官方文档 https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior 。因为在我的工作中，遇到过好几次需要计算时间戳的情况，所以我去参考了datetime的相关资料。由于我们的开发是在中国，本地测试自然也是中国时区，然而我们的产品正式环境的部署是在印度那边，所以对于时间戳的传递需要考虑得仔细一点，稍微不注意，可能就弄错了。于是我们统一传达的是UTC时间，这样不论是哪个时区，服务器都会自动换算成当地的时间。中国与印度相差2.5小时，所以如果印度需要16：00这个时间点，我们在本地测试只要是18：30的那个就正确了。或许直接通过函数方法获取时间戳还是容易的，但是如果涉及到具体的计算，比如给每下一个星期六上午11：30（印度时间）的时间戳，这个就要考虑了。计算时，我们得统一成印度或者中国的时间再换算，但是具体的点是给的印度时间，所以统一换算成印度时间是最容易的，因为这样我们考虑时差时是不需要考虑多一天或者少一天的情况，因为最终的那个时间点是确定了的。可能说的有些啰嗦了，我们给个具体的例子来进行分析吧。这也是我的学习分享。

先说说这六个类吧。timedelta，顾名思义就是时间的变化

……未完待续……
