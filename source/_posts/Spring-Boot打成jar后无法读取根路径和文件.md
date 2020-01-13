---
title: Spring Boot打成jar后无法读取根路径和文件
categories:
  - Java
tags:
  - Spring Boot
abbrlink: 13b294db
date: 2020-01-13 14:50:38
---
记录一下`getContextClassLoader().getResource()`之坑`FileNotFoundException`<!--more-->
今早部署代码到测试环境之后，测试需求的时候出现了`FileNotFoundException`，发现是获取字体路径的时候报错了，很奇怪，在本地调试的时候并未发现此问题。
问题代码如下：
![](/code.png)
排查发现问题如下：
这是因为打包后Spring试图访问文件系统路径，但无法访问JAR中的路径。使用`ClassPathResource`解决问题。
![](/code_fix.png)