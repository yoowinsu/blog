# 1.元素之间的间隙

两个inline-block 元素之间会出现间隙。如下图：

![空隙](https://ooo.0o0.ooo/2017/06/21/5949e229b7b47.png) 
解决方法：

- 第一种：

将父元素的 font-size 设置为0，然后在 inline-block 元素中将 font-size 设置为 14px，如下图：

![父元素font-size=0](https://ooo.0o0.ooo/2017/06/21/5949e2299bf09.png)

- 第二种：

去掉元素之间的空格、回车、tab。如下图：

![去掉空格、换行](https://ooo.0o0.ooo/2017/06/21/5949e229b52c3.png)

# 2.不同高度的元素无法对齐

两个不同高度的 inline-block 元素无法对齐。如下图：

![对不齐的情况](https://ooo.0o0.ooo/2017/06/21/5949e229b8b23.png)

解决方法：

改变 inline-block 元素的 vertical-align，一般改为 top 或 middle.如下图：

![top](https://ooo.0o0.ooo/2017/06/21/5949e2299cbfe.png)

![middle](https://ooo.0o0.ooo/2017/06/21/5949e229ba60f.png)

# 还有一种现象就是img元素下面无缘无故多出几像素（img默认是inline-block）

img下面留白,如下图：

![img下面留白](https://ooo.0o0.ooo/2017/06/21/5949e229b9989.png)

解决办法：

设置vertical-align为bottom，如下图：

![vertical-align为bottom](https://ooo.0o0.ooo/2017/06/21/5949e229bb1de.png)

# 建议

工作中，使用 float 或 flex，尽量不要使用 inline-block，如果要使用，请避开bug

## 更多

[张鑫旭--去除inline-block元素间间距的N种方法](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

[知乎--![]()元素底部为何有空白？](https://www.zhihu.com/question/21558138)