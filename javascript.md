### javascript

#### javascript变量

可变的量

##### 变量声明

- var 	  （ES3）
- function   （ES3）  创建函数（函数名也是变量，只不过存储的值是函数类型的而已）
- let      （ES6）与var相似
- const   （ES6）创建常量
- import   （ES6）基于es6的模块规范导出需要的信息
- class    （ES6）基于es6创建类

``` javascript
/*
*语法：
*var [变量名] = 值;
*let [变量名] = 值;
*const [变量名] = 值;
*function 函数名(){}
*/
var a = 3;

function mySum(sum1,sum2){
  return sum1+sum2;
}

```

##### 变量命名规范

- 区分大小写：变量、函数名、运算符以及其他一切东西都是区分大小写的。比如：变量test与变量TEST是不同的。

```javascript
var a = 12;
var A = 12;//两个变量不一样
```

- 驼峰命名：首字母是小写的，接下来的字母都以大写字符开头

  第一个字符必须是字母、下划线（_）或美元符号（$）

  余下的字符可以是下划线、美元符号或任何字母或数字字符

  ```javascript
  var myTestValue = 0;
  ```

- 不能有关键字与保留字：有特殊含义的叫关键字，未来有可能成为关键字的叫保留字

----

#### 数据类型

##### 基本数据类型（值类型）

- Number   数字


- String  字符串
- Null  空
- Undefined 未定义
- Boolean  布尔

```javascript
[基本数据类型]
var n = 12；//NaN（not a number:不是一个数字，但是它是一个特殊的numer类型）

字符串
var a = '';

布尔
var c = true//只有两个值  true 真与false 假

```



##### 引用数据类型

- 对象object
  + 普通对象
  + 数组对象
  + 数学对象
  + 日期对象
  + ......
- 函数function

```javascript
[引用数据类型]
普通对象：
var o = {name:"丁会想",age:21}

数组对象：
var arr = [12,2,22]


```



##### ES6新加的数据类型：symbol

创建出来的是惟一的值

```javascript
var a = Symbol("dinghuixiang");
var b = Symbol("dinghuixiang");
a==b;//false,a与b不相等
```

##### 扩展：js代码如何运行以及运行后如何输出结果

[如何被运行]

- 把代码运行在浏览器中（浏览器内核来渲染解析）
- 基于node来运行（node也是一个基于v8引擎渲染与解析ja的工具）

[如何输出结果]

- alert：弹窗，基于alert输出的结果都会转化为字符串
- console.log
- console.dir

##### 类型的详解

- number数字类型
  + NaN：not a number   但它是数字类型，NaN和谁都不相等
  + isNaN：检测当前值是否不是有效数字，返回false代表是有效数字，返回true代表不是有效数字

```javascript
var num = 12
isNaN(num)//false
isNaN('12')//false
isNaN('丁')//true
isNaN(true)//false
isNaN(false)//false
isNaN(null)//false
isNaN(undefined)//true
isNaN({age:2})//true
isNaN([12,230])//true
isNaN([12])//false
isNaN(function(){})//true

isNaN检测机制：
1、验证当前的需要检测的值是否为数字类型，如果不是，浏览器会默认的把值转化为数字类型

	-其他类型转数字：直接使用Number（）

    Number(true)//1
	Number(false)//0
	Number(null)//0
	Number(undefined)//NaN
    
    -把引用数据类型转化为数字：先用toString转化为字符串，在Number转化为数字
    
	parseFloat()	解析一个字符串，并返回一个浮点数。
	parseInt()	解析一个字符串，并返回一个整数。
2、当前检测的值已经是数字类型，是有效数字返回false，不是返回true
（数字类型中只有nan不是有效数字，其余都是）

```



- 字符串
- 布尔类型

> 只有两个值：true/false

如何将其他数据转换为布尔类型

-  Boolean
- ！
- !!

```javascript
Boolean()
!'丁会想'//先把其他数据类型转换为布尔类型，然后取反
!!'丁会想'//取两次反，等价于没取反（一般使用）
规律：`在js中只用0/NaN/null/undefined/空字符串，转化为布尔为false，其余为true`
```

- null与undefined

> 都代表空或没有
>
> - null：空对象指针
> - undefined：未定义

null：在 JavaScript 中 null 表示 "什么都没有"，是一个只有一个值的特殊类型，表示一个空对象引用

```javascript
var person = null; // 值为 null(空), 但类型为对象
//是手动控制的，于是后面会为其赋值
```

undefined:在 JavaScript 中 undefined 是一个没有设置值的变量。

```javascript
var person; // 值为 undefined(空), 类型是undefined  未定义
//
```

---

##### 对象数据类型

> 普通对象
>
> - 有大括号包裹起来的
> - 由零个到多个属性名与属性值（键值对）组成

` 属性是用来描述当前对象的特征的 `

属性为[key]

` 属性名为[value]`

```javascript
var obj = {
  name:'dinghuixiang',
  age:21
}
//对象的操作

[获取]
语法：对象.属性名/对象[属性名]
obj.name
obj['name'] :一般来说属性名是字符串格式的

[增/改]
在js对象（同一对象中）中属性名是不可以重复的，是惟一的
obj.name = 'ding-mouren';//=>修改name属性
obj.sex = '男';//增加sex属性

[删]
彻底删除:对象不存在此属性
delete obj['age'];

假删除：并没有删除这个属性，只是让当前属性的值为空
obj.sex = null;

```



---









