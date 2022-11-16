---
date: 2022-10-20
title: React.memo
aliases: []
tags:
  - react
  - js
  - memo
  - HOC
category: react
from: 
---
# React.Memo使用時機
1. Component 為pure function
	1. button
	2. footer
2. 元件經常被渲染
3. 大部分都以相同的props，來渲染`component`
4. 渲染的內容較多

# Conclusion
> `React.Memo` is different from **memorization** : `React.Memo` only compare the prevProps value and postProps value ,if same return the memorized value.