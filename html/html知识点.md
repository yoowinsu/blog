# HTML、XML、XHTML 有什么区别
- HTML，超文本标记语言，是语法较为松散的、不严格的Web语言；
- XML，可扩展标记语言，主要用于存储数据和结构；
- XHTML，可扩展超文本标记语言，基于XML，作用与HTML类似，但语法更严格。

# 怎样理解 HTML 语义化
HTML一直在朝语义化的方向发展。
- 语义化利于计算器和开发者更容易读懂代码，有利于SEO，可以更好地让搜索引擎抓取和理解文档；
- 语义化可以让有视觉障碍的人群可以获取页面信息；
- W3C推出的HTML5进一步推进了语义化发展，诸如nav、footer等语义化标签，弥补了采用id="footer"或者class="footer"形式的不足，以更好的推动Web的发展；
- 节省维护成本，提高开发效率

# 怎样理解内容与样式分离的原则
- 尽量避免出现行内样式
- 可以降低后期维护成本和提高开发效率
- 可以提高样式代码的复用率
- 在HTML结构没有样式的情况下依然可以语义化的显示内容，不受样式影响

# 有哪些常见的meta标签
META标签用来描述一个HTML网页文档的属性，例如作者、日期和时间、网页描述、关键词、页面刷新等。
META标签可分为两大部分：HTTP-EQUIV和NAME变量。
HTTP-EQUIV：
```
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">字符集设置为utf-8
<meta http-equiv="Content-Language" content="zh-CN">语言设置为中文
<meta http-equiv="Refresh" content="n;url=http://yourlink">定时让网页在指定的时间n内，跳转到你的页面
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">针对浏览器版本选择渲染的设置
<meta http-equiv="Expires" content="Mon,12 May 2001 00:20:00 GMT">cookie设定，如果网页过期，存盘的cookie将被删除
<meta http-equiv="Pragma" content="no-cache">用于设定禁止浏览器从本地机的缓存中调阅页面内容
<meta http-equiv="Page-Enter" content="revealTrans（duration=10,transition= 50）">设定进入页面时的特殊效果
<meta http-equiv="Page-Exit" content="revealTrans（duration=20，transition=6）">设定进入和离开页面时的特殊效果
<meta http-equiv="windows-Target" content="_top">强制页面在当前窗口中以独立页面显示，防止网页被当作frame页调用
```
NAME（一般放于title标签后面）：
```
<meta name="keywords" content="科比 詹姆斯" />关键词
<meta name="description" content="NBA是美国职业篮球联盟" />网站描述，用于在搜索引擎上显示的网站描述（自然语言，非关键词），用于SEO
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" >网页视窗，合理的呈现于各种设备窗口
<meta name="Author" content="" />作者
```

# 文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用?
- <!DOCTYPE>声明位于位于HTML文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
- 严格模式：也叫标准模式。标准模式的排版和JS运作模式都是以该浏览器支持的最高标准运行。
混杂模式：也叫兼容模式。在兼容模式中，页面以宽松的向后兼容的方式显示，模拟老式浏览器的行为以防止站点无法工作。
- <!doctype html>用来声明当前文档为html5方法。
HTML5不基于SGML，因此不需要对DTD进行引用，但是需要DOCTYPE来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
HTML4.01基于SGML，所以需要对DTD进行引用，才能让浏览器知道该文档所使用的文档类型。

# 浏览器乱码的原因是什么？如何解决
- 乱码的原因通俗点讲就是文档保存的编码格式和文档中声明的charset不一致导致的。
- 保存的文件编码格式和文档中charset要一致。
[编码与乱码](https://zhuanlan.zhihu.com/p/24465635?refer=study-fe)

# 常见的浏览器有哪些，什么内核
- 常见浏览器有Chrome、IE、Firefox、Opera、Safari等
- Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]
Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]
[浏览器内核的解析和对比](http://www.cnblogs.com/fullhouse/archive/2011/12/19/2293455.html)

# 列出常见的标签，并简单介绍这些标签用在什么场景
```
<!DOCTYPE>定义文档类型
<html>定义了整个 HTML 文档
<head>定义关于文档的信息
<title>网页的标题
<meta>定义关于 HTML 文档的元信息
<link>一些外置文件关联
<script>定义客户端脚本
<style>定义文档的样式信息
<!--...-->注释
<body>HTML 文档的主体
<h1>-<h6 >HTML 标题
<em>强调文本
<form>定义供用户输入的 HTML 表单
<a>锚
<span>用来组合文档中的行内元素，适当增强语义
<img>图片标签
<input >输入控件
<button>按钮
<select >选择列表（下拉列表）
<strong >强调的语气
<div>块元素
<ul>无序列表
<ol>有序列表
<li>列表的项目
<dl>定义列表
<dt>定义列表中的项目
<dd>定义列表中的项目的描述
<table>定义表格
<caption>定义表格标题
<th>定义表格中的表头单元格
<tr>定义表格中的行
<td>定义表格中的单元
<p>文字段落
<br>换行
```