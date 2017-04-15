# form表单有什么作用？有哪些常用的input 标签，分别有什么作用？
- HTML表单用于搜集不同类型的用户输入
```

<input type="text"> 定义供文本输入的单行输入字段
<input type="password"> 定义密码字段
<input type="submit"> 定义提交表单数据至表单处理程序的按钮
<input type="radio"> 定义单选按钮
<input type="checkbox"> 定义复选框
<input type="button> 定义按钮
<input type="number"> 用于应该包含数字值的输入字段(能够对数字做出限制)
<input type="date"> 用于应该包含日期的输入字段
<input type="color"> 用于应该包含颜色的输入字段
<input type="range"> 用于应该包含一定范围内的值的输入字段
<input type="month"> 允许用户选择月份和年份
<input type="week"> 允许用户选择周和年
<input type="time"> 允许用户选择时间（无时区）
<input type="datetime"> 允许用户选择日期和时间（有时区）
<input type="datetime-local"> 允许用户选择日期和时间（无时区）
<input type="email"> 用于应该包含电子邮件地址的输入字段
<input type="search"> 用于搜索字段（搜索字段的表现类似常规文本字段）
<input type="tel"> 用于应该包含电话号码的输入字段
<input type="url"> 用于应该包含 URL 地址的输入字段

```
#post 和 get 方式的区别？
- GET
1.从指定的资源请求数据，基本上用于从服务器获得（取回）数据
2.GET 方法可能返回缓存数据
3.不安全，用户的所有信息都会暴露出来
4.请求有长度限制
- POST
1.向指定的资源提交要处理的数据，也可用于从服务器获取数据
2.POST 方法不会缓存数据
3.相对来说安全，因为不直接暴露用户信息
4.请求对数据长度没有要求

![post和get区别](http://upload-images.jianshu.io/upload_images/4669529-45d19e5a168d85ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#在input里，name 有什么作用？
如果要正确地被提交，每个输入字段必须设置一个 name 属性。name的值在提交的数据中相当于一个key值，是不可或缺的，用户输入的值相当于value，key和value是对应的
# radio 如何 分组?
name的值相同的话会被浏览器认定为同一组单选按钮
# placeholder 属性有什么作用?
placeholder 属性提供可描述输入字段预期值的提示信息。
该提示会在输入字段为空时显示，并会在字段获得焦点时消失。
placeholder 属性适用于以下的 <input> 类型：text, search, url, telephone, email 以及 password
# type=hidden隐藏域有什么作用? 举例说明
- <input type="hidden" /> 定义隐藏字段。隐藏字段对于用户是不可见的。隐藏字段通常会存储一个默认值，它们的值也可以由 JavaScript 进行修改。
暂存一些信息。可以将一些必要的又不需要显示的数据存放到<input type="hidden" />中；
提高了安全性，通过传输的数据与服务器的数据做校验，验证是否正确，避免恶意上传以及被攻击。
