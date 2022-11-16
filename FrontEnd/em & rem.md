---
date: 2022-07-31
title: em & rem
aliases: []
tags:
  - css
  - size
category: 
from: 
---
大多數網站在文字的單位都是使用px，尤其在台灣多數使用者都是用windows系統，不管是什麼瀏覽器，在windows下都是以單數px是較為清楚的，如13xp．15px等，而px在建立網站時也是較為方便及準確的，但他的彈性是比較差的。而現在不管是文字及尺寸上都有了新單位可以運用。![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271143385244feea0132e_resize.png)  
本篇CSS效果發表於[http://ashareaday.wcc.tw/#2013-09-27](http://ashareaday.wcc.tw/#2013-09-27) (建議使用Chrome瀏覽器)  
# CSS3 新的文字單位  
大多數網站在文字的單位都是使用px，尤其在台灣多數使用者都是用windows系統，不管是什麼瀏覽器，在windows下都是以單數px是較為清楚的，如13xp．15px等，而px在建立網站時也是較為方便及準確的，但他的彈性是比較差的。![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144055244ff055bfd0_resize.png)  
彈性差的部分就來做一個實驗，就是將他們的外層在增加一個放大的文字屬性。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144075244ff07c2ce4_resize.png)

## **EM**  
而用另一個文字單位em，em隨著外圍的文字大小調整，當然這是他的優點，也是他的缺點。  
本站預設為13px。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144115244ff0b1e5db_resize.png)  

我們可以調整外圍的font-size，就可以影響到內部的文字大小，但是要注意，如果外層也有設定em他也會繼承下去。  

![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144135244ff0dcee32_resize.png)  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144165244ff1016c72_resize.png)  
由上面的範例可得知，一不小心還是會失控的。

## **REM**  
rem是新的文字單位，他和em用法類似，但是他不會繼承，只會受最根部的單位影響，html的font-size(優點是ie需要9以上才支援)。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144235244ff17e4120_resize.png)

```html
html
	font-size: 13px
.f2rem
	font-size: 1.2rem
.f3rem
	font-size: 1.3rem
.f4rem
	font-size: 1.4rem	
```

注意在使用時，它只會受html的font-size影響，body以下的都不會影響。

# **CSS3 新的尺寸單位**  
不久前我有一個問題，就是在自適應的情況下，正方形的CSS語法該如何寫。直接寫px然後配合media query似乎是一個辦法，但如果我的水平都要保持三個等"百分比"的正方形，似乎就不太可能了。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144295244ff1d0f508_resize.png)  
## **vh vw**  
vh vm是CSS3新單位，是指裝置的畫面高度及畫面的寬度百分比。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144265244ff1a2f9a1_resize.png)

```html
.vw
	width: 10vw
	height: 10vw
	margin: 0 8px	
```

這個部分我就單只用vw做範例，建議大家也可以調整瀏覽器大小並重新整理看看，下方是比較小畫面的螢幕截圖，這時的正方形其實和上方的100px大小差不多。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144365244ff24da16e_resize.png)  
這時我把視窗拉滿了16:9的寬度，正方形明顯大很多。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144405244ff281b194_resize.png)  
我又繼續拉滿兩個16:9的螢幕，正方形已經突破天際了。  
![](http://ithelp.ithome.com.tw/upload/images/20130927/201309271144435244ff2b1bcd9_resize.png)

## **vmin**  
除此之外，還有一個單位稱為`vmin`，是裝置中寬度or高度較小的那個值，如果使用者裝置轉來轉去就很有效果!?  
以上是不錯的新單位，但在目前還有許多瀏覽器不支援(android內建browser不支援)，使用前請先注意，