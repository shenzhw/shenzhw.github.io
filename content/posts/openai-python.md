---
title: "国内环境使用python调用openai的API"
date: 2024-07-06T21:57:30+08:00
draft: false
---

在国内环境访问openai的api，需要突破防火墙限制，所以你要有一个代理。拿我自己的环境来说，我有一个socks代理。本机是mac，让python使用socks代理的方法是：
1. 设置环境变量
```shell
vi .zshrc
```

加入如下内容：
```shell
export http_proxy=socks5://127.0.0.1:1086
export https_proxy=socks5://127.0.0.1:1086
```

2. python安装httpx[socks]包：

```shell
pip install 'httpx[socks]'
```
注意这个单引号不能省略，否则会报错

这样python就会使用socks代理访问openai啦！

如果使用的是requests库，那就需要安装如下包：
```shell
pip install 'requests[socks]'
```