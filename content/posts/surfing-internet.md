---
title: "搭建https服务极简教程"
date: 2024-06-22T16:25:30+08:00
draft: false
---

### 申请AWS账号
已有AWS账号的可以跳过此步骤。

### 申请虚拟机实例
为了节省成本，我们使用Lightsail，最便宜的美区实例每个月仅需$5。

操作系统建议选择Ubuntu22LTS

实例位置很重要，可以根据自己的需要进行选择，选择哪个区域的实例，你上网就是从哪个区域出去的。

可以选择生成新的SSH密钥对或者上传已有密钥对的公钥都行

### 域名绑定ip
推荐用cloudflare做你的域名解析提供商

在cloudflare上新增一条A记录，指向上一步申请的实例，注意选择“仅解析”。

### 安装GOST
本地SSH登陆上一步申请的实例

下载gost，这里选择v2版本：https://github.com/ginuerzh/gost/releases/tag/v2.11.5

启动gost：

```shell
./gost-linux-amd64-2.11.5 -L="http2://username:password@0.0.0.0:443?probe_resist=file:/home/ubuntu/hello.txt"
```

hello.txt文件是防探测用的，这个文件的内容就是你访问https://yourip/时的网页内容，随便写几行字就行

至此，就搭建好了，搭配客户端就可以使用了。

不过，安全起见，最好安装证书。

### 安装证书
1. 安装certbot

```shell
sudo snap install --classic certbot
```

2. 申请证书

这一步一定要保证gost启动，否则证书检测网站连接时会有问题。

```shell
sudo certbot certonly --standalone
```

按照提示输入信息即可。

3. 将申请到的证书copy到gost文件所在的目录

```shell
cp /etc/letsencrypt/live/your-domain-name/cert.pem /home/ubuntu/cert.pem
cp /etc/letsencrypt/live/your-domain-name/privkey.pem /home/ubuntu/key.pem
```

此时重启gost，就自动应用证书了。
