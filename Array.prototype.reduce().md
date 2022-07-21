[[js]][[array]][[number]]

## [語法](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#syntax "Permalink to Syntax")

```
// Arrow function
reduce((previousValue, currentValue) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex, array) => { /* ... */ } )

reduce((previousValue, currentValue) => { /* ... */ } , initialValue)
reduce((previousValue, currentValue, currentIndex) => { /* ... */ } , initialValue)
reduce((previousValue, currentValue, currentIndex, array) => { /* ... */ }, initialValue)

// Callback function
reduce(callbackFn)
reduce(callbackFn, initialValue)

// Inline callback function
reduce(function(previousValue, currentValue) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ })

reduce(function(previousValue, currentValue) { /* ... */ }, initialValue)
reduce(function(previousValue, currentValue, currentIndex) { /* ... */ }, initialValue)
reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ }, initialValue)
```
---
### [參數](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#parameters "Permalink to Parameters")

`callbackFn`

A "reducer" function.

The function is called with the following arguments:

-   `previousValue`: the value resulting from the previous call to `callbackFn`. On first call, `initialValue` if specified, otherwise the value of `array[0]`.
-   `currentValue`: the value of the current element. On first call, the value of `array[0]` if an `initialValue` was specified, otherwise the value of `array[1]`.
-   `currentIndex`: the index position of `currentValue` in the array. On first call, `0` if `initialValue` was specified, otherwise `1`.
-   `array`: the array to traverse.

`initialValue` Optional

A value to which _previousValue_ is initialized the first time the callback is called. If `initialValue` is specified, that also causes `currentValue` to be initialized to the first value in the array. If `initialValue` is _not_ specified, `previousValue` is initialized to the first value in the array, and `currentValue` is initialized to the second value in the array.

### [回傳值](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#return_value "Permalink to Return value")

The value that results from running the "reducer" callback function to completion over the entire array.

---
## [介紹](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#description "Permalink to Description")

The `reduce()` method takes two arguments: a **callback function** and an **optional initial value**. If an initial value is provided, `reduce()` calls the "reducer" callback function on each element in the array, in order. If no initial value is provided, `reduce()` calls the callback function on each element in the array after the first element.

`reduce()` returns the value that is returned from the callback function on the final iteration of the array.

### [什麼時候不要使用reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#when_to_not_use_reduce "Permalink to When to not use reduce()")

Recursive functions like `reduce()` can be powerful but sometimes difficult to understand, especially for less experienced JavaScript developers. If code becomes clearer when using other array methods, developers must weigh the readability tradeoff against the other benefits of using `reduce()`. In cases where `reduce()` is the best choice, documentation and semantic variable naming can help mitigate readability drawbacks.
> reduce() 的trade off是語義化以及可讀性，因此在沒有把握的狀況下盡量不要使用

### [Behavior during array mutations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#behavior_during_array_mutations "Permalink to Behavior during array mutations")

The `reduce()` method itself does not mutate the array it is used on. However, it is possible for code inside the callback function to mutate the array. These are the possible scenarios of array mutations and how `reduce()` behaves in these scenarios:

-   If elements are appended to the array _after_ `reduce()` begins to iterate over the array, the callback function does not iterate over the appended elements.
-   If existing elements of the array do get changed, the values passed to the callback function will be the values from the time that reduce() was first called on the array.
-   Array elements that are deleted _after_ the call to `reduce()` begins _and_ before being iterated over are not visited by `reduce()`.