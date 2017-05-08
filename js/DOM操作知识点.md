## dom对象的innerText和innerHTML有什么区别？
- innerText是一个可写属性，返回元素内包含的文本内容，在多层次的时候会按照元素由浅到深的顺序拼接其内容
- innerHTML属性作用和innerText类似，但是不是返回元素的文本内容，而是返回元素的HTML结构，在写入的时候也会自动构建DOM

## elem.children和elem.childNodes的区别？
- Element.children属性返回包括当前元素节点的所有子元素，与childNodes属性的区别是，它只包括HTML元素类型的子节点，不包括其他类型的子节点。
- childNodes获取元素的第一层的所有子节点，包含文本、注释
## 查询元素有几种常见的方法？ES5的元素选择方法是什么?
- getElementById()
- getElementsByClassName()
- getElementsByTagName()
- getElementsByName()

ES5的元素选择方法：
- querySelector()
- querySelectorAll()

## 如何创建一个元素？如何给元素设置属性？如何删除属性
创建元素：
- document.createElement()
document.createElement方法用来生成网页元素节点。

- document.createTextNode()
document.createTextNode方法用来生成文本节点，参数为所要生成的文本节点的内容。

- document.createDocumentFragment()
createDocumentFragment方法生成一个DocumentFragment对象。

给元素设置属性：
- getAttribute()

getAttribute()用于获取元素的attribute值

createAttribute()方法生成一个新的属性对象节点，并返回它。

setAttribute()方法用于设置元素属性

删除属性：

removeAttribute()用于删除元素属性

## 如何给页面元素添加子元素？如何删除页面元素下的子元素?
- appendChild()
在元素末尾添加元素

- insertBefore()
在某个元素之前插入元素

- replaceChild()
replaceChild()接受两个参数：要插入的元素和要替换的元素

- parentNode.removeChild(childNode)
删除元素

## element.classList有哪些方法？如何判断一个元素的 class 列表中是包含某个 class？如何添加一个class？如何删除一个class?

- classList对象有下列方法:

```
add()：增加一个class。
remove()：移除一个class。
contains()：检查当前元素是否包含某个class。
toggle()：将某个class移入或移出当前元素。
item()：返回指定索引位置的class。
toString()：将class的列表转为字符串。
```

- 判断一个元素的 class 列表中是包含某个 class:

```
/*第一种：*/
Element.classList.contains('myCssClass'); // 返回 true 或者 false

/*第二种：*/
function hasClass(className){
	/*假设检测的类名是'cls'*/
	return (/(^|\s+)cls($|\s+)/).test(className);
}
```

- 如何删除一个class：

```
// 添加class
document.getElementById('foo').classList.add('bold');

// 删除class
document.getElementById('foo').classList.remove('bold');

//toggle方法可以接受一个布尔值，作为第二个参数。如果为true，则添加该属性；如果为false，则去除该属性。
element.classList.toggle('abc', boolean);
```

## 如何选中如下代码所有的li元素？ 如何选中btn元素？

```
<div class="mod-tabs">
   <ul>
       <li>list1<li>
       <li>list2<li>
       <li>list3<li>
   </ul>
   <button class="btn">点我</button>
</div>

- 选中li元素
document.getElementsByTagName('li');
document.getquerySelectorAll('li');

- 选中btn
document.getElementsByClassName('btn');
docunment.getquerySelector('.btn');
```