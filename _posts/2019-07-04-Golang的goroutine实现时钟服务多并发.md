---
layout: post
title: 实现时钟服务多并发
date: 2019-07-04 15:01
categories: Golang
header-img: /images/paris.jpg
tags:
  - Golong
  - Go语言笔记
  - Go语言
  - Goroutine
---

### 1. Golang 的多并发

其实是在读《Go 程序设计语言》这本书，然后读了其中一些章节，进一步了解和熟悉了 goroutine 的概念和使用。书中给出了很典型的一个实现多并发的服务，就是 clock 并发服务。

我们设计一个时钟服务器，每隔一秒钟返回当前时间给客户端。这个例子很简单，尤其是顺序执行的服务器，也就是第一个 client 结束请求，第二个 client 才能正确访问。我们先看下顺序执行服务器的代码:

```shell
package main

import (
	"io"
	"log"
	"net"
	"time"
)

func main() {
	listener, err := net.Listen("tcp", "localhost:8000")
	if err != nil {
		log.Fatal(err)
	}

	for {
		conn, err := listener.Accept()
		if err != nil {
			log.Print(err)
			continue
		}
		func(c net.Conn) {
			defer c.Close()
			for {
				_, err := io.WriteString(c, time.Now().Format("15:04:05\n"))
				if err != nil {
					return
				}
				time.Sleep(1 * time.Second)
			}
		}(conn)
	}
}

```

那么如何才可以使得多个 client 的差不多同时请求，并且各自都可以得到服务端的正确返回呢，其实很简单，我们只需要添加一个单词，两个字母即可`go`。

```shell
	for {
		conn, err := listener.Accept()
		if err != nil {
			log.Print(err)
			continue
		}
		go func(c net.Conn) {
			defer c.Close()
			for {
```

其实就在`func()`之前添加了`go`即可，这样每一次调用该函数，都会起一个新的 goroutine，每个请求都在各自独立的 goroutine 服务中被处理，自然也就实现了并发。

### 2. 客户端的编写

为了方便，我们还是写一个客户端的程序来获取服务上的时钟。

```shell
package main

import (
	"io"
	"log"
	"net"
	"os"
)

func main() {
	conn, err := net.Dial("tcp", "localhost:8010")
	if err != nil {
		log.Fatal(err)
	}
	defer conn.Close()
	mustCopy(os.Stdout, conn)
}

func mustCopy(dst io.Writer, src io.Reader) {
	if _, err := io.Copy(dst, src); err != nil {
		log.Fatal(err)
	}
}
```

对于并发的服务来说，我们可以任意启动多个客户端，同时获取时间，结果这里就不赘述了。其实这个例子的核心，就是让我加深对 goroutine 的理解，这很像其他语言中的多线程编程，只是 goroutine 更小。

### 3. 书中留了一个练习，让把服务改成从传入参数获取端口以及时区，这样模拟出多个不同时区的服务。然后实现一个客户端，能够同时接受这几个服务的返回值，并且输出。我自己做了一个简单的实现。

服务端代码：

clockserver.go

```shell
package main

import (
	"flag"
	"io"
	"log"
	"net"
	"time"
)

func main() {
	p := flag.String("port", "8000", "http listen port")
	tz := flag.String("tz", "Asia/Beijing", "timezone")
	flag.Parse()

	listener, err := net.Listen("tcp", "localhost:"+*p)
	if err != nil {
		log.Fatal(err)
	}

	for {
		conn, err := listener.Accept()
		if err != nil {
			log.Print(err)
			continue
		}
		go handleConn(conn, *tz)
	}
}

func handleConn(c net.Conn, tz string) {
	lc, _ := time.LoadLocation(tz)
	defer c.Close()
	for {
		_, err := io.WriteString(c, tz+"  "+time.Now().In(lc).Format("15:04:05\n"))
		if err != nil {
			return
		}
		time.Sleep(1 * time.Second)
	}
}

```

客户端代码：
clockwall.go

```shell
package main

import (
	"io"
	"log"
	"net"
	"os"
)

func main() {
	addrs := []string{"localhost:8000", "localhost:8010", "localhost:8020", "localhost:8030"}
	for _, addr := range addrs {
		go getTime(addr)
		// mustCopy(os.Stdout, conn)
	}
	for {
	}
}

func mustCopy(dst io.Writer, src io.Reader) {
	if _, err := io.Copy(dst, src); err != nil {
		log.Fatal(err)
	}
}

func getTime(addr string) {
	conn, err := net.Dial("tcp", addr)
	if err != nil {
		log.Fatal(err)
	}
	defer conn.Close()

	mustCopy(os.Stdout, conn)
}

```

其中运行命令，服务端：

```shell
$ go build clockserver.go
$ ./clockserver -port=8000 -tz=Asia/Shanghai & ./clockserver -port=8010 -tz=Asia/Tokyo & ./clockserver -port=8020 -tz=Europe/London & ./clockserver -port=8030 -tz=US/Eastern
```

客户端：

```shell
go run clockwall.go
```

结果自己尝试看吧！
