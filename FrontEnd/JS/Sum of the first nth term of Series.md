---
date: 2022-07-24
aliases(別名): []
tags: JS
---
# Metadata
status :: first<br>
Note Type :: <br>
Topics :: {}
(使用`[Topic],[Topic]`格式)[[js]][[array]][[algorithm]][[math]]
#JS
## Task:

Your task is to write a function which returns the sum of following series upto nth term(parameter).

```
Series: 1 + 1/4 + 1/7 + 1/10 + 1/13 + 1/16 +...
```

## Rules:

-   You need to round the answer to 2 decimal places and return it as String.
    
-   If the given value is 0 then it should return 0.00
    
-   You will only be given Natural Numbers as arguments.
    

## Examples:(Input --> Output)

```
1 --> 1 --> "1.00"
2 --> 1 + 1/4 --> "1.25"
5 --> 1 + 1/4 + 1/7 + 1/10 + 1/13 --> "1.57"
```

---
## ANS

```
function SeriesSum(n) {
  for (var s = 0, i = 0; i < n; i++) {
    s += 1 / (1 + i * 3)
  }
  
  return s.toFixed(2)
}
```

### 註記
-  不需要用到`reduce`  也可以達到`reduce`的效果
- 不要把問題複雜化