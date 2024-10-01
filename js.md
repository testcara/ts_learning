# Javascript Basics

- [Javascript Basics](#javascript-basics)
  - [改变 HTML 内容](#改变-html-内容)
  - [改变 HTML 属性](#改变-html-属性)
  - [改变 HTML 样式 (CSS)](#改变-html-样式-css)
  - [隐藏 HTML 元素](#隐藏-html-元素)
  - [显示 HTML 元素](#显示-html-元素)
  - [代码位置](#代码位置)
  - [显示方案](#显示方案)
  - [命名](#命名)
  - [作用域](#作用域)
  - [const](#const)
  - [set](#set)
  - [map](#map)
  - [对象](#对象)
  - [事件](#事件)
  - [字符串方法](#字符串方法)
  - [数组方法](#数组方法)
  - [Date](#date)
  - [Math](#math)
  - [流程控制(condition, loop)](#流程控制condition-loop)
  - [use strict](#use-strict)
  - [this 关键词](#this-关键词)
  - [ES6](#es6)
  - [箭头函数](#箭头函数)
  - [类](#类)
  - [模块](#模块)
  - [导出](#导出)
  - [导入](#导入)
  - [call](#call)
  - [apply](#apply)
  - [闭包](#闭包)
  - [回调函数](#回调函数)
  - [promise](#promise)
  - [async \& await](#async--await)
  - [样式指南](#样式指南)
  - [最佳实践](#最佳实践)

## 改变 HTML 内容

```javascript
document.getElementById("demo").innerHTML = "Hello JavaScript";
```

##  改变 HTML 属性

```javascript
<button onclick="document.getElementById('myImage').src='/i/eg_bulboff.gif'">关灯</button>
```

## 改变 HTML 样式 (CSS)

```javascript
document.getElementById("demo").style.fontSize = "25px";
```

## 隐藏 HTML 元素

```javascript
document.getElementById("demo").style.display="none";
```

## 显示 HTML 元素

```javascript
document.getElementById("demo").style.display="block";
```

## 代码位置

必须位于```<script>``` 与 ```</script>``` 标签之间

```javascript
<script>
document.getElementById("demo").innerHTML = "我的第一段 JavaScript";
<button type="button" onclick="myFunction()">试一试</button>
function myFunction() {
   document.getElementById("demo").innerHTML = "第二段JavaScript";
}
</script>
// 当前页面
<script src="myScript1.js"></script>
// 外部网站
<script src="https://www.w3school.com.cn/js/myScript1.js"></script>
// 位于当前网站上指定文件夹中
<script src="/js/myScript1.js"></script>
```

## 显示方案

```javascript
// 使用 innerHTML 写入 HTML 元素
document.getElementById("demo").innerHTML = 5 + 6;
// 用 document.write() 写入 HTML 输出
document.write(5 + 6);
// 使用 window.alert() 写入警告框
window.alert(5 + 6);
// 使用 console.log() 写入浏览器控制台
console.log(5 + 6);
```

## 命名

- 命名不能使用连字符。它是为减法预留的, 如```first-name```
- 命令倾向于用驼峰式大小写```FirstName```和```firstName```，后者更常用
- 大小写敏感，只能包含数字，字母，下划线和$，但是数字不能作为开头

## 作用域

```javascript
// 全局（在函数之外）声明的变量拥有全局作用域
// 全局变量， var和x没有区别
var x = 1
let x = 1 // 同一作用域不能用let重复声明同一变量

// 块作用域
{
    console.log(x); // 1
    // let声明块作用域，块外部不能访问
    let y = 0;
    // 通过 var 关键词声明的变量没有块作用域
    var x = 2;
}

console.log(x) // 2

// 函数作用域, var和let也没区别，只能函数内部访问
function myTest() {
    var x = 1
    let y = 0
}

// 循环作用域
var i = 7;
for (var i = 0; i < 10; i++) {
  // 一些语句
}
let i = 7;
for (let i = 0; i < 10; i++) {
  // 一些语句
}
// 此处 i 为 7
```

## const

```javascript
// JavaScript const 变量必须在声明时赋值
const PI = 3.14159265359;

// 您可以创建 const 对象：
const car = {type:"porsche", model:"911", color:"Black"};
// 您可以更改属性：
car.color = "White";
// 您可以添加属性：
car.owner = "Bill";

// 您可以创建常量数组：
const cars = ["Audi", "BMW", "porsche"];
// 您可以更改元素：
cars[0] = "Honda";
// 您可以添加元素：
cars.push("Volvo");

// 在块作用域内使用 const 声明的变量与 let 变量相似
// 在同一作用域或块中，为已有的 const 变量重新声明声明或赋值是不允许的：
// 在另外的作用域或块中重新声明 const 是允许的：
```

## set

Set（集合）是一组唯一值的集合。每个值只能在 Set 中出现一次。Set 可以容纳任何数据类型的值。
```new Set()```，```add()```， ```delete()```， ```has()```， ```clear()```， ```forEach()```，
```values()```， ```keys()```， ```entries()```， ```size```

## map

Map 保存键值对，其中键可以是任何数据类型，会记住键的原始插入顺序，提供表示映射大小的属性。
```new Map()```，```set()```，```get()``` ，```clear()```，```delete()```，```has()```，
```forEach()```，```entries()```，```keys()```，```values()```

## 对象

```javascript
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id       : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

person.firstName;
person.fullName();
// 请不要把字符串、数值和布尔值声明为对象
var x = new String();        // 把 x 声明为 String 对象
var y = new Number();        // 把 y 声明为 Number 对象
var z = new Boolean();       //	把 z 声明为 Boolean 对象
```

## 事件
  
HTML 事件是发生在 HTML 元素上的“事情”。当在 HTML 页面中使用 JavaScript 时，JavaScript 能够“应对”这些事件。

```javascript
// 通过 JavaScript 代码，HTML 允许您向 HTML 元素添加事件处理程序。
<element event='一些 JavaScript'>
<button onclick='document.getElementById("demo").innerHTML=Date()'>现在的时间是？</button>
// onchange, onclick, onmouseover, onmouseout, onkeydown, onload
```

## 字符串方法

```length```, ```indexOf("item")```, ```lastIndexOf("item")```, ```search(/text/ig)```, ```slice(start, end)```,
```substring(start, end)```, ```substr(start, length)```, ```replace(/text/ig,/hello/)```, ```toLowerCase()```,
```toUpperCase()```, ```concat(another_string)```, ```String.trim()```, ```charAt(position)```,
```charCodeAt(position)```, ```split(",")```, ```lastIndexOf()```, ```startsWith("item")```, ```endsWith("item")```,
```match(/text/ig)```, ```includes("item")```, 

## 数组方法

```toString()```, ```join("*")```, ```pop()```, ```push("new_item")```, ```shift()```, ```unshift("item")```,
```splice(how_many_added, how_many_dropped, "item1", "item2")```, ```splice(where_to_drop, how_many_drop)```, ```length```,```concat(item_1, item_2)```, ```slice(from_index_to_end)```, ```toString()```, ```sort()```,
```forEach(function_name)```, ```map(function_name)```, ```filter(function_name)```, ```reduce(function_name)```, ```reduceRight(function_name)```, ```every()```, ```some(function_name)```, ```indexOf(function_name)```, ```lastIndexOf(function_name)```, ```findIndex(function_name)```

## Date

```new Date()```, ```new Date(year, month, day, hours, minutes, seconds, milliseconds)```, ```new Date(milliseconds)```, ```new Date(date string)```, ```getDate()```, ```getDay()```, ```getFullYear()```, ```getHours()```, ```getMilliseconds()```, ```getMinutes()```, ```getMonth()```, ```getSeconds()```, ```getTime()```, ```getUTCDate()```, ```getUTCDay()```, ```getUTCFullYear()```, ```getUTCHours()```, ```getUTCMilliseconds()```, ```getUTCMinutes()```, ```getUTCMonth()```, ```getUTCSeconds()```, ```setDate()```, ```setFullYear()```, ```setHours()```, ```setMilliseconds()```, ```setMinutes()```, ```setMonth()```, ```setSeconds()```, ```setTime()```

## Math

```Math.round()```, ```Math.PI```, ```Math.pow(x, y)```, ```Math.sqrt()```, ```Math.abs(x)```, ```Math.ceil()```,
```Math.floor()```, ```Math.sin()```, ```Math.cos()```, ```Math.min()```, ```Math.max()```, ```Math.random()```,
```Math.tan()```, ```Math.sqrt()```, ```Math.log()```, ```Math.floor(Math.random() * 10)```, 

## 流程控制(condition, loop)

- ```if () {} else {}```, ```if () {} else if () {} else {}```
- switch
  
```javascript
   switch(表达式) {
     case n:
        代码块
        break;
     case n:
        代码块
        break;
     default:
        默认代码块
   }
```

- loop
  - for - 多次遍历代码块
  - for/in - 遍历对象属性
  - while - 当指定条件为 true 时循环一段代码块
  - do/while - 当指定条件为 true 时循环一段代码块

```javascript
for (i = 0; i < cars.length; i++) { 
    text += cars[i] + "<br>";
 }
var person = {fname:"Bill", lname:"Gates", age:62}; 

var text = "";
for (let x in person) {
    text += person[x];
}
```

## use strict

它不算一条语句，而是一段文字表达式，更早版本的 JavaScript 会忽略它。
"use strict"; 的作用是指示 JavaScript 代码应该以“严格模式”执行。

在严格模式中，您无法，例如，使用未声明的变量。

## this 关键词

JavaScript this 关键词指的是它所属的对象。

它拥有不同的值，具体取决于它的使用位置:

- 在对象方法中，this 指的是所有者对象。
- 单独的情况下，this 指的是全局对象。
- 在函数中，this 指的是全局对象。
- 在函数中，严格模式下，this 是 undefined。
- 在事件中，this 指的是接收事件的元素。
- 像 call() 和 apply() 这样的方法可以将 this 引用到任何对象。

```javascript
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id       : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"Bill",
  lastName: "Gates",
}
person1.fullName.call(person2);  // 会返回 "Bill Gates"
```

## ES6

ECMAScript 6（简称ES6）是于2015年6月正式发布的JavaScript语言的标准，正式名为ECMAScript 2015（ES2015）。

它的目标是使得JavaScript语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

## 箭头函数

ES6 中引入了箭头函数。箭头函数允许我们编写更短的函数。

```javascript
let myFunction = (a, b) => a * b;
hello = function() {
  return "Hello World!";
}
hello = () => {
  return "Hello World!";
}
hello = () => "Hello World!";
hello = (val) => "Hello " + val;
hello = val => "Hello " + val;
```

对于箭头函数，this 关键字始终表示定义箭头函数的对象。

## 类

对象模版，请始终添加名为 constructor() 的方法。

```javascript
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}

let myCar1 = new Car("Ford", 2014);
let myCar2 = new Car("Audi", 2019);
```

## 模块

JavaScript 模块允许您将代码分解成单独的文件。这会使维护代码库更加容易。

模块是使用 import 语句从外部文件导入的。模块还依赖于```<script>``` 标签中的```type="module"```。

```javascript
<script type="module">
import message from "./message.js";
</script>
```

## 导出

带有函数或变量的模块可以存储在任何外部文件中。导出有两种类型：命名导出和默认导出。

- 命令导出
  
让我们创建一个名为 person.js 的文件，并在其中填充我们要导出的内容。

```javascript
// 逐个内联创建
export const name = "Bill";
export const age = 19;
// 在文件底部一次性全部创建
const name = "Bill";
const age = 19;

export {name, age};
```

- 默认导出
  
让我们创建另一个名为 message.js 的文件，并用其演示默认导出。 一个文件中只能有一个默认导出。

```javascript
const message = () => {
const name = "Bill";
const age = 19;
return name + ' is ' + age + 'years old.';
};

export default message;
```

## 导入

您可以通过两种方式将模块导入到文件中，具体取决于它们是命名导出还是默认导出。
命名导出是使用大括号构造的。默认导出不是。

- 从命名导出中导入
从文件 person.js 导入命名导出：

```javascript
import { name, age } from "./person.js";
```

- 从默认导出导入
从文件 message.js 导入默认导出：

```javascript
import message from "./message.js";
```

## call

通过 call()，能够使用属于另一个对象的方法。

```javascript
var person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}
var person1 = {
    firstName:"Bill",
    lastName: "Gates",
}
var person2 = {
    firstName:"Steve",
    lastName: "Jobs",
}
person.fullName.call(person1);  // 将返回 "Bill Gates"

var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"Bill",
  lastName: "Gates"
}
person.fullName.call(person1, "Seattle", "USA");
```

## apply

apply() 方法与 call() 方法非常相似，不同之处是：call() 方法分别接受参数。apply() 方法接受数组形式的参数。

```javascript
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"Bill",
  lastName: "Gates"
}
person.fullName.apply(person1, ["Oslo", "Norway"]);
```

## 闭包

JavaScript 变量属于本地或全局作用域。全局变量能够通过闭包实现局部（私有）。

创建闭包的常见方式是在一个函数内部创建另一个函数，而该内部函数可以访问外部函数的局部变量，
当外部函数执行完毕后，通常这些局部变量会被垃圾收集器回收，但因为闭包的存在，这些变量会继续存在于内存中。

```javascript
function createCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
 
const counter = createCounter();
console.log(counter()); // 输出: 1
console.log(counter()); // 输出: 2
console.log(counter()); // 输出: 3
```

## 回调函数

回调函数是一种特殊的函数，可以作为参数传递给另一个函数，并在某个事件或条件满足时被调用。

回调函数通常用于处理异步操作，比如定时器、事件处理、网络请求等。

```javascript
function doSomething(callback) {
  setTimeout(function() {
    console.log("异步操作完成");
    callback();
  }, 3000);
}
 
function callbackFunction() {
  console.log("回调函数被调用");
}
 
doSomething(callbackFunction);
```

在上述代码中，doSomething函数接受一个回调函数作为参数，并在延迟3秒后调用回调函数。
当异步操作完成时，会打印出"异步操作完成"，然后调用回调函数，打印出"回调函数被调用"。

回调函数的好处是可以将代码模块化和重用，将回调函数作为参数传递给不同的函数，可以根据需要执行不同的操作。
然而，过多的回调嵌套也会导致代码难以维护和理解，为了解决这个问题，可以使用Promise、async/await等更高级的异步编程方式。

## promise

promise 是一种用于处理异步操作的对象。它提供了一种更加优雅的方式来处理异步操作，避免了传统回调函数导致的“回调地狱”（callback hell）。

- Promise 的基本概念
  - ‌三种状态：
    - pending：初始状态，既不是成功，也不是失败状态。
    - fulfilled：意味着操作成功完成。
    - rejected：意味着操作失败。
  - 创建 Promise‌
    通过 new Promise 构造函数来创建，它接受一个执行器函数作为参数，执行器函数有两个参数：resolve 和 reject，分别用于在异步操作成功时和失败时改变 Promise 的状态。
  - 使用 Promise‌：
    - then 方法：用于处理 Promise 成功的情况，它接受一个函数作为参数，这个函数会在 Promise 成功时执行。
    - catch 方法：用于处理 Promise 失败的情况，它接受一个函数作为参数，这个函数会在 Promise 失败时执行。
    - finally 方法：无论 Promise 成功还是失败，都会执行的方法。
- 示例
  
```javascript
let promise = new Promise(function(resolve, reject) {
    // 异步操作
    setTimeout(() => {
        const data = '操作成功';
        // 根据操作结果改变 Promise 的状态
        resolve(data);
        // 或者失败时
        // reject('操作失败');
    }, 1000);
});

promise.then(function(value) {
    // 成功时的处理
    console.log(value);
}).catch(function(error) {
    // 失败时的处理
    console.log(error);
}).finally(function() {
    // 无论成功还是失败都会执行
    console.log('操作完成');
});
```

- 特点

对象的状态不受外界影响。Promise 对象代表一个异步操作，有三种状态：pending、fulfilled 和 rejected。
只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。

一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise 对象的状态改变，只有两种可能：从 pending 变为 fulfilled
和从 pending 变为 rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为 resolved（已定型）。

如果改变已经发生了，你再对 Promise 对象添加回调函数，也会立即得到这个结果。这与事件（Event）完全不同，事件的特点是，如果你错过了它，
再去监听，是得不到结果的。
Promise 是 ES6 引入的，是现代 JavaScript 开发中处理异步操作的重要工具。

## async & await

async & await主要用于处理异步操作，使得异步代码看起来和同步代码一样，从而提高代码的可读性和可维护性

场景：从 API 获取用户数据

假设你有一个 API，它返回关于用户的信息。你想获取这个信息并在控制台中打印出来。使用 async & await，你可以这样写：

```javascript
// 假设 fetchUser 是一个返回 Promise 的函数，它异步地从 API 获取用户数据
async function getUser() {
  try {
    const userData = await fetchUser();
    console.log(userData);
  } catch (error) {
    console.error('获取用户数据时发生错误:', error);
  }
}

getUser();
```

在这个例子中：
getUser 函数被声明为 async，这意味着它将自动返回一个 Promise。
在 getUser 函数内部，我们使用 await 关键字等待 fetchUser() 函数的结果。await 只能在 async 函数内部使用。
如果 fetchUser() 成功解析，其结果将被存储在 userData 变量中，并在控制台中打印出来。
如果 fetchUser() 抛出错误，catch 块将捕获该错误，并在控制台中打印出错误信息。

这种方式的好处是，它使得异步代码看起来更像是同步代码，从而更容易理解和维护。你不需要使用.then()和.catch()方法来处理Promise，
而是可以使用更直观的try/catch结构。async & await是建立在Promise机制之上的，它不能用于普通的回调函数，其本质是对Promise
的封装。

## 样式指南

- 对标识符名称（变量和函数）使用了驼峰式大小写, 且以字母开头
- 全局变量使用大写
- 常量（比如 PI）使用大写
- 始终在运算符（ = + - * / ）周围以及逗号之后添加空格
- 对代码块缩进使用 4 个空格
- 始终以分号结束单条语句
- 复杂语句：
  - 在第一行的结尾处写开括号
  - 在开括号前使用一个空格
  - 在新行上写闭括号，不带前导空格
  - 不要以分号来结束复杂语句
- 对象定义
  - 把开括号与对象名放在同一行
  - 在每个属性与其值之间使用冒号加一个空格
  - 不要在最后一个属性值对后面写逗号
  - 请在新行上写闭括号，不带前导空格
  - 请始终以分号结束对象定义
- 行长度小于 80，换行的最佳位置是运算符或逗号之后
- 使用小写文件名，JavaScript 文件应该使用 .js 扩展名
  
## 最佳实践

- 请避免全局变量，全局变量可用闭包代替
- 始终声明局部变量
- 在顶部声明，一项好的编码习惯是把所有声明放在每段脚本或函数的顶部
- 声明变量时，初始化变量
- 不要声明数值、字符串或布尔对象
- 请勿使用 new Object()
  - 请使用 {} 来代替 new Object()
  - 请使用 "" 来代替 new String()
  - 请使用 0 来代替 new Number()
  - 请使用 false 来代替 new Boolean()
  - 请使用 [] 来代替 new Array()
  - 请使用 /()/ 来代替 new RegExp()
  - 请使用 function (){}来代替 new Function()
- 意识到自动类型转换
  
```javascript
var x = "Hello";     // typeof x 为字符串
x = 5;               // 把 typeof x 更改为数值
var x = 5 + 7;       // x.valueOf() 是 12,  typeof x 是数值
var x = 5 + "7";     // x.valueOf() 是 57,  typeof x 是字符串
```

- 使用 === 比较
== 比较运算符总是在比较之前进行类型转换（以匹配类型）。
=== 运算符会强制对值和类型进行比较：

```javascript
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false
```

- 用 default 来结束 switch
- 避免使用 eval(), 存在安全隐患
- 给函数参数设置默认值




