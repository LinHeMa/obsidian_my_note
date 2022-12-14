---
date: 2022-07-31
title: Adjacent sibling combinator
aliases: []
tags:
  - css
  - css selector
category: 
from: 
---

親代選取器在新手圈算是比較常被忽略的，尤其在目前 CSS3 選取器盛行的時期，這類選取器更加的容易被忽略，但其實這些老選取器還是很好用的啊，當然今天要講的選取器不只一個而是兩個，這兩個選取器剛好一個是 CSS2 一個是 CSS3，兩代選取器相遇，就讓我們看看他們各自有些甚麼樣的能耐吧!

## 『+』號之跟屁蟲選取器

加號選取器通常會被 Amos 稱為跟屁蟲選取器，對! 就像你小時候的妹妹老是跟在你屁股後面一樣，所以當然也許你也可以稱他做妹妹選取器(~~醒醒吧你沒有妹妹~~)，他的語法是 `選取對象A + 選取對象B` ，作用其實很單純，就是選取到`『緊跟在對象 A 同層後方的 B』`，簡單來說就像你看到的那種跟屁蟲妹妹/弟弟一樣，永遠跟在你身後 (~~這是阿飄吧~~)，這個選取器就是選這種緊跟在後面的物件，就像下面的這個例子，

HTML

```html
<h1>金魚系列好棒棒</h1>
<p>段落一的內容...</p>
<p>段落二的內容...</p>
<p>段落三的內容...</p>
```

CSS

```css
h1 + p { color: red; }
```

實作上面這個例子你就可以發現到第一個段落會變成紅色，其他的則沒有任何反應，主要是因為我們的選取器就是要選到 h1 後面的那一個 p，這樣如果是一個內文的頁面的話，我就能夠省下一個 class 來對第一段當作是文章前言來設定了。

其實在早期跟屁蟲選取器曾經被拿來當作『排除第一個項目』的選取用途，像以下這組用法

HTML

```html
<ul>
	<li>暴力網頁入門班</li>
	<li>RWD原來醬子班</li>
	<li>金魚都懂的網頁入門</li>
	<li>金魚都懂的這個網頁怎麼切</li>	
</ul>
```

CSS

```CSS
li + li { border-top: 1px solid red; }
```

[上面這個例子](https://codepen.io/bad_printer/pen/QWLopLr)可以用在最新消息的清單之間產出線條，但是頭尾又不會多出一條線這種情況，因為 Amos 寫的選取器是 `li + li` ，意思就是要選到`緊跟在 li 後面的 li`，因為第一個 li 的前方沒有 li ，所以第一個 li 不會被選取到，後面的每個 li 的前方都有一個 li， 所以都會被選取到。那麼我們如果換個方向來看的話，我們也能用在以下這組例子中

HTML

```HTML
<ul>
	<li>暴力網頁入門班</li>
	<li>RWD原來醬子班</li>
	<li>金魚都懂的網頁入門</li>
	<li>金魚都懂的這個網頁怎麼切</li>	
</ul>
```

CSS

```CSS
li { display: inline-block; }
li + li { border-left: 1px solid #aaa; }
```

[上面這組例子](https://codepen.io/bad_printer/pen/mdboWJW)則是先將清單變成橫向排列，接著在每個項目之間給予一條分隔線，但是又不會在頭尾項目多出一條線。這樣是不是非常的方便阿，~~妹妹選取器~~跟屁蟲選取器真是非常棒的一個選取器呢 (謎: 在你眼中有不好的選取器嗎?)

## 『~』連接號之弟弟妹妹一起來選取

看完了~~妹妹~~跟屁蟲選取器之後，緊接著要介紹的則是『~』連接號選取器，語法是這樣的 `選取對象A ~ 選取對象B`，這個選取器的用途是選取到`『對象 A 同層後方的所有 B』`，看起來是不是跟加號選取器有 87 趴像? 你誤會了，事實是看起來根本一樣啊啊啊! 只有換掉『 + 』改成『 ~ 』啊! 結果是連作用都很像，但有差異的是『 + 』只能選到後面的`那一個`，『 ~ 』是選到`後面整串`的，也就是說『只要是在物件A後面的全部物件B』都會被選到，就像大哥說的話，小弟小妹通通都會跟著喊『大哥是對的』一樣，同樣用一個簡單的例子來看

HTML

```html
<h1>金魚系列好棒棒</h1>
<p>段落一的內容...</p>
<p>段落二的內容...</p>
<p>段落三的內容...</p>
```

CSS

```CSS
h1 ~ p { color: red; }
```

實作上面這段原始碼的話就能發現到，全部的 P 都會變成紅色的，這是因為我的 CSS 選取器設定的就是要選到 h1 後面所有的 p，有趣的地方是這個選取器還能跨過中間亂入的路人，選到後面全部的妹妹(~~夠了!你沒有妹妹~~)，例如以下這段原始碼

HTML

```HTML
<h1>金魚系列好棒棒</h1>
<p>段落一的內容...</p>

<h2>Amos 好帥</h2>
<p>段落二的內容...</p>
<p>段落三的內容...</p>
```

CSS

```css
h1 ~ p { color: red; }
```

實作上面這段原始碼會發現到，不管是段落一還是段落二或是段落三，全部都會變成紅色字，這就是這選取器的厲害之處了，忽略路人的特性，只要是同一層並且在後方，就會被選到，中間不管你加入多少路人進來，只要不是你要選的物件，就會被直接忽略掉了。當大哥的總是要多照顧弟弟妹妹啊，怎麼可以因為有路人的亂入就不管了呢? 各位說對吧!

## 實務應用

上面舉的幾個例子應該算是蠻常用到的了，但也是有其他選取器可以替代啦，照樣容我後面再說，免得模糊焦點了，連接號選取器的部分一般人可能使用到的機會少了一點，但是 Amos 經常會用到他來寫手機選單，並且將兩個選取器一起來應用。由於目前講到的選取器有限，我就簡單舉個互動的例子，我可以利用這個選取器來做到動態換色的區塊，像下方這樣

HML

```html
<a href="#" class="color R">R</a>
<a href="#" class="color G">G</a>
<a href="#" class="color B">B</a>
<div class="color-box"></div>
```

CSS

```css
.color{
	display: inline-block;
	width: 30px;
	height: 30px;

}
.color-box{
	width: 100px;
	height: 100px;
	margin-top: 20px;
	background: #ccc;
}
.R { background-color: red; }
.G { background-color: green; }
.B { background-color: blue; }
.R:hover ~ .color-box{ background-color: red; }
.G:hover ~ .color-box{ background-color: green; }
.B:hover ~ .color-box{ background-color: blue; }
```

當你的滑鼠滑到RGB三個色塊中的任一個之後，下方的大色塊就會變色，這是一個基本觀念，相對的我們就可以利用這樣的基本觀念去設計一些互動的操作了，剩下就讓各位去發揮創意吧。[範例連結](https://codepen.io/bad_printer/pen/vYBPmZz)

以上就是今天的 [金魚都能懂的 CSS 選取器](https://ithelp.ithome.com.tw/users/20112550/ironman/2799) - 親代選取器之妹妹選取器與鞭炮串選取器，如果文中描述有誤歡迎各位前輩不吝指正，各位~~妹妹~~金魚我們明天見～(~~醒醒吧!你沒有妹妹要當你的跟屁蟲，被打!~~)