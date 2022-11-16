---
date: 2022-07-31
title: Tag selector
aliases: []
tags:
  - tag
  - css
  - cssSelector
category: 
from: 
---
# Tag 元素選取器

Tag 元素選取器是CSS選取器中最基本的選取器之一，先離題解釋一下 Tag 是什麼? 白話文就是 HTML 標籤統稱啦，一般來說我們在溝通時為了文字的精準度，有時候會捨棄中文來溝通，這是因為不同的英文是會可能出現相同的中文翻譯的，像是同樣翻譯成標籤的英文在 HTML中就有 Tag 與 Label 這兩個英文單字了，但這兩個單字卻有很明顯的意義落差，Tag 指的是統稱所有 HTML 標籤，而 Label 則僅是 HTML 中的一個語意標籤罷了，所以為了避免這樣的錯誤發生，所以我們這邊會使用 Tag 或標籤來稱呼這個選取器，請大家不要想成了表單的 label 標籤，講了一堆這樣還是不懂嗎？那...跳過！直接看下面的例子應該更簡單（~~那你講那麼多幹嘛？~~）。

## CSS標籤選取器的設定方式

回到我們的 CSS 選取器來談，Tag 選取器的使用方式很單純，基本上就是你想針對哪個 Tag 設定就直接把它的 Tag name 寫出來就好了，就像下面這樣

```css
h1{
  color: red;
}
p{
  color: gray;
}
```

在上面區塊中，Amos 針對了網頁的主標題 h1 標籤設定了文字色彩為紅色，對 p 段落標籤內的文字則設定了灰色。這表示頁面中 **`所有的 h1 跟 p`** 都會變色(~~怎麼這段描述看起來很像廢話~~)，應用這樣的特性我們在網頁設計的實務中，經常會在 [CSS reset](https://youtu.be/WtjXBIyxhw8) 時利用這種選取器來將網頁瀏覽器中的差異設定到一致的外觀，此外也會在一般網站的內容頁內(像是新聞稿這種詳細內容頁面)，利用此選取器做區域性的標籤設定，避免使用者因為不會處理網頁原始碼而導致畫面出現預期外的視覺狀態。

## 實際範例

上面有提到的[[CSS reset]] 就是用這類選取器設定的，我們可以看看以下這一段出自 [Eric A. and Kathryn S. Meyer.](https://meyerweb.com/eric/tools/css/reset/) 網站的 CSS reset 原始碼

```css
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

在上面的例子中也可以看到另外一種選取器的撰寫方式，就是[使用逗號做選取器的區隔](https://ithelp.ithome.com.tw/articles/10217964)，這部分 Amos 之後會再另外講解。