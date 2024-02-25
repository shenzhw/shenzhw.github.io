---
title: "docker"
date: 2024-02-26T07:36:30+08:00
draft: false
---

### 编写Dockerfile
也可以使用docker init，当然也可以手工书写。
### 本地打镜像
默认会使用本地的cpu架构打镜像，因我使用的机器是macbook m1，服务器的架构为amd64，需加参数"--platform linux/amd64"。
```shell
docker build --tag tgbot:amd64 --platform linux/amd64 .
```
### 镜像上传到服务器

本地机器执行以下命令导出镜像：
```shell
docker save -o imagename.tar tgbot:latest
```
上传镜像到服务器：
```shell
scp imagename.tar ubuntu@server-ip:/home/ubuntu
```
在服务器上执行以下命令导入镜像：
```shell
docker load < imagename.tar
```
启动容器
```shell
docker run tgbot:latest
```