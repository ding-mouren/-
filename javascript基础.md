### javascript基础

#### javascript用法：

##### <script> 标签：

如需在 HTML 页面中插入 JavaScript，请使用 <script> 标签。

1. <script> 和 </script> 会告诉 JavaScript 在何处开始和结束。
2. <script> 和 </script> 之间的代码行包含了 JavaScript。

```javascript
<script>
    alert("我的第一个 JavaScript");
</script>
```

浏览器会解释并执行位于 <script> 和 </script>之间的 JavaScript 代码 

注意：那些老旧的实例可能会在 <script> 标签中使用 type="text/javascript"。现在已经不必这样做了。JavaScript 是所有现代浏览器以及 HTML5 中的默认脚本语言。

##### javascript脚本所在位置：

###### <body> 中的 JavaScript：

```javascript
<!DOCTYPE html>
<html>
<head>
 	<meta charset="utf-8"> 
  	<title>body标签你的javascript</title> 
<body>
	<h1>我的 Web 页面</h1>
	<p id="demo">一个段落</p>
	<button type="button" onclick="myFunction()">尝试一下</button>

	<script>
		function myFunction()
		{
			document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
		}
	</script>

</body>
</head>
</html>
```



###### <head> 中的 JavaScript：

```javascript
<!DOCTYPE html>
<html>
<head>
  	<meta charset="utf-8"> 
    <title>head标签内的javascript</title> 
	<script>
	function myFunction()
	{
		document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
	}
	</script>
</head>
<body>
	<h1>我的 Web 页面</h1>
	<p id="demo">一个段落</p>
	<button type="button" onclick="myFunction()">尝试一下</button>
</body>
</html>
```



###### 外部的 JavaScript：

也可以把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码。（开发中建议使用）

1. 外部 JavaScript 文件的文件扩展名是 .js。
2. 如需使用外部文件，请在 <script> 标签的 "src" 属性中设置该 .js 文件：
3. 外部脚本不能包含 <script> 标签。

```javascript
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8"> 
	<title>外部javascript</title>
    <script src="myScript.js"></script>
<body>
</body>
</head>
</html>
```



#### JavaScript 输出：

JavaScript 没有任何打印或者输出的函数。

JavaScript 可以通过不同的方式来输出数据：

1. 使用 **window.alert()** 弹出警告框。
2. 使用 **document.write()** 方法将内容写到 HTML 文档中。
3. 使用 **innerHTML** 写入到 HTML 元素。
4. 使用 **console.log()** 写入到浏览器的控制台。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>原生javascript</title>
</head>
<body>
    <p id="demo1">第一个段落</p>
    <button onclick="myFunction()">点击</button>
    <script>
        // 弹出警告框
        alert("Hello Javascript");
        /*
         使用 document.write() 方法将内容写到 HTML 文档中。
         请使用 document.write() 仅仅向文档输出写内容。
         如果在文档已完成加载后执行 document.write，整个 HTML 页面将被覆盖。
        */
        document.write("Hello javascript");
        // 写在控制台
        /*
        console.log() 方法能够让你看到你在页面中的输出内容，让你更容易调试javascript；
        与alert相比，console不会打断你页面的操作，console里面的内容非常丰富，你可以在控制台输入 console。
        程序中调试是测试，查找及减少bug(错误)的过程。
        */
        console.log("Hello Javascript");
        // 操作HTML元素
        document.getElementById('demo1').innerHTML="段落已修改";
        function myFunction(){
            document.getElementById('demo1').innerHTML="段落又已修改";
        }
    </script>
</body>
</html>
```



#### javascript注释

JavaScript 不会执行注释。

我们可以添加注释来对 JavaScript 进行解释，或者提高代码的可读性。

- 单行注释以 // 开头。
- 多行注释以 /* 开始，以 */ 结尾。

#### javascript变量：

变量是用于存储信息的"容器"，您可以把变量看做存储数据的容器。

##### 变量命名规范：

1. 变量必须以字母开头，后面有英文字母、数字、下划线组成
2. 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做）
3. 变量名称对大小写敏感（y 和 Y 是不同的变量）
4. 使用驼峰命名法：第一个单词首字母小写，其他首字母大写

JavaScript 语句和 JavaScript 变量都对大小写敏感。

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

---



##### 变量声明：

在 JavaScript 中创建变量通常称为"声明"变量。

我们使用 var 关键词来声明变量并赋值。

```javascript
var x = 15;   
var y = 16;
var z = x+y;
您可以在一条语句中声明很多变量。该语句以 var 开头，并使用逗号分隔变量即可
var lastname="Doe", age=30, job="carpenter";
```

- var 	  （ES3）
- function   （ES3）  创建函数（函数名也是变量，只不过存储的值是函数类型的而已）
- let      （ES6）与var相似
- const   （ES6）创建常量
- import   （ES6）基于es6的模块规范导出需要的信息
- class    （ES6）基于es6创建类

```javascript
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



#### javascript数据类型：

##### 基本数据类型

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



1. 字符串（String）、

   字符串是存储字符（比如 "Bill Gates"）的变量。

   字符串可以是引号中的任意文本。您可以使用单引号或双引号

   **规则:**如果把数字与字符串相加，结果将成为字符串！

   ```javascript
   var carname="Volvo XC60";
   var carname='Volvo XC60';
   x=5+5;  
   y="5"+5; 
   z="Hello"+5;
   10 
   55 
   Hello5
   ```

 2.数字(Number)、

 3.布尔(Boolean)、

   布尔（逻辑）只能有两个值：true 或 false。

```javascript
var x=true;
var y=false;
布尔常用在条件测试中
```

4. 数组(Array)、

   ```javascript
    var cars=new Array();
    cars[0]="Saab";
    cars[1]="Volvo";
    cars[2]="BMW";
   或者
   var cars=new Array("Saab","Volvo","BMW");
   数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。
   ```

5. 对象(Object)、

   对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (key : value) 来定义。属性由逗号分隔

   ```javascript
   var person={firstname:"John", lastname:"Doe", id:5566};
   或许
    var person={
    firstname : "John",
    lastname  : "Doe",
    id        :  5566
    };
   ```

6. 空（Null）、

7. 未定义（Undefined）。

JavaScript 拥有动态类型。这意味着相同的变量可用作不同的类型：

```javascript
var x;               // x 为 undefined
var x = 5;           // 现在 x 为数字
var x = "John";      // 现在 x 为字符串
```

##### 引用数据类型

- 对象object
  - 普通对象
  - 数组对象
  - 数学对象
  - 日期对象
  - ......
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
  - NaN：not a number   但它是数字类型，NaN和谁都不相等
  - isNaN：检测当前值是否不是有效数字，返回false代表是有效数字，返回true代表不是有效数字

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

- Boolean
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

------

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



------



#### javascript函数

##### 函数语法

函数就是包裹在花括号中的代码块，前面使用了关键词 function：

```javascript
function functionname()
 {
	执行代码
 }
```

**JavaScript 对大小写敏感。关键词 function 必须是小写的，并且必须以与函数名称相同的大小写来调用函数。**

**function 中的花括号是必需的，即使函数体内只包含一条语句，仍然必须使用花括号将其括起来。**

##### 函数定义

JavaScript 使用关键字 **function** 定义函数。

函数可以通过声明定义，也可以是一个表达式。

1. 函数声明

```javascript
<p>本例调用的函数会执行一个计算，然后返回结果：</p>
<p id="demo"></p>
<script>
function myFunction(a,b){
	return a*b;
}
document.getElementById("demo").innerHTML=myFunction(4,3);
</script>

```

函数声明后不会立即执行，会在我们需要的时候调用到。

2.函数表达式

```javascript
<p>函数存储在变量后，变量可作为函数使用：</p>
<p id="demo"></p>
<script>
var x = function (a, b) {return a * b};
document.getElementById("demo").innerHTML = x(4, 3);
</script>
```

以上函数实际上是一个 **匿名函数** (函数没有名称)。

函数存储在变量中，不需要函数名称，通常通过变量名来调用。

上述函数以分号结尾，因为它是一个执行语句。

3.Function() 构造函数

```javascript
<p>JavaScrip 内置构造函数。</p>
<p id="demo"></p>
<script>
var myFunction = new Function("a", "b", "return a * b");
document.getElementById("demo").innerHTML = myFunction(4, 3);
</script>

```

在 JavaScript 中，很多时候，你需要避免使用 **new** 关键字。

实际上，你不必使用构造函数。上面实例可以写成

```javascript
<p id="demo"></p>
<script>
var myFunction = function (a, b) {return a * b}
document.getElementById("demo").innerHTML = myFunction(4, 3);
</script>

```

#### javascript作用域

作用域是可访问变量的集合。

1. 在JavaScript中，能够定义全局作用域或者局部作用域。
2. 在 JavaScript 中, 对象和函数同样也是变量。
3. **在 JavaScript 中, 作用域为可访问变量，对象，函数的集合。**
4. JavaScript 函数作用域: 作用域在函数内修改。

##### javascript局部作用域

变量在函数内声明，变量为局部作用域。

局部变量：只能在函数内部访问。

因为局部变量只作用于函数内，所以不同的函数可以使用相同名称的变量。

局部变量在函数开始执行时创建，函数执行完后局部变量会自动销毁

```javascript
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>W3Cschool教程(w3cschool.cn)</title> 
</head>
<body>

<p>局部变量在声明的函数内可以访问。</p>
<p id="demo"></p>
<script>
myFunction();
document.getElementById("demo").innerHTML =
	"我可以显示 " +  typeof carName;
function myFunction() 
{
    var carName = "Volvo";
}
</script>

</body>
</html>   
//
显示
//

局部变量在声明的函数内可以访问。

我可以显示 undefined
```

##### javascript全局作用域

变量在函数外定义，即为全局变量。

全局变量有 **全局作用域**: 网页中所有脚本和函数均可使用。 

```javascript
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>W3Cschool教程(w3cschool.cn)</title> 
</head>
<body>

<p>全局变量在任何脚本和函数内均可访问。</p>
<p id="demo"></p>
<script>
var carName = "Volvo";
myFunction();
function myFunction() 
{
    document.getElementById("demo").innerHTML =
		"我可以显示 " + carName;
}
</script>

</body>
</html>
//
显示
//
全局变量在任何脚本和函数内均可访问。

我可以显示 Volvo
```



##### javascript作用域生命周期

- JavaScript 变量生命周期在它声明时初始化。
- 局部变量在函数执行完毕后销毁。
- 全局变量在页面关闭后销毁。

##### 函数参数

函数参数只在函数内起作用，是局部变量。



#### 注意

你的全局变量，或者函数，可以覆盖 window 对象的变量或者函数。 
局部变量，包括 window 对象可以覆盖全局变量和函数。

在 ES6 中，提供了 let 关键字和 const 关键字。

let 的声明方式与 var 相同，用 let 来代替 var 来声明变量，就可以把变量限制在当前代码块中。

使用 const 声明的是常量，其值一旦被设定便不可被更改。

#### javascript事件

事件是可以被 JavaScript 侦测到的行为。

```javascript
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>W3Cschool教程(w3cschool.cn)</title> 
</head>
<body>

<p>点击按钮执行 <em>displayDate()</em> 函数.</p>
<button onclick="displayDate()">点我</button>

<script>
function displayDate()
{
	document.getElementById("demo").innerHTML=Date();
}
</script>
<p id="demo"></p>

</body>
</html>
```

#### javascript字符串

JavaScript 字符串用于存储和处理文本。

##### 字符串属性

| 属性          | 描述            |
| ----------- | ------------- |
| constructor | 返回创建字符串属性的函数  |
| length      | 返回字符串的长度      |
| prototype   | 允许您向对象添加属性和方法 |



##### 字符串方法

| Method              | 描述                                       |
| :------------------ | :--------------------------------------- |
| charAt()            | 返回指定索引位置的字符                              |
| charCodeAt()        | 返回指定索引位置字符的 Unicode 值                    |
| concat()            | 连接两个或多个字符串，返回连接后的字符串                     |
| fromCharCode()      | 将指定的 Unicode 值转换为字符串                     |
| indexOf()           | 返回字符串中检索指定字符第一次出现的位置                     |
| lastIndexOf()       | 返回字符串中检索指定字符最后一次出现的位置                    |
| localeCompare()     | 用本地特定的顺序来比较两个字符串                         |
| match()             | 找到一个或多个正则表达式的匹配                          |
| replace()           | 替换与正则表达式匹配的子串                            |
| search()            | 检索与正则表达式相匹配的值                            |
| slice()             | 提取字符串的片断，并在新的字符串中返回被提取的部分                |
| split()             | 把字符串分割为子字符串数组                            |
| substr()            | 从起始索引号提取字符串中指定数目的字符                      |
| substring()         | 提取字符串中两个指定的索引号之间的字符                      |
| toLocaleLowerCase() | 根据主机的语言环境把字符串转换为小写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
| toLocaleUpperCase() | 根据主机的语言环境把字符串转换为大写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
| toLowerCase()       | 把字符串转换为小写                                |
| toString()          | 返回字符串对象值                                 |
| toUpperCase()       | 把字符串转换为大写                                |
| trim()              | 移除字符串首尾空白                                |
| valueOf()           | 返回某个字符串对象的原始值                            |

#### javascript高级





### ES6

#### let与const命令

##### let命令



#### promise函数

##### 介绍与基本使用

promise：异步编程的一种解决方案，更加优雅的方式来进行异步操作

//sync:同步

//async：异步

异步操作之后有三种状态：

1、pending：等待  

2、fulfill：满足   主动回调resolve函数时，就处于这种状态，并会回调.then（）函数

3、reject：拒绝  主动回调reject函数时，就处于这种状态，并会回调.catch（）函数

##### 基本语法

第一种：

```javascript
//什么时候使用promise，一般是有异步操作时，使用promise对这个异步操作进行封装	
		//new -> 构造函数(1、保存状态信息，2、执行传入函数)
		new Promise((resolve,reject) => {
			setTimeout(() => {
				//网络请求成功
				// resolve("dinghuixiang")
				//网络请求失败
				reject("error message")
			},1000)
		}).then((data) => {//处理成功
			//处理代码
			console.log(data);
		}).catch((err) => {//处理失败
			console.log(err);
		})
```

第二种：

```javascript
//什么时候使用promise，一般是有异步操作时，使用promise对这个异步操作进行封装	
			//new -> 构造函数(1、保存状态信息，2、执行传入函数)
			new Promise((resolve,reject) => {
				setTimeout(() => {
					//网络请求成功
					// resolve("dinghuixiang")
					//网络请求失败
					reject("error message")
				},1000)
			}).then((data) => {//处理成功
				//处理代码
				console.log(data);
			},(err) => {//处理失败
				console.log(err);
			})
```



实例以及简写：

```javascript
		//网络请求:aaa 
		//处理:bbb111
		//处理:bbb222
		new Promise((resolve,reject) => {
			setTimeout(() => {
				resolve("aaa")
			},1000)
		}).then(res => {
			console.log(res);
			return new Promise((resolve,reject) => {
				// resolve(res+"111");//成功
				reject("error message")//失败
			})
		}).then(res => {
			console.log(res);
			return new Promise((resolve,reject) => {
				resolve(res+"222");
			})
		}).then(res => {
			console.log(res);
		}).catch(err => {
			console.log(err);
		})

// 	new Promise((resolve,reject) => {
// 		setTimeout(() => {
// 			resolve("aaa")
// 		},1000)
// 	}).then(res => {
// 		console.log(res);
// 		return Promise.resolve(res+"111")
// 	}).then(res => {
// 		console.log(res);
// 		return Promise.resolve(res+"222")
// 	}).then(res => {
// 		console.log(res);
// 	})

// 	new Promise((resolve,reject) => {
// 		setTimeout(() => {
// 			resolve("aaa")
// 		},1000)
// 	}).then(res => {
// 		//自己处理代码
// 		console.log(res);
// 		return (res+"111")
// 	}).then(res => {
// 		console.log(res+"第二层");
// 		return (res+"222")
// 	}).then(res => {
// 		console.log(res+"第三次");
// 	})
```

