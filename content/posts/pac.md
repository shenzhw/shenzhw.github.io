---
title: "PAC文件解析"
date: 2023-11-04T21:27:30+08:00
draft: false
---

维基百科有详细的解释[PAC](https://en.wikipedia.org/wiki/Proxy_auto-config)文件到底是什么。

```javascript
function FindProxyForURL (url, host) {
  return 'PROXY proxy.example.com:8080; DIRECT';
}
```
和浏览器之间的接口其实就是这个函数，只要按特定的格式返回就行了，浏览器根据返回结果决定是否走代理、走哪个代理。

返回值的格式规定如下：
```shell

returnValue = type host,":",port,[{ ";",returnValue }];
  type        = "DIRECT" | "PROXY" | "SOCKS" | "HTTP" | "HTTPS" | "SOCKS4" | "SOCKS5"
  host        = UTF16String       (* ECMA262-compatible UTF16 string *)
  port        = UTF16String       (* Digits *)
```

如果走HTTP代理的话，要写成这样：
```javascript
return 'PROXY 192.168.3.5:1087; DIRECT';
```
这里其实有一个容错机制，先走代理，如果走不通，再走直连。

这个架构方案的核心其实是gost，是时候研究一下gost的源码了。