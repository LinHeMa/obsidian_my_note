---
date: 2022-10-20
title: useCallback()
aliases: []
tags:
  - react
  - js
  - efficiency
  - render
  - callback
category: 
from: 
---
# Timing
#### when dealing with functions

```js
const memoizedCallback = useCallback(callback, [dependencyArray]);
```

# What is the difference between useMemo() and useCallback() when passing fn ?
### [[useMemo()]]

```js
const compute = useMemo(function(),[dependencyArray])

```
will excute the `function()` and return the `value`

#### [[useCallback()]]

```js
const compute = useCallback(function() ,[dependencyArray])
```
will directlly return the `function()`


