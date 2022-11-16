---
date: 2022-07-31
title: 比較Nodelist與HTML collection的差異
aliases: []
tags:
  - html
  - DOM
category: 
from: 
---
# 透過DOM API取得網頁節點的方法：

```js
//根據傳入的id 名稱，找到DOM裡面相同id名稱的節點。
document.getElementById('idName');

//根據傳入的tag名稱，回傳所有符合條件的NodeList物件。
document.getEleMentsByTagName('tagName');

//根據傳入的class名稱,回傳所有符合條件的NodeList物件。
document.getElementsByClassName('className')

//根據所設定的selector條件(class或id都可以)，回傳第一個符合條件的節點。
document.querySelector('selector');

//根據所給定的selector條件，回傳所有符合條件的 NodeList。
document.querySelectorAll;
```

由以上方法所回傳的可能會有以下三種節點：

-   HTML元素節點(element nodes)
-   文字節點(text node)，包含空白
-   註解節點(comment node)

getElementById與querySelector都是取得單一元素或節點，沒有 index 及 length 屬性。

DOM提供2種節點集合，用於容納多個節點：

## HTML collection：
	由「document.getElementsByTagName()」及「document.getElementsByClassName」查詢後回傳，HTML Collection只收集HTML 元素節點，這個集合不是陣列，不能使用陣列型別所提供的方法，但是有陣列索引(index)及length屬性可以使用，是一個有序的動態集合。

## NodeList：
	由「document.querySelectorAll()」查詢後回傳，除了HTML節點外，也包括文字節點、屬性節點，這個集合同樣不是陣列，不能使用陣列所提供的方法，但是有陣列索引(index)及length屬性可以使用。

## 差別
1.  HTMLCollection是 **HTML 元素**的集合。
	1. 只包含HTML元素節點(element nodes)
2.  NodeList 是一个文字節點的集合。
3. NodeList 與 HTMLCollection 都類似陣列。
4.  NodeList 與 HTMLCollection 都可以使用 length 屬性。
5.  HTMLCollection 元素可以使用 name，id 或index指定特定元素。
	1. `namedItem`
6.  NodeList 只能透過index来取得特定元素。

## 重點！！
The `getElementsByClassName()` and `getElementsByTagName()` methods return a live HTMLCollection.

The `querySelectorAll()` method returns a static NodeList.

The `childNodes` property returns a live NodeList.

HTML Collection是一個動態的集合，節點的變動會及時反應在集合中。

```html
<div id="sword">
  <ul id="fiveHero">
    <li id="firstHero">1 東邪</li>
    <li id="secondHero">2 西毒</li>
    <li id="thirdHero">3 南帝</li>
    <li id="fifthHero">4 北丐</li>
    <li id="lastHero">5 中神通</li>
  </ul>
</div>
```

```jsx
var outside = document.getElementById('fiveHero');
var collection = document.getElementsByTagName('li');
console.log(collection.length);  //5  得出5個HTML元素節點
console.log(collection[1].textContent);  //"2 西毒"
//清空<ul id="fiveHero">下面的節點
outside.innerHTML = '';
console.log(collection.length);  //0 即時更新為0個元素節點
```

本來抓取到的HTML collection集合中有5個`<li>`元素，但是我們用outside.innerHTML =''清空之後，再console.log(collection.length)一次，已經即時更新為0個了。

**NodeList大部分都是即時更新的**，由childNodes屬性返回的NodeList物件是一個動態的集合，但是透過document.querySelectorAll() 及 document.querySelector()取得的NodeList是**靜態**的集合。

```html
<div id="sword">
  <ul id="fiveHero">
    <li id="firstHero">1 東邪</li>
    <li id="secondHero">2 西毒</li>
    <li id="thirdHero">3 南帝</li>
    <li id="fifthHero">4 北丐</li>
    <li id="lastHero">5 中神通</li>
  </ul>
</div>
```

```jsx
var outside = document.querySelector('ul');
var list = document.querySelectorAll('li');  //抓取所有<li>元素節點
console.log(list.length);          //5
console.log(list[2].textContent);  //"3 南帝"
//清空<ul id="fiveHero">下面的節點
outside.innerHTML = '';
console.log(list.length);          //5   沒有即時更新狀態
```

「outside.innerHTML = ''」清空了底下的`<li>`元素，但是 console.log(list.length)仍然為5，沒有更新為0，所以 document.querySelector() 回傳的是一個靜態的集合。

But 人生最厲害的就是那個but！由 childNodes 屬性返回的 NodeList 物件是一個動態的集合，**可以即時更新**集合的狀態。

```html
<div id="sword">
  <ul id="fiveHero">
    <li id="firstHero">1 東邪</li>
    <li id="secondHero">2 西毒</li>
    <li id="thirdHero">3 南帝</li>
    <li id="fifthHero">4 北丐</li>
    <li id="lastHero">5 中神通</li>
  </ul>
</div>
```

```jsx
var outside = document.querySelector('ul');
console.log(outside.childNodes.length);   //5
console.log(outside.childNodes);
// [object NodeList] (11)
//["#text","<li/>","#text","<li/>","#text","<li/>","#text","<li/>","#text","<li/>","#text"]
outside.innerHTML = '';
console.log(outside.childNodes.length);  //0
```

我們抓取了`<ul>`，存在變數 outside 裡面，利用 coconsole.log() 查詢它 childNodes 的長度，然後清空了outside裡面的內容，再查詢一次childNodes.length，果然即時更新變成0了。

HTML collection 還有一個 nameItem() 方法，可以返回集合中 name 屬性和 id 屬性值的元素。

```jsx
<div id="sword">
  <ul id="fiveHero">
    <li id="firstHero">1 東邪</li>
    <li id="secondHero" name="1">2 西毒</li>
    <li id="thirdHero">3 南帝</li>
    <li id="fifthHero">4 北丐</li>
    <li id="lastHero">5 中神通</li>
  </ul>
</div>
```

```jsx
var one = document.getElementsByTagName('li').namedItem('firstHero');
var two = document.getElementsByTagName('li').namedItem('2');
console.log(one);     //<li id="firstHero">1 東邪</li>
console.log(two);     //<li id="secondHero" name="2">2 西毒</li>
```

名稱 |可否即時更新| 
------------ | ------------ 
 | HTML Collection-----------------|      |
 | `document.getElementsByClassName()` | 可以 |
 | `document.getElementsByTagName()` | 可以 |
 | NodeList------------------------|------|
 | `document.querySelectorAll()`     | 不行 |
 | `document.querySelectorAll()` 搭配 `.childNodes`|可以|
