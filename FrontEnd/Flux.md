---
date: 2022-10-20
id: hash
title: Flux
aliases: []
tags:
  - flux
  - pattern
  - redux
category: 
from: 
anki: true
---
[延伸閱讀](https://www.jianshu.com/p/0ccf27d55e4c)

# flux 架構下的資料操作流程
1.  管理者預先定義好有哪些規則(action)可以使用
2.  管理者預先定義好規則(action)對應到的邏輯運算(store/reducer)是什麼。
3.  操作者透過一個溝通用的函式(dispatch)，把他選擇的規則(action)和需要的參數(payload)丟給管理者
4.  流程/資料透過管理者規定好的方式更新