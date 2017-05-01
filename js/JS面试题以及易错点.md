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