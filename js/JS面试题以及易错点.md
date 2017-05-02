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
 name: 'hunger', 
 sex: 'male', 
 age: 28 
}
for(b in obj)
{console.log(obj[b])}
//hunger male 28
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

    getInfo('饥人谷', 2, '男');
	//name:饥人谷
	//age:2
	//sex:男
	//['饥人谷', 2, '男']
	//name valley
	
	getInfo('小谷', 3);
	//name:小谷
	//age:3
	//sex:undefined
	//['小谷', 3]
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