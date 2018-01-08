---
layout: post
title: Go实现反向代理
category: 技术
tags: Go
description: Go语言实现反向代理，激活idea
---

### 背景

ubuntu下撞了个idea，没钱激活，由于最新版的idea授权服务器封得很严，所以才文朋友找了个教程尝试了一下，效果还不错，特此分享出来。

### 反向代理基本介绍

其实什么是反向代理，我自己对概念也不是很清楚，但只记得知乎上有个大v用一个开饭店的故事对什么是反向代理进行了一番描述：[反向代理为何叫反向代理](https://www.zhihu.com/question/24723688)

### 代码

```
sh
package main

import (
 "flag"
 "log"
 "net/http"
 "net/http/httputil"
 "net/url"
)

type handle struct {
 reverseProxy string
}

func (this *handle) ServeHTTP(w http.ResponseWriter, r *http.Request) {
 remote, err := url.Parse(this.reverseProxy)
 if err != nil {
 log.Fatalln(err)
 }
 proxy := httputil.NewSingleHostReverseProxy(remote)
 r.Host = remote.Host
 proxy.ServeHTTP(w, r)
 log.Println(r.RemoteAddr + " " + r.Method + " " + r.URL.String() + " " + r.Proto + " " + r.UserAgent())
}

func main() {
 bind := flag.String("l", "0.0.0.0:8888", "listen on ip:port")
 remote := flag.String("r", "http://idea.imsxm.com:80", "reverse proxy addr")
 flag.Parse()
 log.Printf("Listening on %s, forwarding to %s", *bind, *remote)
 h := &handle{reverseProxy: *remote}
 err := http.ListenAndServe(*bind, h)
 if err != nil {
 log.Fatalln("ListenAndServe: ", err)
 }
}
```

### 使用方法

安装Go
执行命令：

```
sh
go build xxx.go
go run xxx.go
```

lisence注册那儿地址填localhost:8888，点激活即可
