---
title: centerOS 7 相关指令
categories:
  - Linux
tags:
  - centerOS
  - 防火墙
thumbnail: 'https://s2.ax1x.com/2019/12/05/Q8TYDJ.png'
abbrlink: 9d0b5e63
date: 2019-12-05 15:13:13
---
收集的一些centerOS指令。
<!--more-->

#### 一、防火墙相关指令

##### 1.启动防火墙
```
	systemctl start firewalld.service
```
##### 2.查看防火墙状态 
``` shell
	systemctl status firewalld.service
```
##### 3.关闭防火墙
```
	systemctl stop firewalld.service  
```
##### 4.查询某个端口是否开放
```
	firewall-cmd --query-port=888/tcp
```
##### 5.开放某个端口号
```
	firewall-cmd --zone=public --add-port=888/tcp --permanent
```
| 命令 | 含义 |
|:--|:--|
| --zone | #作用域 |
| --add-port=80/tcp | #添加端口，格式为：端口/通讯协议 |
| --permanent | #永久生效，没有此参数重启后失效 |