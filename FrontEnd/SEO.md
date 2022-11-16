---
date: 2022-10-22
title: SEO
aliases: []
tags:
  - web
  - ankiReact
  - efficiency
  - googlebot
category: 
from: 
---

![[Pasted image 20221022163234.png]]

## 介紹
當我們談到 SEO，我們必須要先了解 SEO 背後的流程是 **crawling** → **indexing** → **ranking** 三個階段，而另一件重要的事是 **「沒有渲染的內容是不會被加入到 indexing 的」**。
<!--SR:!2022-10-25,3,250-->

在 google search engine 團隊不斷的努力，CSR 網站實際上是可以參與 SEO 的，並不像是第一次跟伺服器拿到 HTML 後，發現裡面只有一個 `<div>` 後，就不理這個網站了。

這必須談到 googlebot 有所謂 **second wave of indexing** 技術，如果一個網站有需要被渲染的需求，亦即像是等待 JavaScript 把內容渲染出來，而 googlebot 遇到這種情況會先丟到 **render queue** 裡面，等待**有資源處理渲染任務**後才會回來做這件事。
<!--SR:!2022-10-25,3,250-->

而另一個你需要知道的是 googlebot 每天都要處理數量非常龐大的網站，它必須要有些機制判斷有些內容實際上不必參與 SEO，也就是 **render budget** 的評估機制。

render budget::機制判斷有些內容實際上不必參與SEO

render budget 包括像是**等待渲染的時間太久**、很少人去的網站等因素，則會造成 googlebot 評估一個網站「**不用等到全部的內容渲染完畢後才 indexing**」，因此這種情況下只有部分內容會進入到 indexing 跟 ranking 的階段。所以對使用者來説，比較重要的內容是在 JavaScript 渲染階段才會出現在畫面上，googlebot 有機會不將這些重要的內容納入 indexing 中，最終將會不利於 SEO。

綜合上述，CSR 實際上可以參與 SEO，但是不利於**內容變動快速**的網站，因為 CSR 沒辦法讓 googlebot 快速地拿到需要的內容。這時候 SSR 跟 SSG 就能夠發揮效用，googlebot 不必經過 **second wave of indexing** 就可以迅速地跟伺服器拿到資料，因此有利於內容變動快速的網站做 SEO。

> 當然，以上只是說明了 SEO 的一小部分，根據 Google 工程師 Martin Splitt 在 [JavaScript: SEO Mythbusting](https://www.youtube.com/watch?v=EZtCgrpa6ss&t=968s&ab_channel=GoogleSearchCentral) 這部影片中分享了 SEO 的其中一個秘辛是「它的指標有 200 多種」，上述只是稍微摸到邊而已，有興趣的人再深入去研究吧！?