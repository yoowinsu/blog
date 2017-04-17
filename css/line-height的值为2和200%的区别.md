line-height: 2和line-height: 200%是有区别的。
两个属性设置给具体的某一个元素时是没有区别的。如下图：

![都设置为line-height: 2](http://upload-images.jianshu.io/upload_images/4669529-3647dabdc94443e8.png?imageMogr2/auto-orient/strip%7CimageView2/2)

![line-height: 200%，表现和设置为line-height: 2一样](http://upload-images.jianshu.io/upload_images/4669529-a2c90bac80770b7d.png?imageMogr2/auto-orient/strip%7CimageView2/2)

那么他们的区别又在哪里呢？
区别就是他们设置两种不同的属性后其子元素表现样式上的区别！
可以看下面的例子：
- 父元素设置line-height: 200%;属性时
父元素设置这个属性后，其所有子元素的行高都是一个具体的值，即他们父元素字体大小的200%。下例可看出子元素的行高都一致，即父元素字体大小的2倍，32px。

![line-height：200%属性下子元素行高是具体的值](http://upload-images.jianshu.io/upload_images/4669529-5a8c4f77d4ae2719.png?imageMogr2/auto-orient/strip%7CimageView2/2)

- 父元素设置line-height: 2;属性时
父元素设置这个属性后，其所有子元素的行高都是自身字体大小的2倍。下例可看出子元素的行高都是不一致的。

![line-height：2;属性下子元素行高都是一个相对自身字体大小的值](http://upload-images.jianshu.io/upload_images/4669529-19a2afc8a9b018b7.png?imageMogr2/auto-orient/strip%7CimageView2/2)
