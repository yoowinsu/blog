---
title: 面试题总结之CSS篇
categories: CSS
tags:
  - CSS
  - 面试
date: 2017-06-26 20:01:43
---
![](https://unsplash.it/800/400/?image=258)
<!-- more -->
## 一个div，宽度是100px，此时设置padding是20px，添加一个什么css属性可以让div的实际宽度仍然保持在100px，而不是140px？
```css
selector{box-sizing: border-box;}
```

## 清除浮动的方式，提供尽可能多的方案。
[清除浮动全总结](https://github.com/yoowinsu/blog/issues/31)

## 如何让两个div分别以40%和60%的比例排在一行内，提供尽可能多的方案。
```html
<style>
  .wrap{
  margin: 0 auto;
  height: 300px;
  background-color: #ccc;
}
.first{
  background-color: pink;
}
.second{
  background-color: #777;
}
</style>
<body>
  <div class="wrap">
    <div class="first"></div>
    <div class="second"></div>
  </div>
</body>
```

* 方法一：flex
```css
.wrap{
  display: flex;
}
.first{
  flex-grow: 2;
}
.second{
  flex-grow: 3;
}
```

* 方法二：百分比
```css
.first{
  height: 100%;
  float: left;
  width: 40%;
}
.second{
  height: 100%;
  float: left;
  width: 60%;
}
```

* 方法三：左列定位，右列浮动+margin
```css
.wrap{
  position: relative;
}
.first{
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  width: 40%;
}
.second{
  height: 100%;
  float: left;
  width: 60%;
  margin-left: 40%;
}
```

## 如何用css实现一个div的一秒内向右平滑移动100px的动画 .
[预览链接](https://yoowinsu.github.io/demos/just-demos/css3%E5%8A%A8%E7%94%BB.html)
```css
selector{
	width: 100px;
	height: 100px;
	background-color: #000;
	position: relative;
}
selector:hover{
	animation: loops 1s linear forwards;
}
@keyframes loops{
	0%{
	left: 0;
	}
	100%{
	left: 100px;
	}
}
```

## 左右布局：左边定宽、右边自适应，不少于3种方法
```html
<style>
  .wrap{
  margin: 0 auto;
  height: 300px;
  background-color: #ccc;
}
.first{
  background-color: pink;
  width: 100px;
}
.second{
  background-color: #777;
}
</style>
<body>
  <div class="wrap">
    <div class="first"></div>
    <div class="second"></div>
  </div>
</body>
```
方法一：左列浮动
```css
.first{
  float: left;
  height: 100%;
}
.second{
  width: 100%;
  height: 100%;
  padding-left: 100px;
}
```
方法二：flex布局
```css
.wrap{
  display: flex;
}
.first{
  height: 100%;
}
.second{
  flex-grow: 1;
  height: 100%;
}
```
方法三：左列定位
```css
.wrap{
  position: relative;
}
.first{
  position: absolute;
  height: 100%;
}
.second{
  height: 100%;
  width: 100%;
  padding-left: 100px;
}
```
方法四：左右都定位，左侧层级更高
```css
.wrap{
  position: relative;
}
.first{
  position: absolute;
  height: 100%;
  z-index: 1;
}
.second{
  position: absolute;
  height: 100%;
  width: 100%;
  padding-left: 100px;
}
```
## CSS3用过哪些新特性
CSS3新特性：
1. 圆角， 圆形
2. div 阴影
3. 2D 转换：放大、缩小、偏移、旋转
4. 3D 转换：移动、旋转
5. 背景色渐变
6. 过渡效果
7. 动画

## BFC、IFC
[IFC、BFC、GFC 与 FFC](https://github.com/chokcoco/iCSS/issues/5)
## 对栅格的理解
全局采用IE盒模型
每个容器分为行（row）和列（column）组成，容器可以嵌套容器，所有列都左浮动，按照百分比做多可以分为12列，每一行撑满了会自动换行

## （水平）居中有哪些实现方式
**块级元素水平居中：**

margin：0 auto；
绝对定位并用负边距居中；
**行内元素居中：**

text-align:center；
## （垂直）居中有哪些实现方式
[垂直居中几种方法](https://yoowinsu.github.io/2017/04/02/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E6%B3%95/)

## 水平垂直居中有哪些方式？
```css
/*水平垂直居中一*/
/*确定容器的宽高 宽500 高 300 的层*/
/*设置层的外边距*/

 div {
 	position: relative;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	margin: -150px 0 0 -250px;     	/* 外边距为自身宽高的一半 */
 	background-color: pink;	 	/* 方便看效果 */
  }

/*水平垂直居中二*/
/*未知容器的宽高，利用 `transform` 属性*/
 div {
 	position: absolute;		/* 相对定位或绝对定位均可 */
 	top: 50%;
 	left: 50%;
 	transform: translate(-50%, -50%);
 	background-color: pink;	 	/* 方便看效果 */

 }

/*水平垂直居中三*/
/* 利用 flex 布局*/
/* 实际使用时应考虑兼容性*/
 .container {
 	display: flex;
 	align-items: center; 		/* 垂直居中 */
 	justify-content: center;	/* 水平居中 */

 }
 .container div {
 	width: 100px;
 	height: 100px;
 	background-color: pink;		/* 方便看效果 */
 }  
```

## 1像素边框问题
造成原因：在 Retina 屏下，设置 1px 边框，实际显示 2px，是因为部分移动设备中devicePixelRatio属性不为1，如苹果5s为2，CSS设置的1px实际上是物理像素，也就是设备屏幕的1px，devicePixelRatio为2的设备的屏幕会显示为2px，devicePixelRatio为3的设备的屏幕会显示为3px

解决办法：viewport + rem
动态加载页面的viewport，如devicePixelRatio = 2 时，动态输出viewport：
```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5">
```

## 描述css reset和normalize.css，并说一下他们的不同之处？
Normalize 相对「平和」，注重通用的方案，重置掉该重置的样式，保留有用的 user agent 样式，同时进行一些 bug 的修复，这点是 reset 所缺乏的。

Reset 相对「暴力」，不管你有没有用，统统重置成一样的效果，且影响的范围很大，讲求跨浏览器的一致性。


## css实现空心三角箭头
[blog](https://yoowinsu.github.io/2017/05/01/CSS%E5%AE%9E%E7%8E%B0%E4%B8%89%E8%A7%92%E6%8C%87%E7%A4%BA%E7%AE%AD%E5%A4%B4/)

## 单行文本溢出加 …如何实现?
```css
E{
  overflow: hidden;  /*超出隐藏*/
  white-space: nowrap;  /*不换行*/
  text-overflow: ellipsis;  /*用“...”表示超出的文本*/
}
```


## 什么是 CSS 继承? 哪些属性能继承，哪些不能？
css继承就是子标签继承了上级标签的CSS样式的属性。

可继承的属性：font-size，font-style，font-family，font-weight，text-align，text-indent，color，visibility；
不可继承的属性：border，padding，margin， width， height， display， background，overflow，opacity

## px, em, rem 有什么区别
px是像素，是固定单位
em是相对于直接父元素单位的大小，em就是倍数，是相对单位
rem是相对于根元素的大小，rem也是倍数，是相对单位

## 解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?
```css
body{
  font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
}
```
代码表示设置body字体大小为12px，行高为字体的1.5倍，后面是设置字体以及备选字体，中间用逗号隔开，首选字体为tahoma，没有的话选用arial，以此类推。
‘Hiragino Sans GB’加引号是因为中间有空格，不加引号的话会被认为是两个字体； ‘\5b8b\4f53’加引号是因为需要转义。
字体里\5b8b\4f53代表宋体的unicode码。不写成”宋体”是为了防止用户页面解码方式不一致造成乱码。
text-align: center的作用是什么，作用在什么元素上？能让什么元素水平居中
text-align: center是让行内元素水平居中。一般作用于文本元素或img元素。作用在块元素，会使块元素里的行内子元素水平居中； 作用在行内元素的时候直接水平居中。


## IE 盒模型和W3C盒模型有什么区别?
IE盒模型：盒模型的width和height的值是border+padding+content的和。在ie6、ie7、ie8在不添加doctype时会是IE盒模型模式。
w3c盒模型：盒模型的width和height的值是content的值（不包括border和padding）。在Chrome和ie9及以上，以及ie6、ie7、ie8在添加doctype时会是w3c盒模型模式。


## inline-block有什么特性？如何去除缝隙？高度不一样的inline-block元素如何顶端对齐?
inline-block可以设置宽高以及内外边距，不占据整行位置，宽度有内容撑开。
去除缝隙主流有两种方法： 1.去除空格，即去除标签之间的空格和换行； 2.设置font-size:0； 3.其他方法参考N种方法

设置vertical-align: top可以使顶端对齐


## CSS sprite 是什么?
CSS sprite是将许多页面图片放入单个图片中的集合。具有许多页面图片的网页可能需要很长时间才能加载并有多个服务器请求。使用CSS sprite将减少服务器请求的数量并节省带宽。CSS sprite也叫css精灵。


## 让一个元素”看不见”有几种方式？有什么区别?
display：none;彻底消失（看不见也摸不到），不占据原来位置；
visibility: hidden;隐藏（看不见但摸得到），占据原来的位置；
opacity: 0;元素透明度为0，只是不显示，但是元素还在，还占据原来的位置


## CSS3新增伪类有那些？
     p:first-of-type	选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
  	p:last-of-type	选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
      p:only-of-type	选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
  	p:only-child		选择属于其父元素的唯一子元素的每个 <p> 元素。
  	p:nth-child(2)	选择属于其父元素的第二个子元素的每个 <p> 元素。

  	:after			在元素之前添加内容,也可以用来做清除浮动。
  	:before			在元素之后添加内容
      :enabled  		
  	:disabled 		控制表单控件的禁用状态。
  	:checked        单选框或复选框被选中。

## display有哪些值？说明他们的作用。

    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	缺省值。象行内元素类型一样显示。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。

## position的值relative和absolute定位原点是？

    absolute
  	生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
    fixed （老IE不支持）
  	生成绝对定位的元素，相对于浏览器窗口进行定位。
    relative
  	生成相对定位的元素，相对于其正常位置进行定位。

## CSS3有哪些新特性？

    新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
    圆角		    （border-radius:8px）
    多列布局	    （multi-column layout）
    阴影和反射	（Shadow\Reflect）
    文字特效		（text-shadow、）
    文字渲染		（Text-decoration）
    线性渐变		（gradient）
    旋转		 	（transform）
    缩放,定位,倾斜,动画,多背景
    例如:transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:

## 如何自定义滚动条？
```css
selector::-webkit-scrollbar {
    width: 4px; /*垂直方向滚动条宽度*/
    height: 4px; /*水平方向滚动条高度*/
}
/*滚动条轨道*/
selector::-webkit-scrollbar-track {
    background-color: pink;
} 
/*滑块*/
selector::-webkit-scrollbar-thumb {
    background-color: red;
}
```

## css3 实现一个幻灯片
[预览效果](https://yoowinsu.github.io/demos/just-demos/CSS%E5%AE%9E%E7%8E%B0%E8%BD%AE%E6%92%AD.html)
```html
<head>
    <style type="text/css">
      .box{
            width: 800px;
            height: 400px;
            margin: 0 auto;
            animation: loops 10s infinite;
         }
         @keyframes loops {
            0% {
                background:url(https://unsplash.it/800/400?image=11) no-repeat;             
            }
            25% {
                background:url(https://unsplash.it/800/400?image=12) no-repeat;
            }
            50% {
                background:url(https://unsplash.it/800/400?image=13) no-repeat;
            }
            75% {
                background:url(https://unsplash.it/800/400?image=14) no-repeat;
            }
            100% {
                background:url(https://unsplash.it/800/400?image=15) no-repeat;
            }
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
```

## rgba()和opacity的透明效果有什么不同？

rgba()和opacity都能实现透明效果，但opacity作用于元素和所有子元素的透明度，而rgba()只作用于元素自身的颜色和透明度（即子元素不继承透明度）

## css中可以让文字在垂直和水平方向上重叠的两个属性是什么？
垂直方向：line-height
水平方向：letter-spacing（字间距）

## letter-spacing可以消除inline-block元素间的换行符空格间隙

## <img>怎样垂直居中？
```css
/*img父元素*/
selector{
  vertical-align: middle;
  display: table-cell;
}
```
## 多列等高布局

规定下面的布局，实现多列等高布局。
```html
<div id="container">
    <div class="left">多列等高布局左</div> 
    <div class="right">多列等高布局右</div>
</div>
```
多列等高布局，算是比较常见的一种布局，要求两列布局看上去高度一致（就是通常是两列背景色一致）。

如果只是两列背景颜色高度一致，有很多方法可以实现。

法一、使用 display:flex 的方式实现

法二、使用正负 margin 与 padding 相冲的方式实现

法三、父容器设置背景色实现

法四、父容器多重背景色--线性渐变

法五、display:table-cell 实现

## ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。

  单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。（伪元素由双冒号和伪元素名称组成）
  双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，
  比如:first-line、:first-letter、:before、:after等，
  而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。

  想让插入的内容出现在其它内容前，使用::before，否者，使用::after；
  在代码顺序上，::after生成的内容也比::before生成的内容靠后。
  如果按堆栈视角，::after生成的内容会在::before生成的内容之上

## CSS 斜线的实现
方法一：旋转
```css
selector{
  height: 1px;
  background: #222;
  width: 80px;
  transform:rotateZ(45deg) scale(1.414);
}
```
方法二：三角形
```css
selector{
  position: relative;
  width: 0;
  height: 0;
  border: 50px solid transparent;
  border-bottom-color: orange;
  border-left-color: orange;
}


selector::before{
  content:"";
  position:absolute;
  left: -50px;
  top: -48px;
  border: 49px solid transparent;
  border-bottom-color: #000;
  border-left-color: #000;
}
```
方法三：clip-path
css3新属性
```css
selector{
    position: relative;
    width: 100px;
    height: 100px;
    -webkit-clip-path: polygon(0 0, 0 100px, 100px 100px, 0 0);
    background: deeppink;
}

selector::before{
  content:"";
  position:absolute;
  left: 0;
  top: 1px;
  border: 49.5px solid transparent;
  border-bottom-color: #000;
  border-left-color: #000;
}
```
方法四：线性渐变
```css
selector{
  width: 100px;
  height: 100px;
  background: linear-gradient(45deg, transparent 49.5%, deeppink 49.5%, deeppink 50.5%, transparent 50.5%); 
}
```