---
title: "ShadowSocks 服务端配置"
date: 2017-04-17
---

## 安装 ShadowSocks

Debian / Ubuntu:

```bash
$ apt-get install python-pip
$ pip install shadowsocks
```

CentOS:

```bash
$ yum install python-setuptools && easy_install pip
$ pip install shadowsocks
```

## 配置文件

```bash
$ vim /etc/shadowsocks.json
# {
#    "server": <server_ip>,
#    "server_port": 8388,
#    "local_address": "127.0.0.1",
#    "local_port": 1080,
#    "password": <password>,
#    "timeout": 300,
#    "method": "aes-256-cfb",
#    "fase_open": false
# }
```

## 客户端

Mac 使用 GoAgentX。
链接: [https://pan.baidu.com/s/1c1LoCi0](https://pan.baidu.com/s/1c1LoCi0) 密码: phsy

* 本地端口：1080
* 服务器地址：<server_ip>
* 服务器端口：8388
* 连接超时（秒）：60
* 服务密码：<password>
* 加密方式：aes-256-cfb
