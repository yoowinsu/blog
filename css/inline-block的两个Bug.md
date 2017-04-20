## 1.元素之间的间隙
两个inline-block 元素之间会出现间隙。如下图：
![空隙](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/3cX*L9uFmfRp*.NV.PDaW7i9wFznJFVMzat1AwzfIq4!/r/dGoBAAAAAAAA)
解决方法：
- 将父元素的 font-size 设置为0，然后在 inline-block 元素中将 font-size 设置为 14px，如下图：
![父元素font-size=0](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/V2sVnF6Kwt8o7amTVa2KBHbYFGJ9XOyksxd5w7LCyBQ!/r/dGkBAAAAAAAA)
- 去掉元素之间的空格、回车、tab。如下图：
![去掉空格、换行](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/I.0wThy*q4KRIzXTa7GrjdnukuJB*lFKWiGYCF0uS*I!/r/dGkBAAAAAAAA)

## 2.不同高度的元素无法对齐
两个不同高度的 inline-block 元素无法对齐。如下图：
![对不齐的情况](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/SOLPRr310kSNCStAfVN*7IzFHlwSFgBS3aZ*DPMHmqg!/r/dGkBAAAAAAAA)
解决方法：
- 改变 inline-block 元素的 vertical-align，一般改为 top 或 middle.如下图：
![top](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/OtZmObHVVTVxiDubedFFztaBLMQR50PFroVr.BHBe4w!/r/dGgBAAAAAAAA)
![middle](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/rafYRjPsa*KivYbdS2i2GcXAgjPlrNi92sB78jD7lqI!/r/dGkBAAAAAAAA)
## 还有一种现象就是img元素下面无缘无故多出几像素（img默认是inline-block）
如下图：
![img下面留白](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/D3azQa0Z3LTuxQkOci*1oZU7dxRmf.5*M0zFKdatGVA!/r/dGoBAAAAAAAA)
解决办法：
- 设置vertical-align为bottom，如下图：
![vertical-align为bottom](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/lOE120utDhjlzYq.seFXuuXySIWoZii8zb.Wtuu96Ic!/r/dGoBAAAAAAAA)
## 建议
工作中，使用 float 或 flex，尽量不要使用 inline-block，如果要使用，请避开bug

## 更多
[张鑫旭--去除inline-block元素间间距的N种方法](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)
[知乎--<img>元素底部为何有空白？](https://www.zhihu.com/question/21558138)