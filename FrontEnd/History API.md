---
date: 2022-10-22
title: React Router Dom
aliases: []
tags:
  - html
  - ankiReact
  - web
  - history
category: 
from: 
---
# History


在 `react-router` 中使用的 history 是經過封裝的物件，它提供多種產生 history 物件的方法：

-   `createBrowserHistory` 是一個在瀏覽器中使用 **HTML5 history API 處理 Url**的方法，處理像是這樣的 URL： `example.com/some/path`。這個方法通常必須依賴**伺服器端讓 URL 都映射至 index.html**，否則會出現 404。
-   `createHashHistory` 是使用 **hash tag (#) 處理 URL** 的方法，處理像是這樣的 URL： `example.com/#/some/path`。由於 **# 後的 URL 不會出現在 HTTP 請求中**，所以在請求時都是用 `example.com` 請求 index.html，因此伺服器端不用修改也沒有問題。
-   `createMemoryHistory` 適用在沒有 DOM 的環境，例如 React Native 或是前端的測試。
## Location

Location 物件是 history 中最重要的物件，用於描述**目前頁面 URL 的各種屬性**像是用於 GET 請求的 `search` 、目前頁面的位置 `pathname` 、URL 上的 `hash` 等。

`key` 則是一個唯一用於 ::識別該 Location 的字串。
<!--SR:!2022-10-25,3,250-->
```js
{

pathname: '/here',

search: '?key=value',

hash: '#extra-information',

state: { modal: true },

key: '3wgzwe'

}
```
## Listen

History 是使用 **observer** pattern 讓在外部的程式碼能夠監聽 **Location 的轉變**。每個 history 物件都有 `listen` 函式，它包含一個 **callback function** 參數，當 Location 改變時，將會執行這個 callback function。
```js
history.listen((location, action) => {

console.log(

`The current URL is ${location.pathname}${location.search}${location.hash}`

);

console.log(`The last navigation action was ${action}`);

});
```
<!--SR:!2022-10-25,3,250-->
