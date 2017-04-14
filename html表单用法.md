# HTML表单介绍
用于搜集不同类型的用户输入。HTML表单是被包含在form标签里的。
### <form>元素
常用属性：
- action ：表单提交的地址
- method ：提交表单的方法，有get和post两种
![get和post区别](http://upload-images.jianshu.io/upload_images/4669529-45d19e5a168d85ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 表单元素
HTML 表单包含表单元素。
表单元素指的是不同类型的 input 元素、复选框、单选按钮、提交按钮等等。
- ### <input> 元素
<input> 元素是最重要的表单元素。
<input> 元素有很多形态，根据不同的 type 属性。
**1.<input type="text"> **
定义供文本输入的单行输入字段
![输入类型：text](http://upload-images.jianshu.io/upload_images/4669529-46fd62ed4d7141e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*注意：有一个value属性，对应的值会默认显示在输入框中；html5中有一个placeholder 属性，提供可描述输入字段预期值的提示信息。
该提示会在输入字段为空时显示，并会在字段获得焦点时消失*

*注意：text对应有个label标签，label标签中有个for属性，for属性对应text中id的值，当值一致时，点击label对应的文字时，输入框将获取焦点*

**2.<input type="password">**
定义密码字段，字段中的字符会被做掩码处理（显示为星号或实心圆）

![输入类型：password](http://upload-images.jianshu.io/upload_images/4669529-5ce9ec093ee77549.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*注意：html5中有一个placeholder 属性，提供可描述输入字段预期值的提示信息。
该提示会在输入字段为空时显示，并会在字段获得焦点时消失*

*注意：password对应有个label标签，label标签中有个for属性，for属性对应password中id的值，当值一致时，点击label对应的文字时，输入框将获取焦点*

**3.<input type="submit">**
 定义提交表单数据至表单处理程序的按钮，value值是提交按钮显示的值，不写则默认是submit


![输入类型：submit](http://upload-images.jianshu.io/upload_images/4669529-cd3218784d3ff17c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**4.<input type="radio">**
 定义单选按钮，同一组单选按钮的name值必须一致，被选中的按钮，将提交name：value对应的数据

![输入类型：radio](http://upload-images.jianshu.io/upload_images/4669529-1312fbeb303af864.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*注意：如果想让某一项默认被选中，可以在input标签中加上“checked”属性*

**5.<input type="checkbox">** 
定义复选框，同一组复选框name值必须一致，被选中的按钮，将提交name：value对应的数据

![输入类型：checkbox](http://upload-images.jianshu.io/upload_images/4669529-0bf7e0dc0660fbf5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*注意：如果想让某一项默认被选中，可以在input标签中加上“checked”属性*

**6.<input type="button>** 
定义按钮，value值对应按钮上显示的值


![输入类型：button](http://upload-images.jianshu.io/upload_images/4669529-2e33ec7ada91a534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**7.<input type="file" />** 
用于文件上传，accept属性用于指定上传文件的类型
![输入类型：file](http://upload-images.jianshu.io/upload_images/4669529-087d4ac0d5d82eea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**8.<input type="hidden" />** 
定义隐藏字段。隐藏字段对于用户是不可见的。隐藏字段通常会存储一个默认值，它们的值也可以由 JavaScript 进行修改。
暂存一些信息。可以将一些必要的又不需要显示的数据存放到<input type="hidden" />中；
提高了安全性，通过传输的数据与服务器的数据做校验，验证是否正确，避免恶意上传以及被攻击。
![输入类型：hidden](http://upload-images.jianshu.io/upload_images/4669529-3aabf73da8ca370f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- ### <select> 元素
<select> 元素定义下拉列表
<option> 元素定义待选择的选项。
列表通常会把首个选项显示为被选选项。
您能够通过添加 selected 属性来定义预定义选项。

![select元素](http://upload-images.jianshu.io/upload_images/4669529-a65ba181d318478c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- ###<textarea> 元素
<textarea> 元素定义多行输入字段（文本域）
有cols和rows属性，对应的是行数和列数。
label元素for属性对应textarea的id属性，点击“多行文本”是输入框就会获取焦点

![textarea元素](http://upload-images.jianshu.io/upload_images/4669529-c1744db025bbf2f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
