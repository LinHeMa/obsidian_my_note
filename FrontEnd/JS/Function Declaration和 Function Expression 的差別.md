---
date: 2022-07-25
title: Function Declaration和 Function Expression 的差別
aliases: []
tags:
  - function
  - declaration
  - expression
category: function
from: 
---
[[js]][[function]][[hoisting]][[algorithm]]
## **Function Declaration**
- 使用function去宣告一個function，所以一定會有名字
- Function declaration不需要變數賦值
- 會在其他code之前先行執行
- 有hoisting
```js
function fn(paramA, paramB) {
    // Set of statements
}
```
---
## **Function Expression**
- 沒有函式名稱
- 可以儲存在變數之中

	>	所以所設定的名稱，是變數（盒子）的名稱，並不是function本身的名稱
- 不會hoisting
```js
var fnExp= function(paramA, paramB) {
    // Set of statements
}
```


|項目|Declaration |Expression|
|-----|-----|--------|
|hoisting|yes|no       |
|name?|yes  |no      |
