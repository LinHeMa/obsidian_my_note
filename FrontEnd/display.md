[[css]] [[flex_container]] 
---
date: [[2022-07-26]]
title: display
aliases: []
tags:
  - css
  - flex
  - display
category: [[css]]
from: 
---
在認識了`normal flow`中`BFC`與`IFC`的概念後，我們要來認識以這兩個佈局規則為基準的`display`屬性。`display`屬性也有特殊的佈局如flex及grid等，但不在此筆記範圍。

## Display基本概念

### Display的outer與inner

CSS的Display屬性可以改變元素對外所參與的佈局環境（outer display type），例如：

-   `inline`  
    參與inline formatting context。
-   `block`  
    參與block formatting context。

也可以為元素創造內部的佈局環境，提供後代元素佈局的規則（inner display type）。對內創造的佈局例如：

-   `flow layout`  
    block container的佈局環境，等於normal flow佈局：IFC水平佈局+BFC垂直佈局。
-   `flow root`  
    創建一個新的BFC時，其內部的佈局叫做`flow root`，一個新的`normal flow`佈局。
-   `flex`  
    彈性盒佈局，該屬性值的元素本身對外仍參與normal flow，可是內部環境為獨立的flex formatting context。
-   `grid`  
    格線佈局，該屬性值的元素本身對外仍參與normal flow，可是內部環境為獨立的彈性盒佈局grid formatting context。

### 所有的Diaplay的屬性值可見[CSS規範](https://www.w3.org/TR/css-display-3/#the-display-properties)：

![](https://i.imgur.com/bt7DrLg.png)

## Display參數值介紹

這篇僅選擇 none ｜ contents | inline ｜ block ｜ inline-block 來介紹

### `display: block`

我們以`<header>`跟`<div>`元素來說明，這兩個元素都是block-level element，它們都是預設`display: block`。  
html：

```html
<header></header>
<div>阿囉哈</div>
<header></header>
```

css：兩個元素的預設都是`display: block`，所以不再累贅聲明一次。

```css
header {
    width: 300px;
    height: 50px;
    border: 5px solid;
}

div {
    width: 300px;
    height: 50px;
    background-color: green;
}   
```

它們的box佔滿`<body>`作為`block container`的寬度，並垂直向下排列。width跟height的聲明也都有效。  
![](https://i.imgur.com/YWn0wq6.png)

### `display: none`

同樣的條件，對`<div>`元素聲明：

```css
div {
    display: none;
}
```

`<div>`的box被忽略，不予顯示  
![](https://i.imgur.com/zZGnh8T.png)

### `display: contents`

相同條件下，對`<div>`元素聲明：

```css
div {
    display: contents;
}
```

`<div>`的box被取代成只有contents area的box，只顯示內容文字。  
![](https://i.imgur.com/alcJ280.png)

### `display: inline`

相同條件下，對所有元素聲明：

```css
header {
    display: inline;
}

div {
    display: inline;
}
```

`<div>`及`<header>`成為inline box，參與IFC，一個接一個水平排列，且width及height聲明無效。  
![](https://i.imgur.com/CljuJIt.png)

### `display: inline-block`

相同條件下，對所有元素聲明：

```css
header {
    display: inline-block;
}

div {
    display: inline-block;
}
```

`<div>`及`<header>`對外參與IFC佈局，對內創建了BFC佈局，成為一個block container，width與height聲明有效。  
![](https://i.imgur.com/NDPJanF.png)

而`<div>`及`<header>`內部就是一個新的normal flow的環境，block box參與BFC ; inline box參與IFC：

```html
<header>
  <span>你好</span>
  <span>你好</span>
  <span>你好</span>
  <p>三瓦滴咖</p>
</header>
<div>
  ...
</div>
<header>
  ...
</header>
```

![](https://i.imgur.com/8AYi3Mi.png)

CSS的`display`屬性筆記告一段落，接下來我們會認識讓元素脫離`normal flow（out of flow）`的`float`屬性，以及其定位參數。