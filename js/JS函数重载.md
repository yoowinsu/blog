# 重载是什么
重载是很多面向对象语言实现多态的手段之一，在C#和JAVA等编程语言中函数重载是指在一个类中可以定义多个方法名相同但是方法参数和顺序不同的方法，以此来实现不同的功能和操作，这就是重载。
# JavaScript函数没有重载
JavaScript函数不能像传统意义上那样实现重载。因为在JavaScript函数中通过名字确定唯一性，参数不同也被认为是相同的函数，后面的函数覆盖前面的函数。如下例：

```
function addNum(num){
	num+=10;
	return num;
}
function addNum(num){
	num+=100;
	return num;
}
addNum(3); //103 
```

但是我们可以模拟重载。
# 如何实现函数/方法重载

- 通过if条件判断参数是否存在

```
function printPeopleInfo(name, age, sex){
    if(arguments[0]){
        console.log(name);
    }

    if(arguments[1]){
        console.log(age);
    }

    if(arguments[2]){
        console.log(sex);
    }
}

printPeopleInfo('Byron', 26);//Byron 26
printPeopleInfo('Byron', 26, 'male');//Byron 26 male
```

- 通过arguments对象，去判断函数的参数个数
```
function printPeopleInfo(name, age, sex){
    if(arguments.length==1){
        console.log('名字是'+name+',没有年龄和性别的信息');
    }else if(arguments.length==2){
        console.log(name+'今年'+age+'岁了');
    }else if(arguments.length==3){
        console.log(name+'今年'+age+'岁了，是个'+sex+'生');
    }
}

printPeopleInfo('lebron');//名字是lebron,没有年龄和性别的信息
printPeopleInfo('Byron', 26);//Byron今年26岁了
printPeopleInfo('yoowin', 25,'男');//yoowin今年25岁了，是个男生
```

   
**开发人员定义的函数都可以接受任意个数的参数（根据NetScript 文档，最多能接受25个） ，而不会引发错误，任何遗漏的参数都会用undefined 代替，多余的参数被将忽略。**