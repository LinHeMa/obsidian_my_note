---
date: 2022-07-24
aliases(別名): []
tags: []
---
# Metadata
status ::<br>
NoteType ::<br>
Topics :: {}
(使用`[Topic],[Topic]`格式)
# Callback Function

## Callback function 的用途

-   一次性或可重複的計時器
-   被使用者動作觸發
-   透過AJAX從伺服器loading資料
-   在Node.js開啟檔案

---

## Callback function 的定義

一個可以當作paramete的函數

```jsx
function callbackFn(){
	//晾衣服
};

function excuteCallbackFn(callbackFn){
	//洗衣服
};
excuteCallbackFn(callbackFn);
```

<aside> 💡 當作parameter時不需要加括號

</aside>

## Ex1 one-off Timer

## Ex2 color changer