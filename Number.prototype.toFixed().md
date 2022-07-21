[[js]] [[number]] [[math]] [[array]]
---
## [語法](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#syntax "Permalink to Syntax")

```
toFixed()
toFixed(digits)
```

Copy to Clipboard

### [參數](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#parameters "Permalink to Parameters")

`digits` Optional

小數位後幾位，如果可以沒有的話會顯示為0

### [Return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#return_value "Permalink to Return value")

A string representing the given number using fixed-point notation.

### [Exceptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#exceptions "Permalink to Exceptions")

[`RangeError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError)

盡量將位數（`digits` ）控制在0~100之間

[`TypeError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)

If this method is invoked on an object that is not a [`Number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number).

### [例子](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#using_tofixed "Permalink to Using toFixed")

```
let numObj = 12345.6789

numObj.toFixed()       // Returns '12346': rounding, no fractional part
numObj.toFixed(1)      // Returns '12345.7': it rounds up
numObj.toFixed(6)      // Returns '12345.678900': additional zeros
(1.23e+20).toFixed(2)  // Returns '123000000000000000000.00'
(1.23e-10).toFixed(2)  // Returns '0.00'
2.34.toFixed(1)        // Returns '2.3'
2.35.toFixed(1)        // Returns '2.4': it rounds up
2.55.toFixed(1)        // Returns '2.5': it rounds down as it can't
                       // be represented exactly by a float and the
                       // closest representable float is lower
2.449999999999999999.toFixed(1) // Returns '2.5': it rounds up as it less
                       // than NUMBER.EPSILON away from 2.45 and therefore
                       // cannot be distinguished
-2.34.toFixed(1)       // Returns '-2.3': due to operator precedence,
                       // negative number literals don't return a string…
(-2.34).toFixed(1)     // Returns '-2.3'
```