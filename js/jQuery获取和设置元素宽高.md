---
title: jQuery获取和设置元素宽高
categories: JavaScript
tags:
  - JavaScript
  - jQuery
date: 2017-06-06T17:19:23.000Z
---
![](https://unsplash.it/800/400/?image=269)
<!-- more -->
- width()和height()

获取匹配元素集合中的第一个元素的当前计算高度值 或 设置每一个匹配元素的高度值。第一个参数表示设置。(不包括内边距) 

```javascript
$('selector').width();//获取只包括content的宽度
$('selector').width('100px');//设置只包括content的宽度
$('selector').height();//获取只包括content的高度
$('selector').height('100px');//设置只包括content的高度
```

- innerWidth()和innerWidth()

为匹配的元素集合中获取第一个元素的当前计算高度值,包括padding，但是不包括border。第一个参数表示设置。(包括内边距)

```javascript
$('selector').innerWidth();//获取包括内边距的宽度
$('selector').innerWidth('100px');//获取包括内边距的宽度
$('selector').innerHeight();//获取包括内边距的高度
$('selector').innerHeight('100px');//获取包括内边距的高度
```

- outerWidth()和outerHeight()

获取元素集合中第一个元素的当前计算宽度值,包括padding，border和选择性的margin。第一个参数表示设置。(包括边框)

```javascript
$('selector').outerWidth();//获取包括内边距和边框的宽度
$('selector').outerWidth('100px');//获取包括内边距和边框的宽度
$('selector').outerHeight();//获取包括内边距和边框的高度
$('selector').outerHeight('100px');//设置包括内边距和边框的高度
```

- outerWidth()outerHeight()

outerWidth()和outerHeight()的参数省略或者false，padding 和 border会被包含在计算中；如果参数为true，margin也会被包含在计算中 。第一个参数为值，第二个参数为true可以设置包括padding和border以及margin的宽高值(包括外边距)

```javascript
$('selector').outerWidth(true);//获取包括内外边距和边框的宽度
$('selector').outerWidth('100px',true);//设置包括内外边距和边框的宽度
$('selector').outerHeight(true);//获取包括内外边距和边框的高度
$('selector').outerHeight('100px',true);//设置包括内外边距和边框的高度
```
