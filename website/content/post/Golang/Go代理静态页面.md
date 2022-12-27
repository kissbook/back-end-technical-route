---
title: "Go代理静态页面"
date: 2022-09-03T15:13:00+08:00
tags: ["GO", "HTML"]
categories: ["后端"]
author: "张伟"
---


基于Go语言实现的静态网页加载，甚至可以自动打包到二进制文件中去,使用特别简单，联合Gin实现高并发性能

## 1. 安装

      go get github.com/gounits/gohtml

## 2. 使用

![img.png](/img/Go代理静态页面-目录.png)

fs文件夹是存放web静态文件

```golang
package main

import (
	"embed"
	"github.com/gin-gonic/gin"
	"github.com/gounits/gohtml"
)

//go:embed fs
var efs embed.FS

func main() {
	r := gin.Default()
	r.Use(gohtml.NewFs(efs))
	//r.Use(gohtml.New("fs"))
	if err := r.Run(":8080"); err != nil {
		panic(err)
	}
}

```

![img_2.png](/img/Go代理静态页面-HTML.png)

## 3. 打开浏览器

    click http://localhost:8080/ 如果访问到下面，说明执行成功！

![img_1.png](/img/Go代理静态页面-打开成功.png)
