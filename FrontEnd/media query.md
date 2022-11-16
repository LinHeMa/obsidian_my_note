
---
date: 2022-07-31
title: media query
aliases: []
tags:
  -  css
category:  
from: 

---


# Media Query

> 規範直通車：  
> [Media Query](https://www.w3.org/TR/mediaqueries-4/)  
> 規範定義：  
> A _media query_ is a method of testing certain aspects of the user agent or device that the document is being displayed in.  
> A [media query](https://www.w3.org/TR/mediaqueries-4/#media-query) is a logical expression that is either true or false. A media query is true if:  
> the [media type](https://www.w3.org/TR/mediaqueries-4/#media-type) , if specified, matches the media type of the device where the user agent is running, and  
> the [media condition](https://www.w3.org/TR/mediaqueries-4/#media-condition) is true.

![https://ithelp.ithome.com.tw/upload/images/20191012/201118253ldJ9wiQka.png](https://ithelp.ithome.com.tw/upload/images/20191012/201118253ldJ9wiQka.png)

Media Query 是一組邏輯表達式，判斷當前設備是否符合媒體設備條件後再套用樣式，由一個可選可不選的 media type 以及零個至多個的 media feature 所構成，當滿足了以下的條件，Media Query 結果為 `true`，便會套用該樣式，這一組邏輯表達式如同上圖。

-   正確的 media type（當有設定時，舉例來說像是螢幕、影印設備）
-   正確的 media feature 組成的 media condition（像是多少設備解析度、設備螢幕大小）

> A media query consists of a media type and zero or more expressions that check for the conditions of particular media features.

Media Query 有兩種寫法，也就是綠色上圖的意思是：

-   第一種：media type（單個） ＋ media feature（零至多個）。
-   第二種：media feature（單個至多個）組成的 media condition。

## Media Query Modifiers

> A media query may optionally be prefixed by a single media query modifier, which is a single keyword which alters the meaning of the following media query.

Media Query 可以加上單一前綴詞 `not`、`only` 來更改整個邏輯表達式含義：

#### `not`

##### 符合`螢幕` 及同時 `解析度大於 72dpi` 便套用

```css
screen and (min-resolution: 72dpi)
```

加上 `not`

##### 不符合`螢幕` 及同時 `解析度大於 72dpi` 便套用

```css
not screen and (min-resolution: 72dpi)
```

以上面範例來說，原先符合顯示設備為 `螢幕` 以及 `解析度大於 72dpi` 狀態下會套用，不過加上 `not` 後會將整個結果變為 `false`，也就是除了顯示設備為 `螢幕` 以及 `解析度大於 72dpi` 狀態都會套用樣式。

以範例來說，當我們今天要套用某個樣式到除了 `螢幕` 以及同時是 `解析度大於 72dpi` 以外的所有設備，可以這樣設定，這樣 `螢幕` 及同時是 `解析度大於 72dpi` 便不會被套用。

#### `only`

> The concept of [media queries](https://www.w3.org/TR/mediaqueries-4/#media-query) originates from HTML4 [[HTML401]](https://www.w3.org/TR/mediaqueries-4/#biblio-html401) . That specification only defined [media types](https://www.w3.org/TR/mediaqueries-4/#media-type) , but had a forward-compatible syntax that accommodated the addition of future concepts like [media features](https://www.w3.org/TR/mediaqueries-4/#media-feature) : it would consume the characters of a [media query](https://www.w3.org/TR/mediaqueries-4/#media-query) up to the first non-alphanumeric character, and interpret that as a [media type](https://www.w3.org/TR/mediaqueries-4/#media-type) , ignoring the rest. For example, the [media query](https://www.w3.org/TR/mediaqueries-4/#media-query) screen and (color)would be truncated to just [screen](https://www.w3.org/TR/mediaqueries-4/#valdef-media-screen) .

由於部分舊瀏覽器中只支援 media type，今天輸入 `screen and (min-resolution: 72dpi)` 時，舊瀏覽器讀到的是 `screen` 在這樣的情況下會照成非預期的套用，於是 `only` 便出現了，當設定的 `only` 舊瀏覽器會當作沒有這個 media type 而忽略。

```css
only screen and (min-resolution: 72dpi)
```

只有當符合 `screen and (min-resolution: 72dpi)` 才會套用。

![https://ithelp.ithome.com.tw/upload/images/20191013/20111825sCafIIEX63.png](https://ithelp.ithome.com.tw/upload/images/20191013/20111825sCafIIEX63.png)

> only 只能被用在 media type 前，不可以直接加在 media feature 前。

#### 範例：

如下我們針對不同種的情況寫出了不同的範例。  
[example](https://codepen.io/yunru1230/pen/Vwweyza)

```css
@media (min-resolution: 50dpi) and (max-resolution: 600dpi){
  .one{
    color: red;
  }
}
```

當符合 `(min-resolution: 50dpi) and (max-resolution: 600dpi)` 結果便是 `true`。

---

```css
@media all and screen{
  .two{
    color: red;
  }
}
```

有多組 media type 而錯誤不會套用。

---

```css
@media not screen and (max-width: 1000px){
  .three{
    color: red;
  }
}
```

當不符合 `screen and (max-width: 1000px)` 結果便是 `true`