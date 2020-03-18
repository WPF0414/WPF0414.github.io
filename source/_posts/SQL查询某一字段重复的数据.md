---
title: SQL查询某一字段重复的数据
categories:
  - SQL
tags:
  - sql
abbrlink: e5a96a82
date: 2020-01-17 11:54:45
---

查询出重复记录。<!--more-->
```
	select * from 表 WHERE 重复记录字段 in ( select 重复记录字段 from 表 group by 重复记录字段 having count(重复记录字段)>1)
```