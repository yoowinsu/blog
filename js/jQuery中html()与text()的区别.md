## jQuery中html()与text()的区别
- ### html()

    1.不传参
	html()：不管取得的jQuery对象是否为多个，只获取匹配的第一个元素的html内容。这个函数不能用于XML文档。但可以用于XHTML文档，返回的是一个String

		```
        //html页面代码
		<div>
			<p><span>早上</span></p>
			<p><span>好</span></p>;
		</div>

        //jquery代码
		$("p").html();

        //结果
		<span>早上</span>;
		```

    2.传参
	html(val)：设置每一个匹配元素的html内容。这个函数不能用于XML文档。但可以用于XHTML文档。如果传参包括HTML节点，则会以生成元素节点的形式添加。返回一个jQuery对象

		```
        //html页面代码
		<div>这里会显示：
			<p></p>
			<p></p>
		</div>

        //jquery代码
		$("p").html("<span>早上</span>");

        //结果
		这里会显示：早上
		早上
		```     

- ### text()

        1.不传参 
		text()：取得所有匹配元素的内容并返回拼接后的字符串。结果是由所有匹配元素包含的文本内容组合起来的文本。返回的是一个String

		```
        //html页面代码
		<div>
			<p><span>早上</span></p>
			<p><span>好</span></p>;
		</div>

        //jquery代码
		$("p").text();

        //结果
		早上好
		```

		2.传参
		text(val)：设置所有匹配元素的文本内容，与 html()类似，但如果传参包含'<'或'>'，将会转义成文本显示在文本节点中。返回一个jQuery对象

		```
        //html页面代码
		<div>这里会显示：
			<p></p>
			<p></p>
		</div>

        //jquery代码
		$("p").html("<span>早上</span>");

        //结果
		这里会显示：<span>早上</span>
		<span>早上</span>
		``` 