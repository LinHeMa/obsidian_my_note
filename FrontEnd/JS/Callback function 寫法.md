---
date: 2022-07-24
aliases(別名): []
tags: JS
---
# Metadata
status ::<br>
Note Type ::<br>
Topics :: {}
(使用`[Topic],[Topic]`格式)[[callback function]][[js]][[function]]
## callback function 寫法
- 匿名函式
	```
	setTimeout(function(){
		alert("hello!");
	},1000)
	```
- 箭頭函式

	```
	setTimeout(()=> alert("hello!") ,1000)
	```
#### 有arguments 的callback fn
```
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
