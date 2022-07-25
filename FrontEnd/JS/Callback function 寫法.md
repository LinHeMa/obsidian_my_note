---
date: 2022-07-25
title: Callback function 寫法
aliases: []
tags:
  - callbackFunction
category: function
from: 
---
[[callback function]][[js]][[function]]
## callback function 寫法
- 匿名函式
	```js
	setTimeout(function(){
		alert("hello!");
	},1000)
	```
- 箭頭函式

	```js
	setTimeout(()=> alert("hello!") ,1000)
	```
#### 有arguments 的callback fn
```js
const nameInput = document.getElementById('name');
const messageTextArea = document.getElementById('message');

const focusHandler=(e)=>{
  e.target.className='highlight';
};

const blurHandler=(e)=>{
  e.target.className='';
}

nameInput.addEventListener('focus',focusHandler)
nameInput.addEventListener('blur',blurHandler)

messageTextArea.addEventListener('focus',focusHandler)
messageTextArea.addEventListener('blur',blurHandler)
```
