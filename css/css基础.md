# CSS的全称是什么?
CSS全称是 Cascading Style Sheets，即层叠样式表
# CSS有几种引入方式? link 和@import 有什么区别?
CSS的引入一般有三种

- 外部资源引入
- style标签
- 内联style属性

使用link和@import的区别：

- link属于标签，除了加载CSS外，还能用于定义RSS，定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS；

- 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载；

- import是CSS2.1 提出的，只在IE5以上才能被识别，而link是 标签，无兼容问题。
# 以下这几种文件路径分别用在什么地方，代表什么意思?
```
css/a.css  /*指定当前目录下的css文件中的a.css文件，属于相对路径*/

./css/a.css /*指定当前目录下的css文件中的a.css文件（和上面的等价），属于相对路径*/

b.css /*指定当前目录中的b.css文件，属于相对路径*/

../imgs/a.png /*指定上一级目录中的imgs文件夹下的a.png文件，属于相对路径*/

/Users/hunger/project/css/a.css /*指定a.css的从根目录开始的完整路径，属于绝对路径*/

/static/css/a.css /*网站中也可以使用相对路径*/

http://cdn.jirengu.com/kejian1/8-1.png /*指定网络图片的地址，属于网站路径*/
```
# 如果我想在js.jirengu.com上展示一个图片，需要怎么操作?
- 上传到服务器，使用相对路径引用图片
- 可以使用图片的网站链接地址。如果没有网站链接地址，可以上传至第三方工具生成链接地址再引用

# 列出5条以上html和 css 的书写规范
- css语法不区分大小写，但建议统一使用小写
- css不使用内联的style属性定义样式
- id和class使用有意义的单词，体现其功能，分隔符建议使用-（中划线）
- 属性值是0的省略单位
- 尽可能的复用样式
- 复合样式可以提高编码效率
