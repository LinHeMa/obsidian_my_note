---
date: 2022-10-22
title: Virtual DOM
aliases: []
tags:
  - ankiReact
  - react
  - algo
  - web
  - 
category: 
from: 
---
# What is Virtual DOM
Virtual DOM 實際上的作法就是用**物件**來描述 DOM 的結構，在 DOM 的節點需要更動時，不直接修改 DOM，而是 :: 透過 diff 演算法比較 Virtual DOM 修改前與修改後的樹狀結構，然後批次更新真實 DOM 中的節點。

![[Pasted image 20221022171900.png]]

# 初始化Virtual DOM
第一個步驟便是像呼叫 **`React.createElement()`** 的過程。::建立虛擬節點

第二個步驟，**把 vNode 轉換成實際的 Node** 這個過程，會像是將 `{tagName: "div"}` 這樣描述 DOM 的物件轉換成 `<div></div>` 。:: 將虛擬節點轉化成真實節點

最後一個步驟，則是**把產生的 `<div></div>` 掛到真實的 DOM 上。** :: 把節點掛在DOM上（mount）
<!--SR:!2022-10-25,3,250-->

# DIFF Alog
## diff(oldVNode, newVNode)
1.  如果傳入的新節點是 `undefined` ，因為該節點是**將被刪除的節點**，所以回傳的 `patch` 函式中呼叫了 :: `Node.remove()`。
2.  舊節點或是新節點型態是字串 ，此時可以直接比較兩個新舊節點，如果不一樣，則**用新節點取代掉舊節點**。反之，節點**不變化**。
3.  舊節點與新節點的標籤不一樣，::則用新節點取代掉舊節點。
4.  舊節點與新節點的標籤一樣，::繼續往下比較標籤上的屬性以及子節點。