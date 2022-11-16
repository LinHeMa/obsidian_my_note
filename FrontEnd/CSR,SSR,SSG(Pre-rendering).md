---
date: 2022-10-22
title: CSR,SSR,SSG(Pre-rendering)
aliases: []
tags:
  - web
  - react
  - ankiReact
  - efficiency
category: 
from: 
---
# CSR (Client Side Rendering)

CSR 如同其名，是將渲染資料的所有過程都交由==瀏覽器==端處理，使用者在瀏覽網站時，第一次跟伺服器請求的 HTML 檔裡面幾乎不包含任何的內容，伺服器並沒有傳入資料到 HTML。接著，::後續會再透過載入的 bundle，也就是 JavaScript 的檔案，再讓 JS 執行 AJAX 跟伺服器請求資料，最後將資料渲染到畫面上。
<!--SR:!2022-10-25,3,250-->

以下是一個常見 CSR 的應用中，伺服器在使用者瀏覽網頁時會回傳的 HTML 檔案，在 HTML 中僅包含一個 `<div>` 的節點，在==bundle==載入後，JS 才會塞入資料到 **`<div>` 的節點**中。

```html
<html>

	<head>
		<link href="/static/css/main.css" rel="stylesheet"> 
	</head>
	 
	<body>
		<div id="app"></div> 
	</body> 
	
	<script src="/static/js/bundle.js"></script> 
</html>
```

## CSR Pros
- 因為 **bundle 需要包含呼叫 API 的程式碼，一般來說整體會檔案大小會比較大一點**，因此載入的時間就會稍微長一些。
- 在載入完之後，也需要**呼叫 API** 也是一段時間成本。
<!--SR:!2022-10-25,3,250-->


## CSR Cons
- 因為 **bundle 在一開始就載入進來，後續渲染畫面就不用不斷地跟伺服器端交互**，體感上會比 SSR 快，而且在切換頁面的使用者體驗也會更好。
- 使用 CSR 對於**伺服器**來說，也會有較小的負擔。

# SSR (Server Side Rendering)
## Brief SSR
在過去的時代，傳統的 SSR 像是 PHP (世界上最棒的語言) 透過**伺服器**端處理任何的資料，然後再直接編譯成 **HTML 檔案**，最後使用者看到的就是**完整包含資料的 HTML**。

## SSR Pros

- better **SEO**

## SSR Cons
- **瀏覽器的畫面很明顯地閃爍**，在這種情況下瀏覽網站的使用者體驗 (UX) 不是很好。
- 使用 SSR 就必須**有個伺服器**一直處理使用者的請求，一直產生有資料的 HTML，並送到瀏覽器端，這樣的工作對於**伺服器**來說是一個負擔。

# SSG (Static Side Generation)

SSG 意味著**所有的內容都在 bulid 的時候都打包進入檔案中**，所以使用者在瀏覽網站時，就可以拿到**完整的 HTML** 檔案。優點除了可以有利於 SEO 之外，還有因為每次使用者拿到的 HTML 內容都不會變，所以還可以**讓 HTML 被 cache 在 CDN 上**，很適合用在**資料變動較小**的網站中，像是部落格、產品介紹頁這種應用中。
<!--SR:!2022-10-25,3,250!2022-10-25,3,250-->

但使用 SSG 這項技術時，除了必須考量到頁面資料**更新頻率**的問題，再者要衡量隨著應用越來越大時，**打包**的時間也會隨之增長。

*此處參考[[SEO]]*


## 速度
前面有提到 CSR 是在**載入 bundle** 後，才跟伺服器要資料，因此使用者會比較慢看到網站的內容。而對於 SSR 來說伺服器會在**頁面中的資料都準備完畢**後，才給使用者有資料的 HTML 檔案，因此在載入速度的體驗上是 **SSR** 更為快一些。而 SSG 則是在 **build** 的時候就已經產生資料，使用者在進入一個網站後，伺服器可以**直接回應已經產生的 HTML 檔案**，而且因為有 **cache** 的機制，載入速度**整體上是三者中最快的**。
<!--SR:!2022-10-25,3,250!2022-10-27,3,250-->

## SSG v.s. SSR

決定關鍵 :: 網站的內容是靜態的，還是需要透過 API 動態的拿到最新的資料。

如果說內容是靜態的，**SSG** 的方式就非常的適合；但如果資料變動很頻繁，需要呼叫 API 拿到最新的資料，那就得依靠 **SSR**，但是 SSR 會影響**伺服器**的資源，所以有時候 SSG 跟 SSR 就是取捨的問題。

## CSR 是可以捨棄的嗎？

如果說伺服器可以承受負擔，而且 SSG 跟 SSR 對於 SEO 從內容上來看都比較好，難道説「可以不用 CSR 嗎」。前面其實已經提到了「SEO 有 200 多項指標」，而如果全面使用 SSR，把所有資料都在伺服器端處理，其實也不一定有利於 SEO。
??
因為，頁面中的有些內容其實不必參與 SEO 的過程，SSR 只需把「對使用者有價值的資料」渲染完畢，把剩下的部分交由 CSR 處理，使用者可以更快地看到內容，有利於 **「First Contentful Paint」** 的評分。