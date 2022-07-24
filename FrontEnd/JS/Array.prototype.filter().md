---
date: 2022-07-24
aliases(別名): []
tags: JS
---
# Metadata
status ::<br>
Note Type ::<br>
Topics :: {}
(使用`[Topic],[Topic]`格式)[[js]] [[array]]
---
## 語法
```javascript
// Arrow function
filter((element) => { /* ... */ } )
filter((element, index) => { /* ... */ } )
filter((element, index, array) => { /* ... */ } )

// Callback function
filter(callbackFn)
filter(callbackFn, thisArg)

// Inline callback function
filter(function(element) { /* ... */ })
filter(function(element, index) { /* ... */ })
filter(function(element, index, array){ /* ... */ })
filter(function(element, index, array) { /* ... */ }, thisArg)

```


### [參數](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter#parameters "Permalink to Parameters")

`callbackFn`

Function is a predicate, to test each element of the array. Return a value that coerces to `true` to keep the element, or to `false` otherwise.

The function is called with the following arguments:

`element`

The current element being processed in the array.

`index`

The index of the current element being processed in the array.

`array`

The array on which `filter()` was called.

`thisArg` Optional

Value to use as `this` when executing `callbackFn`.