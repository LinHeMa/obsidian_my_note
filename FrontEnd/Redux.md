---
date: 2022-10-20
title: Redux
aliases: []
tags:
  - redux
  - react
  - js
  - state_management
  - flux
  - ankiReact
category: 
from:  
---

## 延伸閱讀
[[译]图解Redux - A cartoon Intro to Redux - 简书 (jianshu.com)](https://www.jianshu.com/p/85086337645d)


![[Pasted image 20221020150216.png]]

# Steps 
1. 使用者的動作觸發**dispatch**
2. call **action creator**
3. action creator returns an **action**
4. action sent to **all reducers**
5. set value
6. **all reducers** 執行 the action and return new state
7. notify containers of the changes to state
8. re-render with new props
![[Pasted image 20221020150837.png]]
1.  透過 `store.dispatch(action)` 發送 **action** ， action 是透過 **action creator** 產生的物件。
2.  發送 **action** 後，Redux 的 **store** 會呼叫代入 `createStore()` 裡面的 **reducers** 函式，並傳入當前的資料狀態（previousState）和動作（action），每個 reducers 函式便可以取用到 `previousState` 和 `action`，並回傳新的 state。
3.  Redux 的 **store** 會掌握所有透過 **reducers** 回傳而來的新 **state**，並重新整合成單一的 state。
4.  所有透過 `store.subscribe(listener)` 註冊的 listener 機會被執行，並且可以透過 `store.getState()` 取得最新的資料狀態。
<!--SR:!2022-10-25,3,250!2022-10-25,3,250!2022-10-25,3,250!2022-10-25,3,250!2022-10-25,3,250!2022-10-25,3,250!2022-10-25,3,250-->


# Redux 
### Actions
- actions 可以想像是一包一包的資料（payloads of infomation），將資料從app運送到 redux store
- redux 的 store只會從actions 獲取資料。
- 唯一發送actions 到 store的方法 就是透過`dispatch()`

```javascript
   Example-
const  ADD_TODO = 'ADD_TODO'

{
   type:ADD_TODO,
   text: 'Build my first redux app'
}
```

### Action Creators
- 用來創造actions 的函式，return action
```javascript
function addToDo(text) {
   return {
    type: ADD_TODO,
    text    
   }
}
```
### Reduces 
- 這裡定義了怎麼樣的actions 會對state產生相對應的改變，所有的state change規則都會在這裡被定義清楚
### Store
1.  存放app的state
2.  允許`getState()`可以拿到store裡的state
3.  允許`dispatch()`可以改變store裡的state
4.  Register listerneres via suscriber(listener)