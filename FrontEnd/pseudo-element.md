---
date: 2022-07-31
title: pseudo-element
aliases: []
tags:
  - css 
  - pseudo-element
  - cssSelector
category: 
from: 
---
[[Pseudo-class selector]]
# ::before & ::after
學過了[偽類選取器](https://ithelp.ithome.com.tw/articles/10221625)之後，讓我們在鐵人賽中插播一個很重要的 CSS 選取器，那就是 CSS 偽元素 (pseudo-element)，簡單的來說就是假的元素，再簡化一點就是假貨啦! 這個假貨是真真實實的，我們完全不用假一賠三，還愛他愛的要死呢! 而為什麼要這麼臨時的要在鐵人賽的偽類選取器 ( pseudo-class ) 話題中插播進來這個選取器呢? 實在是因為這個選取器實在太好用~ 太常用~ 太方便啦~~~ 所以插播進來之後，

偽元素 (pseudo-element) 的語法是 `物件::before` 或 `物件::after` ，從字面上面就可以猜想的出來，一個偽元素是在前面 ( before )，一個偽元素是在後面 ( after ) ，讓我們直接來看看吧

HTML

```html
<div>我是內容文字</div>
```

CSS

```CSS
div{
    padding: 10px;
    background: gray;
}
div::before{
	content: '我是before';
	color: red;
}
div::after{
	content: '我是after';
	color: green;
}
```

上面原始碼會實際出現的畫面會像下面這樣  
![https://ithelp.ithome.com.tw/upload/images/20190929/20112550Ju15AhZM0v.png](https://ithelp.ithome.com.tw/upload/images/20190929/20112550Ju15AhZM0v.png)

畫面可以看到 ::before 會在物件內容的前方加入資料，而 ::after 會在物件內容的後方加入資料，但需要特別注意到的是偽元素常見的用法會是跟在物件後方，也就是採用[CSS 組合式宣告](https://ithelp.ithome.com.tw/articles/10218497)方式，使用這種方式的話，我們可以精確的控制我們的偽元素要在哪個物件內產生，如果物件與 ::before 之間使用了空白的話，就變成了 [CSS 層疊式宣告](https://ithelp.ithome.com.tw/articles/10218978) ，這樣的話會變成後代選取器了，那個意思可是天差地遠的喔(新手太常發生這問題了，我倒)。

另外細心一點的話各位應該也會發現我們屬性中出現的 `content` 這個屬性，這屬性跟 ::before/::after 可說是形影不離，兩者只要缺少任何一方，就活不下去了( 簡直比瓊瑤小說更瓊瑤哪! )

## 沒了會死，有了更精彩

在 ::before / ::after 這兩個選取器中，少了 content 這個屬性的話，整個偽元素就會消失不見，完全不會出現，但有了 content 之後， ::before / ::after 就會存在網頁中，各位可以將剛剛的原始碼網頁用 Chrome打開之後，在你的 Chrome 中使用滑鼠右鍵並點擊「檢查」，就可在開發者工具中看到以下這種畫面。  
![https://ithelp.ithome.com.tw/upload/images/20190929/20112550PDUDyCISTd.jpg](https://ithelp.ithome.com.tw/upload/images/20190929/20112550PDUDyCISTd.jpg)

圖中黃色框框就是經由瀏覽器所產出的假貨 ( ::before / ::after )，偽元素需要經過瀏覽器的運算跟渲染之後才會出現，所以如果各位剛剛不是點擊「檢查」而是點擊「檢視網頁原始碼」的話，由於「檢視網頁原始碼」是將未經過運算的原始碼直接呈現出來，也就是說他就「完全等同於你撰寫的原始碼」，此時你就看不到 ::before / ::after 的區塊囉。

## 有哪些貨，通通給我拿出來

既然知道可以利用 content 來產出內容在頁面中，那麼在 `content` 屬性中可以使用的值有幾種就很重要了，以下幾種是規範中有的:

1.  none
2.  normal
3.  string
4.  url
5.  counter
6.  attr
7.  open-quote
8.  close-quote
9.  no-open-quote
10.  no-close-quote

針對其中比較常用到專案的項目我們簡單的來看看，Amos 本身比較常用到的有

1.  string
2.  counter
3.  attr

### string

string應該就不用特別介紹了，意思就是字串啦，正如同我們一開始使用的範例原始碼，就是利用單引號或雙引號將一段文字包起來，這樣就可以出現在畫面上了，這用法大概有 100% 的機會用在專案之中，例如這次鐵人賽挑戰的另外一個主題 [金魚都能懂的網頁切版 : 人員介紹卡片](https://ithelp.ithome.com.tw/articles/10217278) 就有用到這個選取器喔，還有像是 [金魚都能懂的網頁切版 : 破格式設計](https://youtu.be/l-sQNXNrw3s) 也使用到了這個選取器去做一些裝飾性的區域，更重要的是...歡迎各位訂閱[金魚都能懂的這個網頁畫面怎麼切](https://ithelp.ithome.com.tw/users/20112550/ironman/2623) 系列影片啦。

### counter

counter 的用法比較特別一點，counter 可以讓我們使用 CSS 來指定計數數值，並且也可以讓你指定你要增加的數值以及起始的數值，例如我今天有一分不是使用標準 li 標籤建立的清單

HTML

```html
<div class="amos-list">
  <div class="amos-list-item">list</div>
  <div class="amos-list-item">list</div>
  <div class="amos-list-item">list</div>
  <div class="amos-list-item">list</div>
  <div class="amos-list-item">list</div>
  <div class="amos-list-item">list</div>
</div>
```

接著我們想要對這份清單內容建立數字，那我們可以使用以下 CSS 來建立

CSS

```CSS
.amos-list{
  counter-reset: my-area 7;
}
.amos-list-item::before{
  content: counter(my-area) '. ';
  counter-increment: my-area 1; 
}
```

這邊在 ::before 的位置使用了兩個屬性來建立我們所需要的計數，一個是 `content: counter(自訂要建立計數的區域名稱)` ，另一個則是 `counter-increment: 自訂要建立計數的區域名稱 欲遞增的數` ，接著在父層設定 `counter-reset: 自訂要建立計數的區域名稱 起始數` ，這樣就能讓我們快樂隨意的自訂要起始的數值了，這方式對於一些特殊的計數需求可真是超級棒的阿! (灑花)。

### attr

attr 是屬性 ( Attributes ) 的縮寫，這個值可以讓我們指定我們`想要取得的HTML屬性的值` ，這說法聽起來繞舌，一樣用原始碼來看看

HTML

```html
<a href="https://csscoke.com" target="_blank" data-note="此連結另開視窗">
	CSS coke
</a>
```

CSS

```css
a::after{
	content: attr(data-note);
	color: #aaa;
}
```

在這段原始碼中， Amos 利用了 `attr(data-note)` 來取得 HTML 中 data-note 這個自訂屬性的值，並將它顯示在我的畫面上，設定顯示為淺灰色，這樣有沒有覺得 CSS 有點程式的樣子了，雖然他目前被稱為樣式，但程式具備的一些特性在 CSS 中有越來越多影子出現了呢! 真是太棒了! 這樣以後~~就要學到更多東西了~~就可以有更多自由運用的方式了。

## 你這個中看不中用的XX

哇! 這標題下的可真重! 這也太灑狗血了吧! 這標題指的是 url 這個值，為何說他重看不中用呢? url 這個值可以讓我們指定圖片的路徑，讓你的 ::before / ::after 直接顯示圖片出來，就像是 img 標籤一樣，而且很棒的是這樣顯示出來的圖片是可以被印表機列印出來的(詳見 [使用::before 與 ::after來製作可列印的logo圖片](http://csscoke.com/2013/09/22/%E4%BD%BF%E7%94%A8before-%E8%88%87-after%E4%BE%86%E8%A3%BD%E4%BD%9C%E5%8F%AF%E5%88%97%E5%8D%B0%E7%9A%84logo%E5%9C%96%E7%89%87/)，這看起來真是超級美好的說~ 這大大解決了我們使用背景圖片無法被列印出來的問題，就使用 ::before / ::after 來解決就好啦! But ! 就是這個 But ! 使用 url(...) 抓出來的圖片無法用 CSS 的 width 與 height 控制其寬高，這可是很大的問題啊!!! 至今 Amos 尚未找到完美的解法，像是 scale 這種解法是有瑕疵的，如果您有不錯的方式願意跟 Amos 分享的話，Amos 一定請你吃一頓大餐(笑)

## 特別注意事項

因為 ::before / ::after 本身是偽元素，你可以將其視為一個不存在實體的物件，雖然他會占空間但也只是佔一個偽元素的項目而已，為了你的網站的 SEO 著想，建議您只將偽元素使用在`裝飾性`的物件上，千萬別使用於應該有具體意義的文字項目中，這樣才是一個正確的使用觀念喔

# ::selection 選取狀態僞元素

前一天看完了常見的 [::before 與 ::after 僞元素](https://ithelp.ithome.com.tw/articles/10222534)之後，我們繼續來看看另外一個少見的僞元素選取器 `::selection`，這個僞元素特別之處如同該字面上的意思就是`選取的狀態`，在早期的網頁當使用者選取到一段文字的時候，那個反白色彩都是由瀏覽器自行決定的，所以有時候就會出現反白色彩背景與文字對比不足導致閱讀困難的情況，但現在我們總算可以利用這個選取器來自訂我們的配色了，這樣讓視覺設計師可以有更多的~~工作負擔~~設計發揮了，真的是視覺設計師的好武器啊！

## 設定的彈性

`::selection` 選取器作為一個選取狀態的選取器，在這種將文字反白的狀況可想而知的是屬性變化應該不會支援太多才對，但其實算起來還不少，總共有以下八種之多呢

-   color (文字色彩)
-   background-color （背景色彩）
-   cursor （滑鼠游標）
-   caret-color （閃動標點）
-   outline （外框線）
-   text-decoration （文字裝飾）
-   text-emphasis-color （文字加重強調符號色彩）
-   text-shadow （文字陰影）

說到這大家應該還是無感這個狀態會是怎樣的視覺效果，不多說直接進原始碼伺候

HTML

```CSS
<p>我沒有設定選與效果，色彩由瀏覽器內定</p>
<p class="BG-gray-T-red">我選取狀態下色彩由我決定，背景變灰，文字變紅</p>
```

CSS

```css
.BG-gray-T-red::selection{
	color: red;
	background-color: gray;
}
```

上面例子中當使用者使用滑鼠反白選取文字時第一個段落會是瀏覽器預設的外觀，而第二個段落則會是呈現由我所設定的灰底紅字，這樣應該非常清楚 ::selection 的作用了吧！

## 那些不常用到的值

### caret-color

這個值其實有點冷門，一般人算是比較少會去設定的，這是用來設定插入點的那個閃動光標色彩的，就那個一閃一閃亮雞精的豎線啊。不多說上原始碼來看

```html
<input type="text" name="" id="">
```

CSS

```css
input{
  caret-color: #fa0;
}
input::selection{
  color: #fa0;
}
```

上面的例子當使用者點擊了表單文字欄位時，就能夠看到閃動的豎線標點（插入點）的色彩變成了 Amos 所設定的橙色了，所以意思就是我們可以設定我們選取文字之後的插入點色彩，是不是很有趣啊。

### Text-emphasis-color

text-emphasis-color 這個屬性是設定強調文字符號的色彩，但是當我們沒有設定強調文字的時候，基本上也無效啊，所以我們需要多學一個 `text-emphasis`屬性，這個屬性可以設定「加重強調符號」的樣式，兩者一合併之後就會像是下面這個樣子了

HTML

```html
<p>Amos 所撰寫與錄製的<span>金魚都能懂的 CSS 選取器</span>真是太棒了！這樣的好文應該用力給它訂閱下去啊，林貢丟無丟啊！！！</p>
```

CSS

```css
span{
  -webkit-text-emphasis:'坑';
  text-emphasis: '坑';
}
span::selection{
  -webkit-text-emphasis-color: red;
  background-color: #ffa;
}
```

上面例子當你選取到 span 內的文字的時候，你會發現文字上方的坑字加重符號改變色彩為我設定的紅色了。

## 實際應用

老實說這個選取器多數的設計師應該都不太會去在意，但的確有少數的設計師會對設計吹毛求疵到這些小細節都注意到，事實上 Amos 在多年前就想設定這個屬性了，但當時尚未有這屬性可使用，一切都只能飲恨敲碗捶心肝，現在有了這選取器之後，我想...我用到的機會還是不多啦，但至少知道這選取器之後也可以備而不用，等哪天有需要時，就可以直接用上啦，Amos 還遇到不少這一類備了很久卻沒啥機會的用上的屬性在某些特殊時刻解了我難以克服的狀況。基本上各位願意看到這段話的話，我想多少腦袋裡面都有一個印象了，沒關係，忘記時再回來看看吧。