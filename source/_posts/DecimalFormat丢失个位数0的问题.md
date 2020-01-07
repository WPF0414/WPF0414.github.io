---
title: DecimalFormat丢失个位数0的问题
categories:
  - Java
tags:
  - DecimalFormat
abbrlink: e78d8cf4
date: 2020-01-07 11:44:54
---
由DecimalFormat引发出来的问题。<!--more-->
今天早上线上用户提出个问题，打印pdf的时候客户买了`0.72`吨，打印出来为`.72`吨。
排查代码发现我们数量用的是BigDecimal类型，打印pdf的时候使用DecimalFormat转了一下。
相关代码如下：
![](/DecimalFormat.png)
查询了DecimalFormat的用法，发现如下：
api中文帮助文档关于”#”的翻译是错误的，原文为“`zero shows as absent`”译为“如果为0，则不显示”。
改造代码：
![](/DecimalFormat_new.png)

