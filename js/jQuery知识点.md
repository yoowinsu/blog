---
title: jQuery知识点
categories: JavaScript
tags:
  - JavaScript
  - jQuery
date: 2017-05-26T19:09:45.000Z
---
![](https://unsplash.it/800/400/?image=270)
<!-- more -->
# jQuery 中， $(document).ready()是什么意思？

$(document).ready方法接受一个函数作为参数，将该参数作为document对象的DOMContentLoaded事件的回调函数。也就是说，当页面解析完成（即下载完标签）以后，在所有外部资源（图片、脚本等）完成加载之前，该函数就会立刻运行。

# 库和框架的区别

- 类库 解决的是代码或者是模块级别的复用或者对复杂度的封装问题，例如将一个解决复杂问题的功能模块封装成一个函数，提供一个简单的接口。库它是一种工具，它提供了很多封装好的方法，用与不用取决于我们自身，即使用了也不会影响我们呢的代码结构。

- 框架 更多的是对模式级别的复用和对程序组织的规范。这里的模式是指比如MVC，为了实现M和V的解耦，把复杂的耦合关系由经常变化的业务代码转移到不经常变化的框架内部消化。是面向一个领域来提供一套解决方案，提高开发效率，如果我们选择了使用某框架，就应该遵循该框架所规定的规则。

# jquery 能做什么？

jQuery的最大优势有两个。首先，它基本是一个DOM操作工具，可以使操作DOM对象变得异常容易。其次，它统一了不同浏览器的API接口，使得代码在所有现代浏览器均能运行，开发者不用担心浏览器之间的差异。

# jquery 对象和 DOM 原生对象有什么区别？如何转化？

jQuery对象可以调用jQuery的方法，api，jQuery对象是一个类数组；DOM原生对象是文档对象模型，只能用原生JS的方法，DOM对象可以说一个，也可以是多个（类数组）

jQuery对象转DOM原生对象：加下标 `$('selector')[0]` 或者`$('selector').get(0)`

DOM原生对象转jQuery对象：$包裹原生对象

# jquery中如何绑定事件？bind、unbind、delegate、live、on、off都有什么作用？推荐使用哪种？使用on绑定事件使用事件代理的写法？

- jquery绑定事件：

jQuery提供一系列方法，允许直接为常见事件绑定回调函数。比如，click方法可以为一个元素绑定click事件的回调函数。

```javascript
$('li').click(function (e){
  console.log($(this).text());
});
```

- on方法

on方法是jQuery事件绑定的统一接口。事件绑定的那些简便方法，其实都是on方法的简写形式。 on方法接受两个参数，第一个是事件名称，第二个是回调函数。

```javascript
$('li').on('click', function (e){
  console.log($(this).text());
});
```

- bind()

为一个元素绑定一个事件处理程序。

- delegate()

为所有匹配选择器（selector参数）的元素绑定一个或多个事件处理函数，基于一个指定的根元素的子集，匹配的元素包括那些目前已经匹配到的元素，也包括那些今后可能匹配到的元素。

- unbind()

从元素上删除一个以前附加事件处理程序。

- live()

附加一个事件处理器到匹配目前选择器的所有元素，现在和未来。

- off()

移除一个事件处理函数。

绑定事件推荐： 推荐使用on，它的功能最齐全，也是官方推荐的事件绑定语法。

- 使用on进行事件代理：

```javascript
$('ul').on('click','li',function(){
  console(this);
});
//事件源为li时出发绑定事件
```

# jquery 如何展示/隐藏元素？

- show()

```javascript
.show( [duration ] [, easing ] [, complete ] )
//1.duration (默认: 400) .一个字符串或者数字决定动画将运行多久。字符串 'fast' 和 'slow' 分别代表200和600毫秒的延时。

//2.easing (默认: swing). 一个字符串，表示过渡使用哪种缓动函数。easing默认的是调用  swing, 如果想要在一个恒定的速度进行动画，那么调用 linear

//3.complete. 在动画完成时执行的函数。
```

- hide()

```javascript
.hide( [duration ] [, easing ] [, complete ] )
//1.duration (默认: 400) .一个字符串或者数字决定动画将运行多久。字符串 'fast' 和 'slow' 分别代表200和600毫秒的延时。

//2.easing (默认: swing). 一个字符串，表示过渡使用哪种缓动函数。easing默认的是调用  swing, 如果想要在一个恒定的速度进行动画，那么调用 linear

//3.complete. 在动画完成时执行的函数。
```

- toggle() 切换显示或隐藏当前元素。

# jquery 动画如何使用？

- jQuery提供以下一些动画效果方法。

> show：显示当前元素。

> hide：隐藏当前元素。

> toggle：显示或隐藏当前元素。

> fadeIn：将当前元素的不透明度（opacity）逐步提升到100%。

> fadeOut：将当前元素的不透明度逐步降为0%。

> fadeToggle：以逐渐透明或逐渐不透明的方式，折叠显示当前元素。

> slideDown：以从上向下滑入的方式显示当前元素。

> slideUp：以从下向上滑出的方式隐藏当前元素。

> slideToggle：以垂直滑入或滑出的方式，折叠显示当前元素。

- animate方法

上面这些动画效果方法，实际上都是animate方法的简便写法。在幕后，jQuery都是统一使用animate方法生成各种动画效果。 animate方法接受两个参数，第一个参数是一个对象，表示动画结束时相关CSS属性的值，第二个参数是动画持续的毫秒数。需要注意的是，第一个参数对象的成员名称，必须与CSS属性名称一致，如果CSS属性名称带有连字号，则需要用"骆驼拼写法"改写。animate方法还可以接受第三个参数，表示动画结束时的回调函数。

```javascript
$('div').animate({
    left: '+=50', // 增加50
    opacity: 0.25,
    fontSize: '12px'
  },
  300, // 持续时间
  function() { // 回调函数
     console.log('done!');
  }
);
```

- stop方法，delay方法

stop方法表示立即停止执行当前的动画。

```javascript
$("#stop").click(function() {
  $(".block").stop();
});
//点击按钮后，block元素的动画效果停止
```

delay方法接受一个时间参数，表示暂停多少毫秒后继续执行。

```javascript
$("#foo").slideUp(300).delay(800).fadeIn(400)
//slideUp动画之后，暂停800毫秒，然后继续执行fadeIn动画
```

# 如何设置和获取表单用户输入或者选择的内容？如何设置和获取元素属性？

- .val([value])

这是一个读写双用的方法，用来处理input的value，当方法没有参数的时候返回input的value值，当传递了一个参数的时候，方法修改input的value值为参数值

- .attr([value])

这是一个读写双用的方法，用来处理元素属性，当方法没有参数的时候返回元素属性值，当传递了一个参数的时候，方法修改元素属性值

# $.extend 的作用和用法?

$.extend方法用于将多个对象合并进第一个对象。

```javascript
var o1 = {p1:'a',p2:'b'};
var o2 = {p1:'c'};

$.extend(o1,o2);
o1.p1 // "c"
```

$.extend的另一种用法是生成一个新对象，用来继承原有对象。这时，它的第一个参数应该是一个空对象。

```javascript
var o1 = {p1:'a',p2:'b'};
var o2 = {p1:'c'};

var o = $.extend({},o1,o2);
o
// Object {p1: "c", p2: "b"}
```

默认情况下，extend方法生成的对象是"浅拷贝"，也就是说，如果某个属性是对象或数组，那么只会生成指向这个对象或数组的指针，而不会复制值。如果想要"深拷贝"，可以在extend方法的第一个参数传入布尔值true。

```javascript
var o1 = {p1:['a','b']};

var o2 = $.extend({},o1);
var o3 = $.extend(true,{},o1);

o1.p1[0]='c';

o2.p1 // ["c", "b"]
o3.p1 // ["a", "b"]
```

上面代码中，o2是浅拷贝，o3是深拷贝。结果，改变原始数组的属性，o2会跟着一起变，而o3不会。

# jQuery 的链式调用是什么？

jQuery最方便的一点就是，它的大部分方法返回的都是jQuery对象，因此可以链式操作。也就是说，后一个方法可以紧跟着写在前一个方法后面。

# jQuery 中 data 函数的作用

data方法用于在一个DOM对象上储存数据。

```javascript
// 储存数据
$("body").data("foo", 52);

// 读取数据
$("body").data("foo");
```

该方法可以在DOM节点上储存各种类型的数据。

# 写出以下功能对应的 jQuery 方法：

- 给元素 $node 添加 class active，给元素 $noed 删除 class active

  ```javascript
  $node.addClass('active');
  $node.removeClass('active');
  ```

- 展示元素$node, 隐藏元素$node

  ```javascript
  $node.show();
  $node.hide();
  ```

- 获取元素$node 的 属性: id、src、title， 修改以上属性

  ```javascript
  $node.attr('id');
  $node.sttr('src');
  $node.sttr('title');
  ```

- 给$node 添加自定义属性data-src

  ```javascript
  $node.attr('data-src','something');
  ```

- 在$ct 内部最开头添加元素$node

  ```javascript
  $ct.prepend('node');
  ```

- 在$ct 内部最末尾添加元素$node

  ```javascript
  $ct.append('node');
  ```

- 删除$node

  ```javascript
  $node.remove();
  ```

- 把$ct里内容清空

  ```javascript
  $ct.html('');
  ```

- 在$ct 里设置 html

  ```javascript
  $ct.html('<div class="btn"></div>');
  ```

- 获取、设置$node 的宽度、高度(分别不包括内边距、包括内边距、包括边框、包括外边距)

[jQuery获取和设置元素宽高](https://yoowinsu.github.io/2017/06/06/jQuery%E8%8E%B7%E5%8F%96%E5%92%8C%E8%AE%BE%E7%BD%AE%E5%85%83%E7%B4%A0%E5%AE%BD%E9%AB%98/)

- 获取窗口滚动条垂直滚动距离

  ```javascript
  $node.scrollTop();
  ```

- 获取$node 到根节点水平、垂直偏移距离

  ```javascript
  $node.offset();
  ```

- 修改$node 的样式，字体颜色设置红色，字体大小设置14px

  ```javascript
  $node.css({'color':'red','font-size':'14px'});
  ```

- 遍历节点，把每个节点里面的文本内容重复一遍

  ```javascript
  $element.each(function(){
    $(this).text($(this).text()+$(this).text())
  });
  ```

- 从$ct 里查找 class 为 .item的子元素

  ```javascript
  $ct.find('item');
  ```

- 获取$ct 里面的所有孩子

  ```javascript
  $ct.children();
  ```

- 对于$node，向上找到 class 为'.ct'的父亲，在从该父亲找到'.panel'的孩子

  ```javascript
  $node.parents('.ct').find('.panel');
  ```

- 获取选择元素的数量

  ```javascript
  $element.length;
  ```

- 获取当前元素在兄弟中的排行

  ```javascript
  $element.index();
  ```

# 用jQuery实现以下操作

- 当点击$btn 时，让 $btn 的背景色变为红色再变为蓝色

  ```javascript
  $btn.on('click',function(){
    $(this).css('background','red');
    setTimeout(function(){
        $btn.css({'background':'blue','transition':'2s'})
  },1000)
  })
  ```

- 当窗口滚动时，获取垂直滚动距离

  ```javascript
  $(window).on('scroll',function(){
    console.log($(window).scrollTop())
  })
  ```

- 当鼠标放置到$div 上，把$div 背景色改为红色，移出鼠标背景色变为白色

  ```javascript
  $div.on('mouseover',function(){
    $(this).css('background-color','red');
  })
  $div.on('mouseleave',function(){
    $(this).css('background-color','#fff');
  })
  ```

- 当鼠标激活 input 输入框时让输入框边框变为蓝色，当输入框内容改变时把输入框里的文字小写变为大写，当输入框失去焦点时去掉边框蓝色，控制台展示输入框里的文字

  ```javascript
  $('input').on('focus',function(){
    $(this).css('border-color','blue');
  })
  $('input').on('input',function(){
    $(this).val($(this).val().toUpperCase());
  })
  $('input').on('blur',function(){
    $(this).css('border-color','none');
    console.log($(this).val());
  })
  ```

- 当选择 select 后，获取用户选择的内容

  ```javascript
  $('select').on('change',function(){
  console.log($('select option:selected').text())
  })
  ```
