---
title: Mac终端使用shadowsocks代理
categories:
  - Mac
tags:
  - Mac终端
  - shadowsocks
abbrlink: 5d5adef1
date: 2020-01-15 10:20:21
---
配置Mac终端使用shadowsocks代理。<!--more-->

##### 一、配置
- **shadowsocks配置如下：**
![](/shadowsocks_config.jpg)
- 终端 执行vim ~/.zshrc 打开.zshrc文件。
- 添加如下代理配置：
```
	# proxy list
	alias proxy='export all_proxy=socks5://127.0.0.1:1086'
	alias unProxy='unset all_proxy'
```
- `:wq`保存退出。
- 执行`source ~/.zshrc`

##### 二、使用
- 开启终端代理命令：`proxy`
- 解除终端代理命令：`unProxy`
- 查看是否成功：
执行命令`curl cip.cc`:
```
	~  curl cip.cc
	IP	: 45.130.147.245
	地址	: 欧盟  欧盟

	数据二	: 美国

	数据三	: 欧洲

	URL	: http://www.cip.cc/45.130.147.245
```
执行命令`curl -L ip.cn`:
```
	 ~  curl -L ip.cn
	{"ip": "45.130.147.245", "country": "俄罗斯", "city": ""}
```