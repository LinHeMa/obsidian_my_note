---
date: 2022-10-22
title: useState VS useRef
aliases: []
tags:
  - ankiReact
  - react
  - lifecycle
  - hooks
  - functional_component
category: 
from: 
---
![[Pasted image 20221022175729.png]]

![[Pasted image 20221022175809.png]]
## The differences between `useRef` and `useState` at a glance

The following differences have already been discussed in detail but are presented here again in a succinctly summarized form:

- 兩者都可以在render之間保存資料，但只有**useState**的資料更新時會觸發re-render
- useRef return **物件**，useState 回傳**陣列[state ,updater function]**
- useRef return的物件是**mutable**，state是**immutable**，必須透過 **updater function**去更新
- **useRef**可以直接操控DOM

# Why `let` can’t replace `useRef`
??
因為let 有hoisting的機制，在每次re-render之後，會在mounting 因為`let`把變數宣告成undefined，所以沒有辦法在renders之間保持data