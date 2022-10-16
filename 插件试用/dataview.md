---
title: dataview
author: 马鹏飞
category: translation
layout: post
mathjax: yes
Status: waiting
tags: 名词定义
date: 2022-10-16 10:22
---


```dataview
table date AS 创建日期, author as 作者
from #名词定义  
sort date desc 
```
```dataview
task from #名词定义  
```
```dataviewjs
// 修改其中的时间，可以输出当前离倒计时的时间差。
const setTime = new Date("2022-10-16 10:22");
const nowTime = new Date();
const restSec = - setTime.getTime() + nowTime.getTime();
const day = parseInt(restSec / (60*60*24*1000));
const str = "本文件于" + day + "天前创建"
dv.paragraph(str);
```
#now
