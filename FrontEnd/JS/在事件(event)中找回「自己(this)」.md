---
tags: JS
---
#JS 
# 在event中找回this
*標籤*： [[js]] [[this]]  [[EventHandler]]  [[冒泡]]
<br/>
當事件被觸發時，==This==就是觸發事件的元素。
也就是 **event.currentTarget** 並不是 **event.Target**
---
### 結論
因為冒泡機制的關係，事件上的傳遞會由**`input`到`label`**
所以 ~**click**~之後的冒泡機制可以看出，
`e.target`是input
`e.currentTarget`是觸發事件的目標，也就是接到泡泡的label
所以 this = INPUT = `e.currentTarget`  
