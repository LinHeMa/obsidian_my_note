---
date: 2022-10-21
title: Difference between let and useRef()
aliases: []
tags:
  - 
category: 
from: 
---
  
The two ways of defining, refs are not equivalent.

Consider the first example

```javascript
const CompA = () => {
  let _input;
  return (
    <input ref={el => _input = el} type="text" />
  );
}
```

In this example, whenever, CompA re-renders, as new variable `_input` is created and for instance if you have a useEffect in CompA which is meant to run on initial render and it executes something at an interval using this ref variable it would lead to inconsitencies.
#### Conclusion
- re-render 重新產新變數
- 導致不一致

Now consider second case

```javascript
const CompA = () => {
  const _input = useRef(null);
  return (
    <input ref={_input} type="text" />
  );
}
```

In this case, even though the _input variable is created on each render, `useRef` ensures that it receives the same reference that it receives the first time and not initialise it again. `useRef` is the right way to define refs for `functional Components`. For class components you can use `createRef` or the callback pattern you mention
