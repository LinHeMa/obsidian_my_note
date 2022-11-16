---
date: 2022-07-31
title: Class selector
aliases: []
tags:
  - css
  - cssSelector
category: 
from: 
---
## [Class selectors](https://ithelp.ithome.com.tw/articles/10217192)

![[Pasted image 20220731082147.png]]

## class的規則

CSS class 在 HTML 原始碼中的長相就像下方這樣

```html
<div class="amos">文字內容</div>
```

但是一個 HTML 的資料有可能同時間會擁有兩種以上的分類，所以也有可能會長成下面這樣

```html
<div class="amos youtuber handsome">文字內容</div>
```

CSS class 選取器是由一個「.」點作為開頭，後面緊接著則是你想使用的 class 名稱，名稱的開頭有規定的，可使用「中線、底線、Emoji符號」，其他特殊符號一率不可使用，請見 [class名稱可用符號測試表](https://codepen.io/bad_printer/pen/dybgRbp)，在表中需要特別注意的部分，Amos 簡單條列於下讓各位比較容易記憶:

-   可以使用中文 (但由於很容易發生伺服器端編碼問題，所以多數開發者嚴格的禁止使用)
-   可以使用英文
-   可以使用Emoji符號 (但我想你如果用在工作上，前輩可能會把你踢出去)
-   class名稱第一個文字可以是中線
-   class名稱第一個文字可以是底線
-   class名稱有區分大小寫，**大小寫不同則視為不同**
-   除了上述可用的符號外，其他符號都會視為無效的 class 名稱
-   **class 名稱第一個字不能是數字**(非常重要!!!!!!!!!)



```CSS
.login-form { ...略 }
.iLikeBuy { ...略 }
.shopping_car { ...略 }
.-this_class--so__ugly { ...略 }
.? {...略}
```



