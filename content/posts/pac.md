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