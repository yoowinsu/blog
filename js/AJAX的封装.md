---
title: AJAX的封装
categories: JavaScript
tags:
  - JavaScript
  - AJAX
date: 2017-05-26T00:12:57.000Z
---
![](https://unsplash.it/800/400/?image=280)
<!-- more -->
详细步骤见注释。

```javascript
function ajax(opts){
    var settings = {
        url: "",
        method: "get",
        data: {},
        dataType: "json",
        success: function(){},
        error: function(){}
    };


    //用户传动数据覆盖默认数据
    for(var attr in opts){
        settings[attr] = opts[attr];
    }


    //上面已经把用户传的数据覆盖过了，所以这里拼接的数据是settings的数据
    var arr = [];
    for(var attr in settings.data){
        arr.push(attr + "=" + settings.data[attr]);
    }    
    var dataStr = arr.join("&");


    //声明xhr对象
    var xhr = window.XMLHttpRequest? new XMLHttpRequest: ActiveXObject("Microsoft.XMLHTTP");


    //设置完成事件的兼容性
    if(typeof xhr.onload === "undefined"){    //判断是否是ie6
        xhr.onreadystatechange = ready;
    }else{
        xhr.onload = ready;
    }

    //回调函数
    function ready() {
        if(xhr.readyState === 4) {
            //只有2xx和304的状态码，表示服务器返回是正常状态
            //因为get请求中都添加了时间戳，所以这里不考虑缓存出现（即304）的情况
            if(xhr.status >= 200 && xhr.status < 300) {
                switch (settings.dataType.toLocaleLowerCase()) {
                    case "text":
                        settings.success(xhr.responseText);
                        break;
                    case "json":
                        settings.success(JSON.parse(xhr.responseText));
                        break;
                    case "xml":
                        settings.success(xhr.responseXML);
                }
            }else{
                settings.error();
            }
        }
    }


    //判断请求方式
    if(settings.method.toLocaleLowerCase() === "get") {
        //有缓存所以要每次请求地址不一样才能更新，所以用时间戳
        //第三个参数完全可以略去，因为如果用同步（false）会对浏览器有“堵塞效应”
        xhr.open(settings.method, settings.url + "?" + encodeURI(dataStr) +'&'+ new Date().getTime(), true);
        xhr.send();
    }else{
        xhr.open(settings.method, settings.url, true);
        xhr.setRequestHeadr("Content-Type", "application/x-www-form-urlencoded");
        xhr.send(encodeURI(dataStr));
    }

}
```
