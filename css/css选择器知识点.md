## class 和 id 的使用场景?
- id选择器
页面中id选择器只能出现一次。
一般最大曾的容器性的标签使用id选择器。
- class选择器
页面中一个class可以出现多次，同一个标签可以有多个不同的class。
多个元素具有同样的样式可以使用同样的class类名赋予样式，这样可以得到复用。
## CSS选择器常见的有几种?
[简书--css选择器](http://www.jianshu.com/p/d080176d8cd0)
## 选择器的优先级是怎样的?对于复杂场景如何计算优先级？
- 就近原则，被选中元素的样式优先级大于元素继承样式的优先级；
- 优先级顺序如下： !important>行内样式>id选择器样式>class选择器样式>标签选择器样式
- 复杂场景下，行内样式、id选择器样式、class选择器样式、标签选择器样式对应的值分别是1000、100、10、1，累计选择机的总和，值越大优先级越高
- 优先级相同的情况下，后面的样式会覆盖掉前面的样式
## a:link, a:hover, a:active, a:visited 的顺序是怎样的？ 为什么？
顺序依次是a:link>>a:visited>>a:hover>>a:active。
理由如下：
1.鼠标经过“未访问链接”同时拥有a:link、a:hover两种属性，考虑到后面会覆盖前面样式，又要显示hover的样式，所以a:hover需要在a:link的后面；

2.鼠标按下“链接”同时拥有a:hover、a:active两种属性，考虑到后面会覆盖前面样式，又要显示active的样式，所以a:active需要在a:hover的后面；
3.鼠标经过“访问过链接”同时拥有a:visited、a:hover两种属性，考虑到后面会覆盖前面样式，又要显示hover的样式，所以a:hover需要在a:visited的后面；
综上，顺序依次是a:link>>a:visited>>a:hover>>a:active

## 以下选择器分别是什么意思?
```
#header{  /* id为header的元素*/
}
.header{  /*class为header的元素*/
}
.header .logo{  /*class为header的元素中class为logo的子元素*/
}
.header.mobile{  /*class中既有header又有logo的元素*/
}
.header p, .header h3{  /*class为header的元素中的p元素以及class为header中的h3元素*/
}
#header .nav>li{  /*id为header的元素中li的class为nav 的子元素*/
}
#header a:hover {  /*id为header的元素中a元素的鼠标经过样式*/
}
#header .logo~p{  /*id为header的元素中class为logo的元素的后面所有同级p元素*/
}
#header input[type="text"]{  /*id为header的元素中input有[type="text"]属性的子元素*/
}
```

- 伪类选择器已经在[简书--css选择器](http://www.jianshu.com/p/d080176d8cd0)中总结了
- div:first-child和div:first-of-type的作用和区别
div:first-child是选中父元素中第一个子元素且该元素必须为div元素才会生效；
div:first-of-type是选中父元素中第一个为div的元素，如果是类名的话，则是选中所有为该类名的所有类型 第一个元素。
 ```
<style>
.item1:first-child{
  color: red;
}
.item1:first-of-type{
  background: blue;
}
</style>
 <div class="ct">
   <p class="item1">aa</p>
   <h3 class="item1">bb</h3>
   <h3 class="item1">ccc</h3>
 </div>
```

1.“aa”显示为红色是因为div的第一个子元素正好为class为item1的元素；

2.“aa”和“bb”背景为蓝色是因为他们类名为item1，且他们都是该类型的第一个元素。