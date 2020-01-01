---
title: Shadowsocks安装教程
categories:
  - SSR
tags:
  - SSR
abbrlink: ceb8167b
date: 2019-12-31 14:29:38
---

简单的记录一下`SSR`搭建教程。
### 一.安装SSR
本人在使用的是一键安装，也可自行寻找，指令如下：
```
	wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ss-go.sh && chmod +x ss-go.sh && bash ss-go.sh
```
### 二.安装BBR
推荐一键安装，也可自行寻找，指令如下：
```
	wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```
#### 验证Google BBR

``` bash
# 1、第一步：
		sysctl net.ipv4.tcp_available_congestion_control
	# 输出值为：
		net.ipv4.tcp_available_congestion_control = bbr cubic reno
	# 或者为：
		net.ipv4.tcp_available_congestion_control = reno cubic bbr
# 2、第二步：
		sysctl net.ipv4.tcp_congestion_control
	# 输出值为：
		net.ipv4.tcp_congestion_control = bbr
# 3、第三步：
		sysctl net.core.default_qdisc
	# 输出值为：
		net.core.default_qdisc = fq
```
### 三.关闭防火墙
输入以下命令进行验证：
连接不上关闭防火墙，centerOS 7 命令 https://ymxcyn.cn/post/9d0b5e63/

关闭防火墙
``` bash
	systemctl stop firewalld.service #停止firewall
```
``` bash
	systemctl disable firewalld.service #禁止firewall开机启动
```
