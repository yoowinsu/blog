---
title: 检测数据类型的N种方法
categories: JavaScript
tags:
  - JavaScript
  - 数据类型
date: 2017-07-08 18:29:31
---
![](https://unsplash.it/800/400/?image=404)
<!-- more -->
最新的 ECMAScript 标准定义了 7 种数据类型:
6 种 原始类型:Boolean、Null、Undefined、Number、String、Symbol (ECMAScript 6 新定义)和 Object。

原始类型中，一般我们认为null和undefined是两个特殊的值；
Object包括Object、Function、Array、RegExp、Date等等。
下面开始总结检测数据类型的几种方法：
### typeof
typeof可以检测Number、String、Symbol、Boolean、Undefined、Function的类型，其他的类型都返回Object，也就是说区分不出一个数据到底是数组还是对象还是正则表达式，所以这个办法不适合检测对象的数据类型
```js
typeof ''; // string
typeof 1; // number
typeof true; //boolean
typeof (Symbol());//symbol
typeof (function(){}); // function
typeof undefined; //undefined
typeof null; //object
typeof [] ; //object
typeof new Date(); //object
typeof new RegExp(); //object
```
### instanceof
instanceof运算符返回一个布尔值，表示指定对象是否为某个构造函数的实例。
instanceof的原理是检查原型链，对于那些不存在原型链的对象，就无法判断。下面代码中，obj不存在原型，因此instanceof就认为该对象不是Object的实例。
```js
var obj = Object.create(null)
obj instanceof Object // false
```
除了上面的特殊情况，JavaScript之中，只要是对象，就有对应的构造函数。因此，instanceof运算符的一个用处，是判断值的类型。如下：
```js
[1, 2, 3] instanceof Array // true
{} instanceof Object // true
function(){} instanceof Function //true
new Date() instanceof Date  //true
```
注意，instanceof运算符只能用于对象，不适用原始类型的值。

### constructor
prototype对象有一个constructor属性，默认指向prototype对象所在的构造函数。
除了null和undefined之外所有的对象都能从原型对象上获取constructor属性，从而获取数据类型
null和undefined会报错：
```js
null.contructor  //TypeError
undefined.contructor  //TypeError
```
其他的对象都可以通过constructor获取到数据类型：
```js
([1, 2, 3]).constructor === Array // true
({}).constructor === Object // true
(function(){}).constructor === Function //true
(new Date()).constructor === Date  //true
```
constructor虽然是对象属性，但是原始类型的数据依然可以检测数据类型：
```js
(123).constructor === Number // true
//等于(new Number(123)).constructor === Number

false.constructor === Boolean // true
//等于(new Boolean(false)).constructor === Boolean 

'123'.constructor === String // true
//等于(new String('123')).constructor === String 
``` 
在构造函数的实例中，原型对象中的属性constructor指向构造函数，所以不能检测数据类型；
因为constructor是属性，如果被修改，就获取不到数据类型了：
```js
var obj = {constructor:'我是constructor'}
obj.constructor  //"我是constructor"
obj.constructor === Object  //false
```
这说明constructor不是一个检测数据类型的最佳选择。

### Object.prototype.toString 
Object.prototype.toString方法返回对象的类型字符串，因此可以用来判断一个值的类型。这也是检测数据类型的最好选择。
一般toString()方法就可以判断一个值的数据类型，但是实例对象自定义toString()方法的话，就会覆盖掉Object.prototype.toString方法。
我们可以通过函数的call方法，在期望检测数据上准确调用Object.prototype.toString方法，帮助我们判断数据的类型。
```js
Object.prototype.toString.call(123) // "[object Number]"
Object.prototype.toString.call('123') // "[object String]"
Object.prototype.toString.call(true) // "[object Boolean]"
Object.prototype.toString.call(undefined) // "[object Undefined]"
Object.prototype.toString.call(null) // "[object Null]"
Object.prototype.toString.call(Math) // "[object Math]"
Object.prototype.toString.call({}) // "[object Object]"
Object.prototype.toString.call([]) // "[object Array]"
Object.prototype.toString.call(new Date()) // "[object Date]"
```

(本文未考虑多个frame或多个window之间的交互情况)