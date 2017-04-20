## 实现效果：
![空心三角箭头](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/qIkdPtx.A0WcCc5YMrUzIZu1r0G*.bQisf*V4XmvKdc!/r/dGoBAAAAAAAA)

## 实现原理：
- 先实现实心三角箭头的效果
![黑色三角的实心三角箭头效果](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/aI8BDMjCRcnnTkDGKpRUNDd1zu46xrVLqkukvWKbtqE!/r/dGkBAAAAAAAA)
换成粉色看更直观：
![更直观的实心三角箭头效果](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/0ILHGiUIpoxO0LOVbtD00bWAPOJBwSP8mRPzKr4qV5U!/r/dGkBAAAAAAAA)
- 利用伪类再添加一个三角形覆盖原来三角形箭头的部分区域，使得没覆盖的部分呈现箭头形状且和矩形边框宽度一致(效果中颜色视为了更好地呈现效果，把粉色换成蓝色，红色换成黑色即可)
![直观实现效果](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/JjsIGsSYFQkZNoCgjnmJ*ZsuhWrfDaq4H02AJ7dI49o!/r/dGoBAAAAAAAA)
- 伪类三角形的背景颜色换成和矩形背景颜色一致，下面的三角形换成和边框颜色一致
![空心三角箭头](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/qIkdPtx.A0WcCc5YMrUzIZu1r0G*.bQisf*V4XmvKdc!/r/dGoBAAAAAAAA)
## 难点（容易被忽略的一点）
- 伪类三角形的偏移值和矩形边框宽度一样吗？

答案是否定的！
伪类三角形向下的偏移值其实应该是矩形边框宽度的“根号2”倍，约为1.414，为了方便可以按1.4倍计算。看下图是原理：
![勾股定理](http://r.photo.store.qq.com/psb?/V10XVXwu3e9w9Z/Y7xC4MLeT.OAkUq1wcHUk9JdfcWdLLd8*gZ0yxW43sk!/r/dFYBAAAAAAAA)
其中，效果中的矩形边框宽度为6px，所以要实现空心箭头边框宽度为6px的话，伪类三角形向下的偏移量应为6*1.4=8.4px

[在线demo](https://yoowinsu.github.io/demos/just-demos/%E7%A9%BA%E5%BF%83%E4%B8%89%E8%A7%92%E7%AE%AD%E5%A4%B4%E5%AE%9E%E7%8E%B0%E6%95%88%E6%9E%9C.html)

### 附代码：

```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>空心三角形效果的实现</title>
    <style>
        .air-tip-top {
            position: relative;
            width: 300px;
            margin-top: 100px;
            margin-left: 100px;
        }
        .air-tip-top .container{
            width: 300px;
            height: 200px;
            border: 6px solid #000;
            background-color: #8a98ff;
        }
        .air-tip-top .triangle-double{
            position: absolute;
            top: -20px;
            left: 20px;
            border-left: 20px solid transparent ;
            border-right: 20px solid transparent;
            border-bottom: 20px solid #000;
        }
        .air-tip-top .triangle-double:after{
            content: '';
            display: block;
            position: absolute;
            top: 8.4px; /*向下偏移量是矩形边框宽度的1.4（根号2）倍*/
            left: -20px;
            border-left: 20px solid transparent;
            border-right: 20px solid transparent;
            border-bottom: 20px solid #8a98ff;
        }
    </style>
</head>
<body>
<div class="air-tip-top">
    <span class="triangle-double"></span>
    <div class="container"></div>
</div>
</body>
</html>
```