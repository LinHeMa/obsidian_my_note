---
date: 2022-07-30
title: Convert number to reversed array of digits
aliases: []
tags:
  - array
  - numbers
  - js
category: 
from: 
---
# Convert number to reversed array of digits
[[array]] [[js]]

Given a random non-negative number, you have to return the digits of this number within an array in reverse order.

## Example(Input => Output):

```
348597 => [7,9,5,8,4,3]
0 => [0]
```

## Test cases
```js

const chai = require("chai");
const assert = chai.assert;
chai.config.truncateThreshold=0;

describe("Basic tests", () => {
  it("Testing for fixed tests", () => {
    assert.deepEqual(digitize(35231),[1,3,2,5,3]);
    assert.deepEqual(digitize(0),[0]);
    assert.deepEqual(digitize(23582357),[7,5,3,2,8,5,3,2]);
    assert.deepEqual(digitize(984764738),[8,3,7,4,6,7,4,8,9]);
    assert.deepEqual(digitize(45762893920),[0,2,9,3,9,8,2,6,7,5,4]);
    assert.deepEqual(digitize(548702838394),[4,9,3,8,3,8,2,0,7,8,4,5]);
  })
})

describe('Random tests', () => {
  let i, x, y;
  
  it('Testing for 37 random tests', () => {
    for (x = i = 1; i <= 37; x = ++i) {
      y = 10 + Math.ceil((9 * Math.pow(1.7, x) - 10) * Math.random());
      let ans = y.toString().split('').reverse().map(Number)
      assert.deepEqual(digitize(y), ans, `Testing for n = ${y}`);
    };
  })
});

```

## my ans
```js
function digitize(n) {

//code here

const numArray = n.toString().split(",");

const answer = [];

console.log(numArray);

for (let i = numArray.length; i > 0; i--) {

answer.push(numArray.splice(i - 1, 1, 0).toString());

}

return answer;

}
```

## Better !
### 1 

```js
function digitize(n) {
  return String(n).split('').map(Number).reverse()
}
```
### 2 
```typescript
function digitize(n) {
  return Array.from(String(n), Number).reverse();
}
```
### 3 
```js
function digitize(n){
  return (n + '').split('').map(Number).reverse();
}
```