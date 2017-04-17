## 块级元素和行内元素分别有哪些？动手测试并列出4条以上的特性区别
[简书-行内元素和块元素](http://www.jianshu.com/p/950697b69b45)
## 什么是 CSS 继承? 哪些属性能继承，哪些不能？
css继承就是子标签继承了上级标签的CSS样式的属性。
- 可继承的属性：font-size，font-style，font-family，font-weight，text-align，text-indent，color，visibility；

- 不可继承的属性：border，padding，margin， width， height， display， background，overflow，opacity

## 如何让块级元素水平居中？如何让行内元素水平居中?
块级元素水平居中：

- margin：0 auto；
- 绝对定位并用负边距居中；

行内元素居中：

- text-align:center；

## 用 CSS 实现一个三角形

[三角形](http://js.jirengu.com/gorihirexo/1/)

## 单行文本溢出加 ...如何实现?
```
E{
  overflow: hidden;  /*超出隐藏*/
  white-space: nowrap;  /*不换行*/
  text-overflow: ellipsis;  /*用“...”表示超出的文本*/
}
```

## px, em, rem 有什么区别
- px是像素，是固定单位
- em是相对于直接父元素单位的大小，em就是倍数，是相对单位
- rem是相对于根元素的大小，rem也是倍数，是相对单位

## 解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?
```
body{
  font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
}
```
- 代码表示设置body字体大小为12px，行高为字体的1.5倍，后面是设置字体以及备选字体，中间用逗号隔开，首选字体为tahoma，没有的话选用arial，以此类推。
- 'Hiragino Sans GB'加引号是因为中间有空格，不加引号的话会被认为是两个字体；
'\5b8b\4f53'加引号是因为需要转义。
- 字体里\5b8b\4f53代表宋体的unicode码。不写成“宋体”是为了防止用户页面解码方式不一致造成乱码。
## text-align: center的作用是什么，作用在什么元素上？能让什么元素水平居中
text-align: center是让行内元素水平居中。一般作用于文本元素或img元素。作用在块元素，会使块元素里的行内子元素水平居中；
作用在行内元素的时候直接水平居中。

## IE 盒模型和W3C盒模型有什么区别?
- IE盒模型：盒模型的width和height的值是border+padding+content的和。在ie6、ie7、ie8在不添加doctype时会是IE盒模型模式。
- w3c盒模型：盒模型的width和height的值是content的值（不包括border和padding）。在Chrome和ie9及以上，以及ie6、ie7、ie8在添加doctype时会是w3c盒模型模式。

## *{ box-sizing: border-box;}的作用是什么？
作用是盒模型采取IE盒模型，设置盒模型的宽度是包括border和padding以及content的宽度。

## line-height: 2和line-height: 200%有什么区别?
line-height: 2和line-height: 200%是有区别的。
两个属性设置给具体的某一个元素时是没有区别的，当父元素设置这两个属性后，其子元素会有不同的表现：
- line-height: 200%；父元素设置这个属性后，其所有子元素的行高都是具体的值，即父元素字体大小的200%。下图可看出子元素的行高都一致。
<img src="/uploads/default/original/2X/e/e17200a3011bfb320ed3725b3a5b8639e406ec55.jpg" width="690" height="360">
- line-height: 2；父元素设置这个属性后，其所有子元素的行高都是自身字体大小的2倍。下图可看出子元素的行高都是不一致的。
<img src="/uploads/default/original/2X/1/18076ddeb9e0c236cc1af551b75dbb9c9445ab18.jpg" width="690" height="448">

## inline-block有什么特性？如何去除缝隙？高度不一样的inline-block元素如何顶端对齐?
- inline-block可以设置宽高以及内外边距，不占据整行位置，宽度有内容撑开。
- 去除缝隙主流有两种方法：
1.去除空格，即去除标签之间的空格和换行；
2.设置font-size:0；
3.其他方法参考[N种方法](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)
- 设置vertical-align: top可以使顶端对齐
## CSS sprite 是什么?
CSS sprite是将许多页面图片放入单个图片中的集合。具有许多页面图片的网页可能需要很长时间才能加载并有多个服务器请求。使用CSS sprite将减少服务器请求的数量并节省带宽。CSS sprite也叫css精灵。

## 让一个元素"看不见"有几种方式？有什么区别?
- display：none;彻底消失（看不见也摸不到），不占据原来位置；
- visibility: hidden;隐藏（看不见但摸得到），占据原来的位置；
- opacity: 0;元素透明度为0，只是不显示，但是元素还在，还占据原来的位置