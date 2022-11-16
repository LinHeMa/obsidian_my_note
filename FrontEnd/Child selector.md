---
date: 2022-07-31
title: Child selector
aliases: []
tags:
  - css
  - cssSelector
category: 
from: 
---
[[Adjacent sibling combinator]]
---
# 子代選取器 - 一個最安全且不會讓你株連九族的選取器

談完了兄弟之間的親代選取器，現在我們來聊聊長幼之間的子代選取器吧，這個選取器的語法長這樣 `選取對象A > 選取對象B` ，作用是選取到「子層」物件，當然很多人會覺得，之前不就講過可以[使用空格來選取到子層內容物件](https://ithelp.ithome.com.tw/articles/10218978)了嗎？怎麼現在又來一個一樣的選取器呢？要混篇幅也不是這樣混的哪！當然不是混篇幅啦，我們看清楚一點，這邊強調的是「子代」，也就是說這個選取器只會選到子代物件，那子子代（也就是孫輩物件）就選不到啦，然而之前使用的空格，是所有的後代都會被選到，不管你在哪一層，只要是後代都會被選到，這樣的話兩者的差異性就很明顯了。換個更加明確一點的說法的話，「>」選取器是「僅選到下一個層」的物件，話不多說，直接來看範例

HTML

```html
<div class="amos">
	<div class="son-of-amos">
		<div class="grandson-of-amos"></div>
	</div>
</div>
```

CSS

```css
div {
	padding: 30px;
	background: #fff;
	border: 5px solid #red;
}
.amos > div {
	background: yellow;
}
```

實作上面的範例之後可以發現，`.son-of-amos`這個區塊的背景色變了，但是其他項目卻沒變，那如果把「>」符號拿掉的話呢？你應該可以看到只要是位於 .amos 區塊內的 div 通通都變色了，這就是「子代」選取器的用途。

## 美好的？還是具風險的？

由於`子代選取器只能選到下一層的物件`，所以換言之就是他非常的依賴 HTML 結構，只要結構有所不同就會導致這個選取器失效，讓人覺得這選取器的彈性不好，但也因為他非常的依賴結構的正確性，所以對於整個撰寫 HTML 的嚴謹度來說是更加的保險的，所以究竟是美好或是有風險就看各位對自己的原始碼的掌控度了。

從前文來思考這選取器或許太依賴結構，但是有時候卻可以依賴這樣的結構來製作網頁的組件，避免出現 CSS 汙染的情況，以目前盛行的前端框架 Angular 來說，就有這樣的開發機制(新手不知道框架是啥的就跳過這段吧XD)。

## CSS汙染

甚麼是 CSS 汙染? 聽起來好不環保喔(在講啥鬼?)，所謂的 CSS 汙染就是你寫的 CSS 選取器選取到目標以外的對象，像是你明明要對 A 物件做設定，可是你的選取器寫法卻連 B 物件一起選取到了，這樣的話你會變成需要特別針對 A 物件或 B 物件另外做一些特殊處理來避免 CSS 設定互相影響，這也導致你的原始碼開始變的冗長且累墜，甚至結構寫得不好的人還可能不只是影響到 B 物件，搞不好連 C、D、E、F 物件都牽扯進來了，這可說是非常的不 OK 啊! 所以在網頁開發過程中，原始碼的掌控與結構的規劃可是非常重要的!

## 實務應用

CSS 子代選取器在實務應用上我們可以把網頁中的物件外觀區分成通用項目以及組件項目，將通用的項目先用沒有太嚴謹的 CSS scope 來設定，接著利用比較嚴謹的 CSS scope 來規劃我們的組件與區域，這個[影片](https://youtu.be/bxnZArACzuU)或許可以當成一個非典型的例子，另外子代選取器也常見用於多層式選單中，例如以下就是一個多層選單的例子

HTML

```html
<nav class="main-nav">
	<ul class="menu">
		<li><a href="#">第一層A</a></li>
		<li>
			<a href="#">第一層B</a>
			<ul class="sub-menu">
				<li><a href="#">第二層B</a></li>
				<li><a href="#">第二層B</a></li>
				<li><a href="#">第二層B</a></li>
			</ul>
		</li>
		<li><a href="#">第一層C</a></li>
		<li>
			<a href="#">第一層D</a>
			<ul class="sub-menu">
				<li><a href="#">第二層D</a></li>
				<li><a href="#">第二層D</a></li>
				<li><a href="#">第二層D</a></li>
			</ul>
		</li>
	</ul>
</nav>
```

CSS

```CSS
@import url("https://fonts.googleapis.com/css?family=Noto+Sans+TC:500&display=swap");
.main-nav{
	background-color: #f00;
}
.main-nav .menu{
	display: flex;
	justify-content: center;
}
.main-nav .menu a{
	font-family: 'Noto Sans TC', sans-serif;
	font-weight: 500;
	text-decoration: none;
	color: #fff;
	display: block;
	padding: 10px 20px;
}
.main-nav .menu > li{
	position: relative;
}
.main-nav .sub-menu{
	position: absolute;
	width: 8em;
	background: #a00;
	display: none;
	top: 100%;
}
.main-nav .menu li:hover > a{
	background-color: #800;
}
.main-nav li:hover > .sub-menu{
	display: block;
}
```

[上面例子](https://codepen.io/bad_printer/pen/oNvOgyz)綜合利用了 CSS 層疊式宣告及子代選取器，`.main-nav .menu > li` 設定了第一層的子選單，`.main-nav .menu a` 設定了所有選單中的超連結外觀，`.main-nav .menu li:hover > a` 設定了當 li 被滑鼠摸到時僅讓下面一層的 a 變色，`.main-nav li:hover > .sub-menu` 設定了當 li 被滑鼠摸到時，僅讓該子層選單顯示而不影響所有子層選單，這一點需要特別說明的是， Amos 僅做兩層選單，但如果你製作的是三層選單的話，`.main-nav li:hover > .sub-menu` 這一個設定的優勢就會大大的顯露出來了，各位可以試著寫看看喔，或者也可以看一下 Amos 的[金魚切版系列](https://ithelp.ithome.com.tw/users/20112550/ironman/2623)，有時候就會不經意寫出這種選取器喔。

以上就是今天的 [金魚都能懂的 CSS 選取器](https://ithelp.ithome.com.tw/users/20112550/ironman/2799) - 子代選取器 - 一個最安全且不會讓你株連九族的選取器，如果文中描述有誤歡迎各位前輩不吝指正，各位金魚我們明天見～