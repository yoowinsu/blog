# 选择器分类
## 1.标签选择器

```
*	      通用元素选择器，匹配页面任何元素（这也就决定了我们很少使用）
#id	    id选择器，匹配特定id的元素
.class	 类选择器，匹配class包含(不是等于)特定类的元素
element	标签选择器
```


## 2.组合选择器

```
E,F	多元素选择器，用,(半角)分隔，同时匹配元素E或元素F
E F	后代选择器，用空格分隔，匹配E元素所有的后代（不只是子元素、子元素向下递归）元素F
E>F	子元素选择器，用>分隔，匹配E元素的所有直接子元素
E+F	直接相邻选择器，匹配E元素之后的相邻的同级元素F
E~F	普通相邻选择器（弟弟选择器），匹配E元素之后的同级元素F（无论直接相邻与否）
.class1.class2	id和class选择器和选择器连写的时候中间没有分隔符，. 和 # 本身充当分隔符的元素
element#id	id和class选择器和选择器连写的时候中间没有分隔符，. 和 # 本身充当分隔符的元素
```

## 3.属性选择器

```
E[attr]	匹配所有具有属性attr的元素，div[id]就能取到所有有id属性的div
E[attr = value]	匹配属性attr值为value的元素，div[id=test],匹配id=test的div
E[attr ~= value]	匹配所有属性attr具有多个空格分隔、其中一个值等于value的元素
E[attr ^= value]	匹配属性attr的值以value开头的元素
E[attr $= value]	匹配属性attr的值以value结尾的元素
E[attr *= value]	匹配属性attr的值包含value的元素
```

## 4.伪类选择器

```
E:first-child	匹配元素E的第一个子元素
E:link	匹配所有未被点击的链接
E:visited	匹配所有已被点击的链接
E:active	匹配鼠标已经其上按下、还没有释放的E元素
E:hover	匹配鼠标悬停其上的E元素
E:focus	匹配获得当前焦点的E元素
E:lang(c)	匹配lang属性等于c的E元素
E:enabled	匹配表单中可用的元素
E:disabled	匹配表单中禁用的元素
E:checked	匹配表单中被选中的radio或checkbox元素
E::selection	匹配用户当前选中的元素
E:root	匹配文档的根元素，对于HTML文档，就是HTML元素
E:nth-child(n)	匹配其父元素的第n个子元素，第一个编号为1
E:nth-last-child(n)	匹配其父元素的倒数第n个子元素，第一个编号为1
E:nth-of-type(n)	与:nth-child()作用类似，但是仅匹配使用同种标签的元素
E:nth-last-of-type(n)	与:nth-last-child() 作用类似，但是仅匹配使用同种标签的元素
E:last-child	匹配父元素的最后一个子元素，等同于:nth-last-child(1)
E:first-of-type	匹配父元素下使用同种标签的第一个子元素，等同于:nth-of-type(1)
E:last-of-type	匹配父元素下使用同种标签的最后一个子元素，等同于:nth-last-of-type(1)
E:only-child	匹配父元素下仅有的一个子元素，等同于:first-child:last-child或 :nth-child(1):nth-last-child(1)
E:only-of-type	匹配父元素下使用同种标签的唯一一个子元素，等同于:first-of-type:last-of-type或 :nth-of-type(1):nth-last-of-type(1)
E:empty	匹配一个不包含任何子元素的元素，文本节点也被看作子元素
E:not(selector)	匹配不符合当前选择器的任何元素
```

## 5.伪元素选择器

```
E::first-line	匹配E元素内容的第一行
E::first-letter	匹配E元素内容的第一个字母
E::before	在E元素之前插入生成的内容
E::after	在E元素之后插入生成的内容
```

# 选择器知识点
## class 和 id 的使用场景?
- id选择器
页面中id选择器只能出现一次。
一般最大曾的容器性的标签使用id选择器。
- class选择器
页面中一个class可以出现多次，同一个标签可以有多个不同的class。
多个元素具有同样的样式可以使用同样的class类名赋予样式，这样可以得到复用。
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
