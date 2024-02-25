---
title: "visual studio code plugin development"
date: 2024-02-24T19:00:30+08:00
draft: false
---
今天参考[教程](https://code.visualstudio.com/api/get-started/your-first-extension)开发第一个visual studio code插件，记录一下。

### 升级node版本
本地的node版本太旧了，执行以下命令时报错。
命令：
```shell
yo code
```

报错信息：
```log
Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/usr/local/lib/node_modules/stream/promises' imported from /usr/local/lib/node_modules/yo/node_modules/mem-fs/dist/index.js
```
升级node版本的方法：
```shell
sudo npm install n -g
sudo n stable
```
升级完检查node版本，已升级到v20.11.1。
然后再执行`yo code`命令发现已经没有报错了。


