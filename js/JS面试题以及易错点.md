# 运算符、运算符优先级

## 以下代码的输出结果是?为什么?

```
console.log(1+1);    
//2 数值相加

console.log("2"+"4");  
//24 字符串拼接

console.log(2+"4"); 
//24 数字和字符串相加等同于字符串相加

console.log(+"4");
//4 一元运算符转换为数值类型
```

## 以下代码的输出结果是?

```
var a = 1;  
a+++a;  //(a++)+a
typeof a+2;
// 输出"number2" typeof的优先级高
```

## 以下代码的输出结果是? 为什么

``` 
var a = 1;
 var b = 3;
 console.log( a+++b );
//4   
//a+++b等同于（a++）+b，a++结果还是自身，即1，所以最后结果为1+3，为4
```

## 遍历数组，把数组里的打印数组每一项的平方

``` 
var arr = [3,4,5]
for(i=0;i<arr.length;i++)
{console.log(Math.pow(arr[i], 2))
}
```

## 遍历 JSON, 打印里面的值

```
var obj = {
 name: 'yoowin', 
 sex: 'male', 
 age: 28 
}
for(b in obj)
{console.log(obj[b])}
//yoowin male 28
```

## 以下代码输出结果是? 为什么

```
var a = 1, b = 2, c = 3;
var val = typeof a + b || c >0
console.log(val) 
//结果为number2 
//优先级依次为：typeof a、>、+、||，
//即typeof a + b || (c >0)

var d = 5;
var data = d ==5 && console.log('bb')
console.log(data) 
//结果为undefined
//优先级依次为：==、&&、=，
//console.log('bb')是打印值，其返回值是undefined，并非其打印结果！！！
//即var data = {(d ==5) && console.log('bb')}   =>  var data = true&& undefined  =>  var data = undefined

var data2 = d = 0 || console.log('haha')
console.log(data2)
//结果为undefined  
//赋值运算符从右往左
//console.log('haha')是打印值，其返回值是undefined，并非其打印结果！！！
//即var data2 = {d = (0 || console.log('haha'))}  =>var data2 = {d = (0 || undefined)}   =>var data2 = d = undefined =>var data2 = undefined
 
var x = !!"Hello" + (!"world", !!"from here!!");
console.log(x) 
//结果为2
//括号里的数值作运算时，取最后一个逗号后的值
//var x = true + (false, true);  =>var x = 1+ (0, 1);   =>var x =1+1
```

# 函数和作用域链
## 求n!，用递归来实现

```
function num(n){
	if(n===1){
	return 1
	}
	return n*num(n-1)
}
num()
```
## 以下代码输出什么？

```
	function getInfo(name, age, sex){
		console.log('name:',name);
		console.log('age:', age);
		console.log('sex:', sex);
		console.log(arguments);
		arguments[0] = 'valley';
		console.log('name', name);
	}

    getInfo('paul', 2, '男');
	//name:paul
	//age:2
	//sex:男
	//['paul', 2, '男']
	//name valley
	
	getInfo('小苏', 3);
	//name:小苏
	//age:3
	//sex:undefined
	//['小苏', 3]
	//name valley
	
	getInfo('男');
	//name:男
	//age:undefined
	//sex:undefined
	//['男']
	//name valley
	
```
## 写一个函数，返回参数的平方和？

```
   function sumOfSquares(){
   }
   var result = sumOfSquares(2,3,4)
   var result2 = sumOfSquares(1,3)
   console.log(result)  //29
   console.log(result)  //10
```

```
	function sumOfSquares(){
		var num=0;
		for(var i=0;i<arguments.length;i++){
			num=Math.pow(arguments[i],2)+num;
		}
		return num;
	}
	var result = sumOfSquares(2,,4,5,7,8)
	console.log(result)
```
## 如下代码的输出？为什么

```
	console.log(a);//undefined,因为变量a的声明前置
	var a = 1;
	console.log(b);//报错，因为未声明a变量
```
## 如下代码的输出？为什么
```
	sayName('world');//hello world,因为函数声明的调用可以在声明之前可以
	sayAge(10);//报错，因为函数表达式的调用不能在声明前调用
	function sayName(name){
		console.log('hello ', name);
	}
	var sayAge = function(age){
		console.log(age);
	};
```
## 如下代码输出什么? 写出作用域链查找过程伪代码

```
	var x = 10
	bar() 
	function foo() {
		console.log(x)
	}
	function bar(){
		var x = 30
		foo()
	}
	//执行结果是10
	//调用foo时打印x是声明函数所在位置的打印，而不是调用位置！！
	//foo函数内部没找到x，然后找全局变量，找到x=10
```
## 如下代码输出什么? 写出作用域链查找过程伪代码

```
	var x = 10;
	bar() //30
	function bar(){
		var x = 30;
	function foo(){
		console.log(x) 
	}
	foo(); 
	}
	//执行结果是30
	//foo函数内部没找到x，然后往外找，找到x=30	
	
```
## 以下代码输出什么? 写出作用域链的查找过程伪代码

```
	var x = 10;
	bar() 
	function bar(){
		var x = 30;
	(function (){
		console.log(x)
	})()
	}
	//执行结果为30
	//调用bar时自执行函数打印的x在自己作用域中没找到，往外找就找到bar函数作用域中的x=30
```
## 以下代码输出什么？ 写出作用域链查找过程伪代码

```
var a = 1;

function fn(){
  console.log(a)//undefined  a声明的提升
  var a = 5
  console.log(a)//5  fn作用域中a被修改为5
  a++
  var a
  fn3()
  fn2()
  console.log(a)//20  fn2中的a=20是fn中的局部变量，调用fn2时修改了a的值

  function fn2(){
    console.log(a)//6  fn2内没找到a的声明，往外找找到变量a=6
    a = 20
  }
}

function fn3(){
  console.log(a)//1  fn3内没找到a的声明，找到全局变量a=1
  a = 200
}

fn()
console.log(a)//200  fn3中把全局变量a修改为200，fn2中的a=20是函数fn内的局部变量，不是全局变量

```

# 引用类型对象拷贝

## 引用类型有哪些？非引用类型有哪些
基本类型值（数值、布尔值、null和undefined）：指的是保存在栈内存中的简单数据段；
引用类型值（对象、数组、函数、正则）：指的是那些保存在堆内存中的对象，变量中保存的实际上只是一个指针，这个指针执行内存中的另一个位置，由该位置保存对象

## 如下代码输出什么？为什么

```
var obj1 = {a:1, b:2};
var obj2 = {a:1, b:2};
console.log(obj1 == obj2);//false  两个对象是占用的两个内存地址
console.log(obj1 = obj2); //a:1 b:2  把obj2的内存地址赋给obj1
console.log(obj1 == obj2);//true   obj1内存地址是obj2传递的，所以相等
```

## 如下代码输出什么? 为什么

```
var a = 1
var b = 2
var c = { name: 'yoowinsu', age: 2 }
var d = [a, b, c]

var aa = a
var bb = b
var cc = c
var dd = d

a = 11
b = 22
c.name = 'hello'
d[2]['age'] = 3

console.log(aa) //11 值传递
console.log(bb) //22 值传递
console.log(cc) //name: 'hello', age: 3  传址传递，只要改变此地址的参数，此对象的参数就会改变
console.log(dd) //[1,2,{name: 'hello', age: 3}]  d对象中的a、b是值传递，c是传址传递
```

## 如下代码输出什么? 为什么

```
var a = 1
var c = { name: 'yoowinsu', age: 2 }

function f1(n){
  ++n
}
function f2(obj){
  ++obj.age
}

f1(a)
f2(c) 
f1(c.age) 
console.log(a) 
//1  调用f1函数默认把a值传递给n，改变n的值a不受影响，所以打印结果还是1
console.log(c) 
//name: 'yoowinsu', age: 3 
//调用f2函数是传址传递， ++obj.age会改变age的值为3
//调用f1函数默认把c.age值传递给n，改变n的值c.age不受影响，所以打印结果还是3

## 过滤如下数组，只保留正数，直接在原数组上操作

var arr = [3,1,0,-1,-3,2,-5]
function filter(arr){
	for(var i=0;i<arr.length;i++){
		if(arr[i]<=0){
			arr.splice(i,1);
			i--;
		}
	}
}
filter(arr)
console.log(arr) // [3,1,2]
```

## 过滤如下数组，只保留正数，原数组不变，生成新数组

```
var arr = [3,1,0,-1,-3,2,-5]
function filter(arr){
	var newArr=[];
	for(var i=0;i<arr.length;i++){
		if(arr[i]>0){
			newArr.push(arr[i])
		}
	}
	return newArr;
}
var arr2 = filter(arr)
console.log(arr2) // [3,1,2]
console.log(arr)  // [3,1,0,-1,-2,2,-5]
```

# 字符串以及JSON
## 使用数组拼接出如下字符串

```
var prod = {
    name: '女装',
    styles: ['短款', '冬季', '春装']
};
function getTplStr(data){
	var str="<dl class=\"product\"><dt>"+data.name+"</dt><dd>"+data.styles[0]+"</dd><dd>"+data.styles[1]+"</dd><dd>"+data.styles[2]+"</dd></dl>"
	return str;
};
var result = getTplStr(prod);  //result为下面的字符串
console.log(result);
```
```
<dl class="product">
    <dt>女装</dt>
    <dd>短款</dd>
    <dd>冬季</dd>
    <dd>春装</dd>
</dl>
```

## 写出两种以上声明多行字符串的方法
- 字符串拼接

```
var a="ab"
+"cd"
+"ef";
```
- 转义

```
var a="ab \
cd \
ef";
```

## 补全如下代码,让输出结果为字符串: hello\\yoowin

```
var str = "hello\\\\yoowin"
console.log(str)
```

## 以下代码输出什么?为什么

```
var str = 'yoowinsu\nnice'
console.log(str.length)
//13
//\n是换行符，算一个字符，总共13个字符
```

## 写一个函数，判断一个字符串是回文字符串，如 abcdcba是回文字符串, abcdcbb不是

``
function test(str){
	if(str == str.split('').reverse().join('')){
		console.log(str+"字符串是回文字符串")
	}else{
		console.log(str+"字符串不是回文字符串")
	}
}
test("abcdcba")
test("abcdcbb")
```

## 写一个函数，统计字符串里出现出现频率最多的字符

```
function max(str){
  var obj={};
  for(var i=0;i<str.length;i++){
    if(obj[str[i]]){
      ++obj[str[i]];
    }else{
      obj[str[i]]=1;
    }
  }
  var max=0;
  var maxValue;
  for(var key in obj){
    if(obj[key]>max){
      max=obj[key];
      maxValue=key;
    }
  }
  console.log("出现频率最多的字符："+maxValue+"，出现次数："+max);
}
max("ssdcxzzzzzzzzz")
max("ssxzaaaa")
```

## 写一个camelize函数，把my-short-string形式的字符串转化成myShortString形式的字符串，如

```
function camelize(str){
  var arr=str.split('-')
  for(var i=1;i<arr.length;i++){
    arr[i] = arr[i].replace(arr[i].charAt(0),arr[i].charAt(0).toUpperCase());
  }
  var newStr=arr.join('');
  return newStr;
}
camelize("background-color") == 'backgroundColor' //true
camelize("list-style-image") == 'listStyleImage' //true
```


## 写一个 ucFirst函数，返回第一个字母为大写的字符 （***）

```
function ucFirst(str){
	var newStr = str.replace(str.charAt(0),str.charAt(0).toUpperCase());
	return newStr;
}
ucFirst("apple") == "Apple" //true
```

## 写一个函数truncate(str, maxlength), 如果str的长度大于maxlength，会把str截断到maxlength长，并加上...，如

```
function truncate(str, maxlength){
	if(str.length>maxlength){
		str=str.slice(0, maxlength)+"..."; 
	}
	return str;
}
truncate("hello, this is hunger valley,", 10) == "hello, thi...";
truncate("hello world", 20) == "hello world"
```
