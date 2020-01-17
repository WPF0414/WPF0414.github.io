---
title: Linux查询某个时间段的日志
categories:
  - Linux
tags:
  - Linux
abbrlink: '98274668'
date: 2020-01-17 15:41:35
---
查询Linux系统中某个时间段的日志。<!--more-->

**查询某个时间段的日志**
``` bash
	sed -n '/开始时间/,/结束时间/p' 日志文件
	# sed -n '/2020-01-17 08:37:/,/2020-01-17 08:45:/p' catalina.out
```
**查询某个时间段中包含的关键词的日志**
``` bash
	sed -n '/开始时间/,/结束时间/p' 日志文件 | grep "关键词"
	# sed -n '/2020-01-17 08:37:/,/2020-01-17 08:45:/p' catalina.out | grep "key"
```