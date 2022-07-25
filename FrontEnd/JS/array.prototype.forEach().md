---
date: 2022-07-25
title: array.prototupe.forEach()
aliases: []
tags:
  - array
  - forEach()
  - for
category: array
from: 
---
[[js]]  [[array]]
---

## 定義
將陣列內的每個元素傳入「指定函示」並執行
```javascript
const array = [1,2,3,4,5];
array.forEach(x => x*2);
//[2,4,6,8,10];
```
## 語法
```javascript
// Arrow function
forEach((element) => { /* ... */ })
forEach((element, index) => { /* ... */ })
forEach((element, index, array) => { /* ... */ })

// Callback function
forEach(callbackFn)
forEach(callbackFn, thisArg)

// Inline callback function
forEach(function(element) { /* ... */ })
forEach(function(element, index) { /* ... */ })
forEach(function(element, index, array){ /* ... */ })
forEach(function(element, index, array) { /* ... */ }, thisArg)
```
- thisArg
	- 執行`callback function` 的`this`
### example of using index
```javascript
const numbers = [1,2,3,4,5,6,7,8,9,10];

numbers.forEach((number,index)=>{

	console.log(`${index+1})` + index);
})
```
	
## 從for到forEach
```javascript
const items = ['item1', 'item2', 'item3'];
const copy = [];

for (let i=0; i<items.length; i++) {
  copy.push(items[i])
}
```

### after 
```javascript
const items = ['item1', 'item2', 'item3'];
const copy = [];

items.forEach(function(item){
  copy.push(item)
});
```


