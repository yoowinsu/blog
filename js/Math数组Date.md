## 写一个函数，返回从min到max之间的 随机整数，包括min不包括max 

```
function getRandNum(min,max){
		var num = Math.ceil(min)+Math.floor(Math.random()*(Math.floor(max)-Math.ceil(min)));
		// console.log(num)
		return num;
	}
```

## 写一个函数，返回从min都max之间的 随机整数，包括min包括max 

```
function getRandNum(min,max){
		var num = Math.ceil(min)+Math.floor(Math.random()*(Math.floor(max)-Math.ceil(min)+1));
		// console.log(num)
		return num;
	}
```

## 写一个函数，生成一个长度为 n 的随机字符串，字符串字符的取值范围包括0到9，a到 z，A到Z。

```
	function getRandStr(len){
		var str="0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
  		var newStr="";

  		for (var i = 0; i <len; i++) {
  			var one=str[Math.floor(Math.random()*62)];
  			newStr+=one;
  		}
  		return newStr;
	}

	console.log(getRandStr(3))
```

## 写一个函数，生成一个随机 IP 地址，一个合法的 IP 地址为 0.0.0.0~255.255.255.255

```
function getRandIP(){
	var arr = [];
	for (var i =0; i<4; i++) {
		arr[i] =Math.floor(Math.random()*256);
	}
	console.log(arr);
	return arr.join('.');
}
var ip = getRandIP()
console.log(ip)
```

## 写一个函数，生成一个随机颜色字符串，合法的颜色为#000000~ #ffffff

```
/*第一种*/
function getRandColor(){
	var str="0123456789abcdef";
	var newStr="";
	var ch;
	for (var i = 0; i <6; i++) {
		ch=str[Math.floor(Math.random()*16)];
		newStr+=ch;
	}
	newStr="#"+newStr;
	return newStr;
}
var color = getRandColor()
console.log(color) 

/*第二种*/
function getRandColor(){
	var str="0123456789abcdef";
	var newStr="";
	var arr=[];
	for (var i = 0; i <6; i++) {
		arr[i]=str[Math.floor(Math.random()*16)];
	}
	newStr="#"+arr.join('');
	return newStr;
}
var color = getRandColor()
console.log(color)
```
# 数组任务

## 数组方法里push、pop、shift、unshift、join、splice分别是什么作用？

- push方法用于在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度。注意，该方法会改变原数组。
- pop方法用于删除数组的最后一个元素，并返回该元素。注意，该方法会改变原数组。
- shift方法用于删除数组的第一个元素，并返回该元素。注意，该方法会改变原数组。
- unshift方法用于在数组的第一个位置添加元素，并返回添加新元素后的数组长度。注意，该方法会改变原数组。
- join方法以参数作为分隔符，将所有数组成员组成一个字符串返回。如果不提供参数，默认用逗号分隔。
- splice方法用于删除原数组的一部分成员，并可以在被删除的位置添加入新的数组成员，返回值是被删除的元素。注意，该方法会改变原数组。

## 用 splice函数分别实现push、pop、shift、unshift方法
- 实现push

```
var arr=[9,6,3,0]
arr.splice(arr.length,0,100)
console.log(arr.length)
```
- 实现pop

```
var arr=[9,6,3,0]
arr.splice(arr.length-1,1)
console.log(arr)
```
- 实现shift

```
var arr=[9,6,3,0]
arr.splice(0,1)
console.log(arr)
```
- 实现unshift

```
var arr=[9,6,3,0]
arr.splice(0,0,100)
console.log(arr.length)
```
## 写一个函数，操作数组，数组中的每一项变为原来的平方，在原数组上操作

```
/*第一种*/
function squareArr(arr){
	for(var i=0;i<arr.length;i++){
		arr.splice(i,1,Math.pow(arr[i],2))
	}
	return arr;
}

/*第二种*/
function squareArr(arr){
	for(var i=0;i<arr.length;i++){
		arr[i]=Math.pow(arr[i],2);
	}
	return arr;
}

/*第三种*/
function squareArr(arr){
	var newArr =arr.map(function (n) {
		return n*n;
	})
	return newArr;
}

var arr = [2, 4, 6,8,10,12]
console.log(squareArr(arr));
```

## 写一个函数，操作数组，返回一个新数组，新数组中只包含正数，原数组不变

```
/*第一种，for循环从前往后*/
function filterPositive(arr){
	var newArr=[];
	newArr=arr.slice(0);
	for(var i=0;i<newArr.length;i++){
		if(!(typeof newArr[i] ==="number"&&newArr[i]>0)){
			newArr.splice(i,1);
			i--;
		}
	}
	return newArr;
}


/*第二种，for循环从后往前*/
function filterPositive(arr){
	var newArr=[];
	newArr=arr.slice(0);
	for(var i=newArr.length-1;i>=0;i--){
		if(!(typeof newArr[i] ==="number"&&newArr[i]>0)){
			newArr.splice(i,1);
		}
	}
	return newArr;
}

/*第三种filter*/
function filterPositive(arr){
	return arr.filter(function (item) {
	  return typeof item ==="number"&&item>0;
	})
}

var arr = [3, -1,  2,  'yoowin', true, false, 0, 0.1]
var newArr = filterPositive(arr)
console.log(newArr) //
```

# Date 任务

## 写一个函数getChIntv，获取从当前时间到指定日期的间隔时间


```
function getChIntv(time){
	/*日期格式化为去0日期，消除UTC时区影响*/
	var arr=time.split('-');
	arr.splice(0,3,parseInt(arr[0]),parseInt(arr[1]),parseInt(arr[2]));
	time =arr.join('-');

	var d1= new Date(time);
	var d2= new Date();
	var d =Math.abs(d2-d1);
	var days=parseInt(d/(1000*60*60*24));
	var hours=parseInt(d%(1000*60*60*24)/(1000*60*60));
	var minutes=parseInt(d%(1000*60*60)/(1000*60));
	var seconds=parseInt(d%(1000*60)/1000);
	if(d2>d1){
		return time+"已过去"+days+"天"+hours+"小时"+minutes+"分"+seconds+"秒";
	}else{
		return "距"+time+"还有"+days+"天"+hours+"小时"+minutes+"分"+seconds+"秒";
	}
}
var str = getChIntv("2017-10-01");
console.log(str);
```

## 把hh-mm-dd格式数字日期改成中文日期


```
function getChsDate(time){
	var arr=time.split('-');

	var year=arr[0];
	var month=arr[1];
	var day=arr[2];
	var dict=["零","一","二","三","四","五","六","七","八","九","十","十一","十二","十三","十四","十五","十六","十七","十八","十九","二十","二十一","二十二","二十三","二十四","二十五","二十六","二十七","二十八","二十九","三十","三十一"];
	year=dict[year[0]]+dict[year[1]]+dict[year[2]]+dict[year[3]];
	month=dict[parseInt(month)];
	day=dict[parseInt(day)];
	return year+"年"+month+"月"+day+"日"
}
getChsDate('2015-01-08');
```

## 写一个函数，参数为时间对象毫秒数的字符串格式，返回值为字符串。假设参数为时间对象毫秒数t，根据t的时间分别返回如下字符串:

刚刚（ t 距当前时间不到1分钟时间间隔）
3分钟前 (t距当前时间大于等于1分钟，小于1小时)
8小时前 (t 距离当前时间大于等于1小时，小于24小时)
3天前 (t 距离当前时间大于等于24小时，小于30天)
2个月前 (t 距离当前时间大于等于30天小于12个月)
8年前 (t 距离当前时间大于等于12个月)

```
function friendlyDate(time){
	var t=new Date().getTime();
	var timer=(t-time)/(1000*60);
	switch(true){
		case timer <1:
		alert("刚刚");
		break;

		case timer >=1 && timer <60:
		alert("3分钟前");
		break;

		case timer >=60 && timer <60*24:
		alert("8小时前");
		break;

		case timer >=60*24 && timer <60*24*30:
		alert("3天前");
		break;

		case timer >=60*24*30 && timer <60*24*30*12:
		alert("2个月前");
		break;

		default:
		alert("8年前");
		break;
	}
}
var str = friendlyDate( '1493876543647' ) 
var str2 = friendlyDate('1483941245793')
```