### ES6
ES5中有两种变量声明方法：var、function
ES6中六种变量声明方法：
- var：
- function：
- let：
- const：
- import：
- class：

#### let与const命令

##### let命令

> 定义变量：
>
> ES5：ver，function
>
> ES6：let，const

- 基本语法：

  `let 变量名 = 值;`

- 特性：
  1.let使用let声明的变量只在代码块中有效
  ```javascript
  {
    let a = 4;
    var a = 5;
  }
  console.log(a);//
  console.log(b);//
  ```
  2.let没有变量提升：先声明，再使用
  ```javascript
  let a = 5;
  console.log(a)//正常输出

  console.log(b);//报错
  let b = 5;
  ```
  3.let不能重复定义：let不允许在相同的作用域内重复声明一个变量
  ```javascript
  let a = 5;
  let a = 5;
  console.log(a);//报错
  ```
  4.暂时性死区
  5.let定义的变量不会作为window的属性
#####块级作用域
  - 全局作用域
  - 局部作用域
  - 块级作用域：
    ```javascript
    {
    let a = 4;
    //console.log(a);// 4
    }
    console.log(a);//报错，块级作用域   
    ```
#####let与var的比较：
```javascript
var a = [];
    for (var i = 0; i < 10; i++) {
      a[i] = function () {
      console.log(i);
      };
    }
    a[6](); // 输出10
    // 变量i是var命令声明的，在全局范围内都有效，所以全局只有一个变量i
    var c = [];
      for (let n = 0; n < 10; n++) {
        c[n] = function () {
        console.log(n);
        };
      }
    c[6](); // 6
    // 变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量，所以最后输出的是6


    // for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。
    for (let i = 0; i < 3; i++) {
    let i = 'abc';
    console.log(i);
    }//输出三次abc
    //abc
    //abc
    //abc
```


##### const命令
- 基本语法：
  `const 变量名 = 值;`
  -特性：
  1.只能声明一个只读的变量：是一个常量，一旦声明就不能修改,`常量一般首字母大写`
  ```javascript
  // const声明一个只读的常量。一旦声明，常量的值就不能改变。
      // const声明的变量不得改变值，这意味着，const一旦声明变量，就必须立即初始化，不能留到以后赋值。
      // 对于const来说，只声明不赋值，就会报错
      const a;//报错
      const PI = 3.1415;
      PI // 3.1415
      PI = 3;
      // 上面代码表明改变常量的值会报错。
  ```
  1. 对于const来说，只声明不赋值，就会报错
  ```javascript
  const a;//报错
  ```
  3.const一旦声明变量，就必须立即初始化，不能留到以后赋值。
  ```javascript
  PI // 3.1415
      PI = 3;
      // 上面代码表明改变常量的值会报错。
  ```
  4.其他与let一样
  `注意：const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动`
  ```javascript
  const foo = {};
    // 为 foo 添加一个属性，可以成功
    foo.prop = 123;
    foo.prop // 123
    // 将 foo 指向另一个对象，就会报错
    foo = {}; // TypeError: "foo" is read-only
    // 上面代码中，常量foo储存的是一个地址，这个地址指向一个对象。
    // 不可变的只是这个地址，即不能把foo指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性

    const a = [];
    a.push('Hello'); // 可执行
    a.length = 0;    // 可执行
    a = ['Dave'];    // 报错
    // 上面代码中，常量a是一个数组，这个数组本身是可写的，但是如果将另一个数组赋值给a，就会报错。
  ```

注意：`使用let、const、class声明的全局变量，不属于顶层对象的属性`
顶层对象：浏览器中是window对象，在node中是global对象

#### 结构赋值

- 这被称为解构（Destructuring）。
  ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。
##### 数组的结构
  ```javascript
  // 以前，为变量赋值，只能直接指定值。
    // let a = 1;
    // let b = 2;
    // let c = 3;
    
    // ES6 允许写成下面这样。
    let [a,b,c] = [1,2,3];
    console.log(a,b,c);
  ```
- 本质上，这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。
  如果解构不成功变量的值就等于`undefined`
```javascript
let [foo, [[bar], baz]] = [1, [[2], 3]];
    foo // 1
    bar // 2
    baz // 3

    let [ , , third] = ["foo", "bar", "baz"];
    third // "baz"

    let [x, , y] = [1, 2, 3];
    x // 1
    y // 3

    let [head, ...tail] = [1, 2, 3, 4];
    head // 1
    tail // [2, 3, 4]

    let [x, y, ...z] = ['a'];
    x // "a"
    y // undefined
    z // []
```
- 完全结构

 ```javascript
  let [a,b,c] = [1,2,3];
    console.log(a,b,c);
 ```
- 不完全结构

 ```javascript
  let [a,b] = [1,2,3];
  console.log(a,b,c);//c=undefined
 ```
##### 对象的结构
- 对象解构的要求：变量名与对象的属性名保持一致

  ```javascript
  var obj={
    name:'dhx',
    age:21,
    addr:'井冈山'
  }
  let {a,b,c}=obj;
  console.log(a,b,c);//undefined

  //对象解构的要求：变量名与对象的属性名保持一致

  let {name,age,addr}=obj;//顺序不需要一致，对象属性没有次序的
  console.log(name,age,addr);

  ```
  ##### 不完全解构
  ```javascript
  let data={
    id:12,
    imgSrc:'http://dfdsfsf.jps',
    title:'海贼王'，
    URL:'http://dfdsfsf.html',
    time:'2019-9-20'
  };
  let {imgSrc,title}=data;
  consile.log(imgSrc,title);
  ```
##### 字符串解构
- 模式：
  ```javascript
  let str = 'hello';
  let [a,b,c,d,e]=str;//完全解构
  console.log(a,b,c,d,e);
  //不完全解构
  //h
  //e
  //l
  //l
  //o
  ```
- 应用：

  ```javascript
  let a = 10;
  let b = 5;
  //不定义第三个变量，交换a，b的值
  //普通方法
  a=a+b;
  b=a-b;//10
  a=a-b;
  console.log(a,b);

  //使用解构
  [b,a]=[a,b];
  console.log(a,b);

  function show(){
    //let arr=[100,200,300];
    //return arr;

    //return [100,200,300];

    return {
      name:'dhx',
      age:21,
      grade:'大四'
    };
  }

  //let a=show();

  //let [a,b,c]=show();
  //console.log(a,b,c);

  let {name,age}=show();
  console.log(name,age);
  ```
##### 参数的解构

#### 箭头函数

  ES6 允许使用“箭头”（=>）定义函数。

##### 基本语法：

  ```javascript
    var f = v => v;

    // 等同于
    var f = function (v) {
      return v;
    };
  ```
- 无参数函数
  ```javascript
    var f = () => {
      console.log('dinghuixiang');
    };

    // 等同于
    var f = function () {
      console.log('dinghuixiang');
    };
    f();
  ```
- 有一个参数函数
  ```javascript
    var f = v => {
      console.log('dinghuixiang');
    };

    // 等同于
    var f = function (v) {
      console.log('dinghuixiang');
    };
    f();
  ```
- 有多个参数函数
  ```javascript
    var f = (a,b) => {
      console.log('dinghuixiang');
    };

    // 等同于
    var f = function (a,b) {
      console.log('dinghuixiang');
    };
    f();
  ```
- 函数内只有一个返回语句
  ```javascript
    var f = () => v;

    // 等同于
    var f = function () {
      return v;
    };
    f();
  ```
- 函数内只有多个语句
  ```javascript
    var f = () =>{
      console.log('dinghuixiang');
      return v;
    } ;

    // 等同于
    var f = function () {
      console.log('dinghuixiang');
      return v;
    };
    f();
  ```
- 函数内只有一个语句，但不是返回语句，也可以（使用void关键字）
  ```javascript
    var f = () =>void console.log('dinghuixiang');
  
    // 等同于
    var f = function () {
      console.log('dinghuixiang');
    };
    f();
  ```
- 特殊情况：如果箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用return语句返回。由于大括号被解释为代码块， `所以如果箭头函数直接返回一个对象，必须在对象外面加上括号，否则会报错`
  ```javascript
  // 报错
  let getTempItem = id => { id: id, name: "Temp" };

  // 不报错
  let getTempItem = id => ({ id: id, name: "Temp" });
  ```
  + 下面是一种特殊情况，虽然可以运行，但会得到错误的结果。
  ```javascript
  let foo = () => { a: 1 };
  foo() // undefined
  ```
  上面代码中，原始意图是返回一个对象`{ a: 1 }`，但是由于引擎认为大括号是代码块，所以执行了一行语句`a: 1`。这时，`a`可以被解释为语句的标签，因此实际执行的语句是`1`;，然后函数就结束了，没有返回值

##### 箭头函数：省略function，总结
  + 参数个数：
    - 一个参数：可以省略()
    - 多个参数：不能省略()
  + 函数体语句：

    - 一条语句：

      + return语句：省略大括号{}与return
      + 普通语句：可以只用void指令省略

    - 多条语句：不能省略

##### 注意事项
  箭头函数有几个使用注意点。

  （1）函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。

  （2）不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。

  （3）不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

  （4）不可以使用yield命令，因此箭头函数不能用作 Generator 函数。

  上面四点中，第一点尤其值得注意。this对象的指向是可变的，但是在箭头函数中，它是固定的。
  
  

#### ES6中的类与对象

##### 类与对象的创建

##### 类的继承

