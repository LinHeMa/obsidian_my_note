---
date: 2022-10-20
title: What is React Router DOM ?
aliases: []
tags:
  - react 
  - js 
  - react-router-dom
  - context
  - SPA
category: 
from: 
---

## [[History API]]

# BrowserRouter

**BrowserRouter** 是 `react-router` 的根節點，它讓包裹在裡面的元件擁有路由的能力。以下說明這個元件的做的事情：

-   使用 `createBrowserHistory` **初始化 history**。
-   定義 `location` 狀態儲存 **`history.location`**，也就是目前網頁在的位置。
-   定義 `history.listen` ，讓儲存目前網頁位置的 `history.location` 改變時，可以**把改變的值儲存到 `location` 中。**
-   最後用 **Context API** 傳遞 `history` 、 `location` 等在子元件用得到的狀態。
# Route

Route 的目的很簡單，:: 匹配目前的 URL 與在 Route 元件上定義的 `path` ，然後渲染符合的元件。

所以首先透過 Context 取得**目前的 `location`** ，然後看看 `props.computedMatch` 有沒有值，如果有值代表使用了 Switch 元件匹配符合的 `path` 。反之，如果沒有值，則代表沒有 Switch 元件，因此，使用 `matchPath` 匹配目前的 URL，也就是 `location.pathname` 與 `path` 是否一樣。

最終，如果 `match` 有值，則代表**定義在 Route 上的 `path` 是符合目前的 URL ，因此渲染在 Route 中的子元件。**
# Link
## Link

Link 的目標為提供使用者 **`<a href="...">`** ，讓使用者點擊後可以在各個元件中路由，但是不會**重新載入頁面**。

我們一樣整理一下這個元件要做的兩件事 ??

-   定義 `handleOnClick` ，讓使用者在點擊時，使用 `event.preventDefault()` 攔截跳轉頁面的行為，然後把目的地 `to` 儲存到 history 中。
-   回傳 `<a href="...">` 並在標籤上註冊點擊事件的 callback function，最後渲染子元件。

# 結論

1.  首先， `<Router>` 元件用  **`history.location`**  初始化 `location` 狀態。
2.  `<Route>` 元件會從 Context 中拿到 `location`，然後渲染符合 `location` 的元件。
3.  當使用者點擊 UI 上的 `<Link>` 時， ::會呼叫 `history.push()` 把定義在 `<Route>` 上的 `to` 放進 history 中，這時瀏覽器上的 URL 就會跟著一起更動，但是不會跳轉頁面。
4.  接著，位置的改動會觸發:: `history.listen()`，進而改變原本儲存在 `<Router>` 中的 `location` 狀態，然後重複以上第 2 步驟。

![[Pasted image 20221022174107.png]]