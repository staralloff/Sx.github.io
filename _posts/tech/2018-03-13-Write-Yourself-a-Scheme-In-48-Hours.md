---
layout: post
title: Write Yourself a Scheme In 48 Hours
category: 技术
tags: Haskell
keywords: Scheme Parser
---

## 1. 安装 GHC

1.安装 curl

```
sudo apt-get install gcc libgmp3-dev curl
```

2.cabal update

```
cabal update
```

3.官网下载合适版本
使用命令curl -O下载
我本地安装版本7.10.3,上官网下载ghc-7.10.3-x86_64-deb8-lunix.tar.xz

4.安装ghc之前先要安装依赖

```
sudo apt-get install libgmp3-dev

sudo apt-get install libgmp3c2
```

5.haskell接受一个参数，输出Hello，参数

```
module Main where
import System.Environment

main :: IO ()
main = do
    args <- getArgs
    putStrLn ("Hello, " ++ args !! 0)
```
使用ghc --make filename编译文件
运行执行 ./hello args

后面我们就可以用haskell为自己写一个解释器了，haskell是一门函数式编程语言，其精髓将一切定义为函数，如果你理解怎么用SinA表示Sin3A，我相信你一定也能理解haskell

6.WikiBook地址 & 项目git地址
WikiBook:[Click Here](https://en.wikibooks.org/wiki/Write_Yourself_a_Scheme_in_48_Hours)
git:[Click Here](https://github.com/staralloff/Write-Yourself-A-Scheme-In-48-Hours)
