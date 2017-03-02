---
layout: post
title: 阿里云CentOS服务器安装Nginx
categories: Nginx
description: 在阿里云CentOS 6.5上安装Nginx服务器
keywords: 阿里云, centos, nginx
---

在阿里云上买的服务器，我个人喜欢用纯净的镜像，这样可以避免各种软件的污染。阿里云的纯净CentOS镜像是包含了基础库的，比如gcc,g++等。安装nginx需要以下软件

* `pcre` 一个正则表达式库，主要功能是让ngnix支持rewrite
* `zlib` 数据压缩函式库，用于压缩

## 安装pcre
下载，解压pcre

```
cd /usr/local
wget https://sourceforge.net/projects/pcre/files/pcre/8.40/pcre-8.40.tar.gz
tar -zxvf pcre-8.40.tar.gz
```
安装

```
cd /usr/local/pcre-8.40/
./configure
make
make install
```

## 安装zlib
直接使用yum安装

```
yum install -y zlib-devel
```

## 安装nginx
下载，解压nginx

```
cd /usr/local
wget http://nginx.org/download/nginx-1.11.10.tar.gz
tar -zxvf nginx-1.11.10.tar.gz
```
安装

```
cd /usr/local/nginx-1.11.10
./configure --with-pcre=../pcre-8.40 --prefix=/usr/local/nginx
make
make install
```

## 如果需要支持https

先安装openssl

```
yum -y install openssl openssl-devel
```

然后重新编译

```
./configure --with-pcre=../pcre-8.40 --with-http_stub_status_module --with-http_ssl_module --prefix=/usr/local/nginx
```

## 启动nginx

```
cd /usr/local/nginx/sbin
./nginx
```

查看是否已经启动成功，能看到进程说明成功

```
ps aux|grep nginx 
```
