*標籤*  [[js]] [[event]] [[function]] [[object]]

```
<button id='btn'>Click</button>

let btn = document.getElementById('btn')
btn.addEventListener('click', function(e){ 
		console.log(e); }, false);
```


<br/>[addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

當我們執行一個流程控制函數（*eventListener*），瀏覽器會自動產生==事件元素==可以在 function 參數的位置設定變數（**e**），直接在function中使用。
