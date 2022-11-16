---
date: 2022-10-20
title: useMemo()
aliases: []
tags:
  - react
  - js
  - memo
  - efficiency
category: 
from: 
---


# When to use useMemo()
## Timing
1. when facing reference type
	1. reference integrity/equality.
	2. But when the data is primitive type ,using useMemo() is way less efficient than not.`Shallow Equal` can handle it fine.
2. when useing array which includes complicated counts and logic.
	1. array can be extended that is the key reason why we should use `useMemo()`.The array(data) getting larger , the more benefit we will get.
```js
const memoizedResult = useMemo(compute, dependencyArray);
```
### Explain
- first params
	- compute
		- functions
		- objects
		- arrays
		- which is reference type or costs a lot to calculating.
	- dependency Array
		- just like useEffect()
		- **Only** when the value in the array changes ,the hook will re-render itself.


```js
import { useMemo } from 'react';

const Parent = () => {

const [color, setColor] = useState("#283148");

// 假設 color 都沒有改變，則確保都回傳相同的物件「參照位置」

const config = useMemo(() => ({ color }), [color]);

return (

[...]

{/* 將 useMemo() Memoized 的回傳值帶入 */}

<MemoColorBlock config={config} />

[...]

);

}
```

