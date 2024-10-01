# Typescript Basics

- [Typescript Basics](#typescript-basics)
  - [简介](#简介)
  - [编译ts到js](#编译ts到js)
  - [语法特性](#语法特性)
    - [编译时类型检查](#编译时类型检查)
    - [接口](#接口)
    - [类](#类)
      - [访问修饰符](#访问修饰符)
      - [继承](#继承)

## 简介

TypeScript 是 JavaScript 的超集，扩展了 JavaScript 的语法，因此现有的 JavaScript 代码可与 TypeScript 一起工作无需任何修改，TypeScript 通过类型注解提供编译时的静态类型检查。

TypeScript 可处理已有的 JavaScript 代码，并只对其中的 TypeScript 代码进行编译。

## 编译ts到js

- 安装tsc

我的环境是macos的，所以我使用的是```brew install typescript```。在我使用brew安装之前，我也使用
```npm install -g typescript```但是安装成功后，用不了tsc。brew安装就没有这个问题。
指令为：

```bash
brew install tsc
tsc --version
# Version 5.6.2
```

- 编写ts文件
  
```typescript
// greeter.ts
function greeter(person) {
    return "Hello, " + person;
}

let user = "Jane User";

document.body.innerHTML = greeter(user);
```

- 编译ts为js
  
```bash
tsc greeter.ts
```

输出为greeter.js，查看内容，发现和greeter.js基本一致。

有了js只有，我们就可以在html中引用了。

```html
<!DOCTYPE html> 
<html> 
<head> 
<meta charset="utf-8"> 
<title>Learning TypeScript</title>
</head> 
<body> 
    <script src="greeter.js"></script>
</body> 
</html>
```

然后在浏览器中打开给文件，就一个看到界面了。

## 语法特性

### 编译时类型检查

‌在JavaScript中，定义变量和函数参数不需要定义类型，变量的类型是动态的。JavaScript函数在定义时不需要指定参数的类型，函数调用时也不会对传入的参数进行类型检查，甚至参数的个数也不做检查。而Typescript支持类型检查
我们给person参数，定义类型。

```typescript
function greeter(person: string) {
    return "Hello, " + person;
}

let user = 1;

document.body.innerHTML = greeter(user);
```

我们定义person为string类型，但是传参为整数，这个时候重新编译，则会出现以下错误：

```log
greeter.ts:7:35 - error TS2345: Argument of type 'number' is not assignable to parameter of type 'string'.
7 document.body.innerHTML = greeter(user);
                                    ~~~~
Found 1 error in greeter.ts:7
```

编译器捕捉到了该类型错误。

### 接口

在JavaScript中，虽然没有内置的接口支持，也就是说没有关键字interface可以直接声明接口。而Typescript是支持的。
我们继续在greeter.ts中引入接口。

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = { firstName: "Jane", lastName: "User" };

document.body.innerHTML = greeter(user);
```

编译完成了，我们查看生成的js文件（如下），是没有接口的。

```javascript
function greeter(person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}
var user = { firstName: "Jane", lastName: "User" };
document.body.innerHTML = greeter(user);
```

### 类

‌JavaScript中没有传统意义上的类，即是没有class这个关键字，但可以通过原型和构造函数模拟类的行为，并实现继承‌。但是Typescript的类是真正的传统意义上的类，支持class关键字定义，并且支持访问修饰符（public、private、protected），可以限制类成员的访问权限，还引入了JavaScript中没有的其他特性，如抽象类、接口、泛型类等，使得类的定义更加强大和灵活‌。

我们继续更改greeter.ts，编写ts的类。

#### 访问修饰符

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

// 实现了接口
class Student implements Person{
    fullName: string
    constructor(public firstName, public middleName, public lastName) {
        this.fullName = this.firstName + this.middleName + this.lastName
    }
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + person.lastName;
}

let user = new Student('cara', '', 'wang');

document.body.innerHTML = greeter(user);
```

编译ts成功。然而，当我们将其属性设置成private，然后在greeter函数中使用时，编译时，我们将遇到如下类似错误：

```log
greeter.ts:15:50 - error TS2341: Property 'middleName' is private and only accessible within class 'Student'.
```

提示我们私有变量仅能在类内部调用。

#### 继承

我们继续编辑greeter.ts，实现继承功能

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

// 实现了接口
class Student implements Person{
    fullName: string
    constructor(public firstName, public middleName, public lastName) {
        this.fullName = this.firstName + this.middleName + this.lastName
    }
}

class FemaleStudent extends Student {
    greetings: string
    constructor(public firstName: string, public middleName: string,
        public lastName: string, private age: number) {
        super(firstName, middleName, lastName);
        this.greetings = this.firstName + ' ' + this.middleName +
            ' ' + this.lastName + ' is ' + this.age + ' years old!'
    }
}

function greeter(person: FemaleStudent) {
    return person.greetings;
}

let user = new FemaleStudent('cara', ' ', 'wang', 18);

document.body.innerHTML = greeter(user);
```
