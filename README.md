---
title: JS面试题讲解
date: 2018-05-20 09:00:10
tags: 
  - 面试题
  - 讲解
  - 技巧
categories: 
  - 面试题
---

# JS面试题讲解

## 讲解目的

1. **对于面试题有一定的了解。**

   在面试过程中，会存在根据你报的薪资问对应的问题的情况：

   - 薪资较低：HTML、CSS、JavaScript、（写写静态页面）等等......
   - 薪资中等：JavaScript高级、框架的使用、兼容性问题、项目经验（维护开发项目）......
   - 薪资较高：JavaScript高级、框架封装、前沿技术、项目展示、底层原理（Leader）......

   （**不管期望的待遇如何，JS作为前端的灵魂，是必然要熟练使用的看家本领，也是面试中必问的方面**）

2. ***对于JS阶段的学习起到一定的回顾作用。***

   **老实交代，你们还记得多少？**

3. **发现一些在之前学习过程中没遇过的''Bug''。**

   - 实际开发过程中，会遇到很多奇怪的Bug，穷尽你所学，也无法解决它，这时候你怎么办？
   - 很多CSS、JS执行时不符合逻辑的地方，不应该纠结。咱们的代码敲出来是什么效果，是由浏览器说的算的，很多存在的Bug是浏览器的问题，咱们面对这种Bug的时候，只需要知道怎么通过其他途径完成咱们的效果，而不是纠结谷歌公司为什么有这种恶趣味。
   - 而各种奇怪的坑的解决方法，就是咱们前端开发过程中的经验。（前辈只是走过的坑比你们多而已，知识都是一样的）

# 面试题

## 1.  js中使用 typeof 能得到的类型有哪些

#### 简答：

**undefined、string、number、boolean、object、function** 

就这么样就结束了吗？

#### 解析：

```js
// 数据类型有哪些？
// typeof  判断数据类型 把类型信息当作字符串返回 
console.log(typeof undefined) //undefined
console.log(typeof 'abc') //string
console.log(typeof 123) //number
console.log(typeof NaN) //number
console.log(typeof true) //boolean
console.log(typeof {}) //object
console.log(typeof []) //object
console.log(typeof null) //object(ES规范定死的)（比较地址前几位）--------------------------------
console.log(typeof console.log) //function
function fn() {

}
console.log(typeof fn); //function

// 总结： undefined/string/number/boolean/object/function
```

#### 之前：

六大数据类型

- 基本数据类型（简单数据类型）
  - number 数值型(NaN)
  - string 字符串
  - boolean 布尔型
  - undefined 未定义
  - null 空引用
- 引用数据类型（复杂数据类型）
  - object

#### 百度：

```
Null类型是第二个只有一个值的数据类型，这个特殊的值是null，从逻辑角度来看，null值表示一个空对象指针，而这也正是使用typeof操作符检测null值会返回“object”的原因，如下面的例子所示：
    var car =null;
    alert(typeof null);  //object（其实这是JavaScript最初实现的一个错误，后来被ECMAScript沿用下来）
如果定义的变量准备在将来用户保存对象，那么最好将该变量初始化为null而不是其他值。这样一来，只要直接检查null值就可以知道相应的变量是否已经保存了一个对象的引用，如下面的例子：
    if(car != null){
    //对car执行某些操作
    }
实际上，undefined值是派生自null值的，因此ECMA-262规定对他们的相等测试要返回true：
    alert(null == undefined)  //true
    这里，位于null和undefined之间的相等操作符（==）总是返回true，不过要注意的是，这个操作符出于比较的目的会转换其操作数。
    尽管null和undefined有这样的关系，但它们的用途完全不同，如前所述，无论什么情况下都没有必要把一个变量的值显式地设置为undefined，可视同样的规则对null却不适用。换句话说，只要意在保存对象的变量还没有真正保存对象，就应该明确地让该变量保存null值。这样做不仅可以体现null作为空对象指针的惯例，而且也有助于进一步区分null和undefined。
```

## 2. 何时使用 === 何时使用 == 

#### 简答：

**当仅需要比较值是否相等时，用==；**

**当需要比较类型和值时，用===。**

就这么样就结束了吗？

#### 解析：

```js
// 有何区别？
// 会存在隐式转换。
// 1.==

// 如果 x 或 y 中有一个为 NaN，则返回 false；
console.log(NaN == true); //false

// 如果 x 与 y 皆为 null 或 undefined 中的一种类型，则返回 true（null == undefined // true）；否则返回 false（null == 0 // false）；
console.log(null == undefined); //true(特殊情况)---------------------------------
console.log(null == ''); //false
console.log(undefined == ''); //false

// 如果 x,y 类型不一致，且 x,y 为 String、Number、Boolean 中的某一类型，则将 x,y 使用 Number 函数转化为 Number 类型再进行比较；
console.log(true == '123'); //false
console.log(true == '1'); //true
console.log(false == '0'); //true

console.log(true == !0); //true

console.log([] == []); //false
console.log([] == ![]); //true 比较地址 ------------------------------------------------
var a = c = [];
var b = [];
console.log(a == b); //false
console.log(a == !b); //true
console.log(a == c); //true

console.log(Boolean([]) == true); //true
console.log(Number([]) == 0); //true
console.log(Number(false) == 0); //true
```
####百度：

```
如果 x 或 y 中有一个为 NaN，则返回 false；
如果 x 与 y 皆为 null 或 undefined 中的一种类型，则返回 true（null == undefined // true）；否则返回 false（null == 0 // false）；
如果 x,y 类型不一致，且 x,y 为 String、Number、Boolean 中的某一类型，则将 x,y 使用 Number 函数转化为 Number 类型再进行比较；
```

## 3. js变量按照存储方式分为哪些类型，并描述其特点

#### 简答：

**简单数据类型、复杂数据类型（值、引用）。**

**值类型：简单类型， 变量在存储简单类型的时候，存储的是值本身。**

**引用类型：复杂类型，变量在存储复杂类型的时候，只会存储这个对象的地址，并不会存储对象的值。**

？？？

#### 解析：

```js
//简单类型(值类型)
//复杂类型(引用类型)
//在内存中如何存储 （内存）  内存（2G 4G 8G 16G）  硬盘空间（）
//简单类型如何存储

//变量在存储简单类型的时候，存储的直接就是值本身。
var num = 11;
var num2 = num;
num2 = 22;
console.log(num); //11
console.log(num2); //22

//变量在存储复杂类型的时候，不会把整个对象都存储起来，只会存这个对象的地址（引用）
//对象会在内存中随机找一块内存存储起来.
var obj = {
    name: "zs",
    age: 18
};
var obj2 = obj; //把obj的值赋值给obj2（地址）
obj2.name = "ls";
console.log(obj.name); //ls
console.log(obj2.name); //ls

//值类型：简单类型， 因为变量在存储简单类型的时候，存储的是值本身。
//引用类型：复杂类型，变量在存储复杂类型的时候，只会存储这个对象的地址，并不会存储对象的值。
var obj = {};
var obj2 = obj; //仅仅是地址赋值了一份，所以两个变量都指向了同一个地址。
```

## 4. 数组的常用api有哪些 

#### 简答：

**push() 、pop() 、unshift() 、shift()；**
**es6：filter()、 forEach()、 some() 、every() 、map()等**

？？？

#### 解析：

```js
// push() pop() unshift() shift()
// es6：filter() forEach() some() every() map()等
// 注意
// 1. forEach存在的问题，循环停不下来
// 2. filter、map 方法的使用

var arr = [12, 34, 56, 89, 78, 23, 45, 19];

//filter方法返回一个由符合函数要求的元素组成的新数组-------------------------------------------
// 1. 要求：把arr中所有大于30的元素放到一个新数组中。
// 原始方法：
var newArr = [];
for (var i = 0; i < arr.length; i++) {
    if (arr[i] > 30) {
        newArr.push(arr[i])
    }
}
// API的方法：
//调用数组的filter方法，添加过滤方法，符合规则的元素会被存放到新数组里
//element:表示数组里的元素;index:表示索引值;array:表示调用filter方法的数组。
var newArr = arr.filter(function (element, index, array) {
    return element > 30;
});
console.log(arr); //filter方法不会改变原数组里的数据[12,34,56,89,78,23,45,19];
console.log(newArr); //新数组里保存符合要求的元素[34, 56, 89, 78, 45]


//map方法让数组中的每个元素都调用一次提供的函数，将调用的后的结果存放到一个新数组里并返回。------------
// 2. 要求：件数组中的每一个元素后面添加一个字符串'0'放到一个新数组中。
// 原始方法
var newArr = [];
for (var i = 0; i < arr.length; i++) {
    newArr.push(arr[i] + '0');
}
// API的方法
var newArr = arr.map(function (element, index, array) {
    //在数组里的每一个元素的最后面都添加一个字符串"0"
    return element + "0";
});
console.log(newArr); //["120", "340", "560", "890", "780", "230", "450", "190"]
console.log(arr); //map方法不会改变原数组里的数据 [12,34,56,89,78,23,45,19]

//forEach() 方法对数组的每个元素执行一次提供的函数,且这个函数没有返回值------------------------------
// 3.要求：打印每一个元素
// 原始方法
for (var i = 0; i < arr.length; i++) {
    console.log("第" + i + "个元素是" + arr[i]);
}
// API方法
var result = arr.forEach(function (element, index, array) {
    //数组里的每一个元素都会被打印
    console.log("第" + index + "个元素是" + element);
});
console.log(result); //函数没有返回值

//some() 方法测试数组中的某些元素是否通过由提供的函数实现的测试.----------------------------------
// 4.要求：判断数组中是否有元素大于50
// 原始方法
for (var i = 0; i < arr.length; i++) {
    if (arr[i] > 50) {
        result = true;
        break;
    }
}
// API方法
var result = arr.some(function (element, index, array) {
    //数组里否有一些元素大于50.只要有一个元素大于，就返回true
    console.log(element); //12,34,56
    return element > 50;
});
console.log(result); //true

//every() 方法测试数组的所有元素是否都通过了指定函数的测试。----------------------------------------
// 5.要求：判断数组中的每个元素是否都大于50
// 原始方法
var result = true;
for (var i = 0; i < arr.length; i++) {
    if (arr[i] < 50) {
        result = false;
        break;
    }
}
// API方法
result = arr.every(function (element, index, array) {
    //数组里是否每一个元素都大于50.只有在所有的数都大于50时，才返回true
    console.log(element);
    return element > 50;
});
console.log(result); //false
```

## 5. 如何准确判断一个变量是数组类型

#### 简答：

**可以通过 `instanceof` 来判断， 用`arr instanceof Array; ` 。**

？？？

#### 解析：

```js
// instanceof 操作符
// 用来判断引用数据类型属于哪个构造函数的方法

// f instanceof Foo 的判断逻辑：构造函数的原型对象，是否在实例对象的原型链上
// Foo.prototype 是否在 实例f的原型链上

var arr = [];
arr instanceof Array; // true
typeof arr; // object,, typeof 只能获取简单数据的类型
```

#### 之前：

js基础阶段对instanceof作用的描述 : **判断一个对象是否是某个构造函数的实例**

现在我们学习了原型,也学习了原型链,所以我们现在可以更严谨的描述他的作用:

**判断一个函数的原型对象,是否在实例对象的原型链上**

## 6. 描述 new 一个对象的过程

#### 简答：

```js
1. 创建一个对象；
2. this 指向这个新创建的对象；
3. 执行构造函数的代码；
4. 返回this。
```

？？？（这次还说吗？）

## 7. 说一下变量提升的理解? 

#### 简答：

- **变量定义、函数声明提升（同名提升问题）**
- **因为在es6之前没有块级作用域，早起提出一个预解析的方案，但是实际使用的时候，并没有想的那么好。**
- **es6中的let和const可以拥有块级作用域**。

#### 解析：

1. **声明提升**

```js
// 1.变量提升
var a;
console.log(a); // undefined
var a = 100;

// 2.函数声明提升
function fn(name){
    var name='zs';
    var age;
    age = 20;
    console.log(name, age); //zs 、20
}
fn('zs');


//3.变量与函数
function a() {
    console.log('我是函数');
}
console.log(a);
var a = 10;
console.log(a);

// 声明提升的范围：全局作用域 && 函数内部
// 注意：函数声明和函数表达式的区别
var a;
console.log(a);
var a=10;
var a=function(){
    console.log('我是函数');
}
console.log(a);
```

2. **作用域（es6中的let和const）**

```js
//es6之前
// 没有块级作用域{}，只有全局作用域和函数作用域（词法作用域）
// 无块级作用域(如果有块级作用域)
console.log(a); // undefined  --> 没有块级作用域，变量提升到全局作用域
if(true){
    var a = 'zs'; // 提升到if外面（如果是let呢）
}
console.log(a); // zs

// 函数作用域和全局作用域
var a = 100;
function fn(){
    var a = 200;
    console.log('fn ',a); // 200
}
console.log('global ',a); // 100
fn();

// 作用域链
// 作用域链是在函数定义的时候确定下来的
var a = 100;
function fn(){
    var b = 200;
    console.log(a); // 100  --> 当前作用域没有声明变量a，去声明时父级作用域中取值
    console.log(b); // 200
}
```

## **8. 说明  this  几种不同的使用场景?**

#### 简答：

**构造函数（new出来的过程）、对象方法、普通函数、借用方法模式（上下文调用模式）**

#### 解析：

```js
// this的指向要在函数执行的时候才能确定，函数定义时是无法确认（就是只看函数是如何被调用的，而不看函数是如何定义的）

// 1. 作为普通函数执行
function fn(){
    console.log(this === window);
}
fn(); // true

// 2. 对象调用模式
var obj = {
    name: 'A',
    printName: function(){
        console.log(this.name)
    }
};
obj.printName(); // A

// 3. 构造函数new的时候（this指向的变化）
function Foo(name){
    this.name = name;
    console.log(this);
}
var f = new Foo('zs');// f

// 4. 借用方法（上下文调用模式）
function fn(name){
    console.log(name);
    console.log(this);
}
fn.call({x:100}, 'zs');
// zs
// {x:100}


// 综合：
var a = {
    name: 'A',
    fn: function(){
        console.log(this);
    }
};
a.fn(); // ？？
a.fn.call({name: 'B'}); // B  -->  fn函数内部的this指向{name: 'B'}
var fn2 = a.fn;
fn2(); // fn2函数内部的this指向window，不看函数是如何定义的，只看函数是如何被调用的
```

## 9.  如何理解作用域?

#### 简答：

- **es6之前的作用域只有全局作用域和函数作用域（词法作用域）**
- **es6出现了块级作用域（{}）**
- **作用域出现是历史原因**

#### 解析：

```js
//es6之前
// 没有块级作用域，只有全局作用域和函数作用域（词法作用域）
// 无块级作用域(如果有块级作用域)
console.log(a); // undefined  --> 没有块级作用域，变量提升到全局作用域
if(true){
    var a = 'zs'; // 提升到if外面
}
console.log(a); // zs

// 函数作用域和全局作用域
var a = 100;
function fn(){
    var a = 200;
    console.log('fn ',a); // 200
}
console.log('global ',a); // 100
fn();

// 作用域链
// 作用域链是在函数定义的时候确定下来的
var a = 100;
function fn(){
    var b = 200;
    console.log(a); // 100  --> 当前作用域没有声明变量a，去声明时父级作用域中取值
    console.log(b); // 200
}
```

## 10. 实际开发中闭包的应用?

#### 简答：

1. **私有化数据。**
2. **数据保持。**

#### 解析：

```javascript
function main(){
    var money = 10000;  //放到局部作用中,防止全局变量污染(私有化数据)

    return {
        queryMoney : function(){
            return money;
        },
        payMoney : function(num){
            money -= num;
        },
        addMoney : function(num){
            money += num;
        }
    }
}

var moneyManger = main();  // 通过moneyManger 可以获取到局部的变量money
```

**缺点：**

  **由于内部的函数使用了外部函数的变量,导致外部这个函数无法被回收掉.如果代码中大量的存在闭包,可能会导致内存泄露 (不要刻意使用闭包)。**

# 笔试题

## 1.打印结果是什么？ 

```js
console.log(1);
setTimeout(function(){
    console.log(2);
}, 0);
console.log(3);
setTimeout(function(){
    console.log(4);
}, 1000);
console.log(5);

// print: ？？？
堆栈。。。
```

## 2. 打印结果是什么？

```js
function add(x, y) {
    console.log(x + y);
}

function sub(x, y) {
    console.log(x - y)
}
add.call(sub, 5, 3);
// 打印些什么
```

## 3.打印结果是什么？

```js
// 1. 
(function(foo){
    console.log(foo.bar);  // 返回结果？？？
})({ foo: { bar: 1 } });


// 2.
(function f(f){
    console.log(f());  // 返回结果？？？
})(function(){ return 1; });


// 3.
var foo = {
    bar: function() { return this; },
    baz: 1
};
(function(){ 
     console.log(arguments[0]());  // 返回结果？？？
})(foo.bar);
```

##4. 结果是什么？

```js
// 1、考察原型链
// 下面程序执行后弹出什么样的结果?
function fn() {
    this.a = 0;
    this.b = function() {
        alert(this.a)
    }
}
fn.prototype = {
    b: function() {
        this.a = 20;
        alert(this.a);
    },
    c: function() {
        this.a = 30;
        alert(this.a);
    }
}
var myfn = new fn();
myfn.b(); // ???
myfn.c(); // ???
```

## 5. 统计一个字符串中每个字符出现的次数

```js
var str = 'asdfssaaasasasasaa';

var arr = str.split('');
var result = {};
arr.forEach(function (e, i, a) {
    if (result[e] == undefined) {
        result[e] = 1;
    } else {
        result[e]++;
    }
})
console.log(result);
```

## 6. 获取随机数，要求是长度一致的字符串格式

```js
// Math.random() 生成[0,1)的随机数，小数点后面数值个数不定
function getRanLeng(){
    // 要求是每次获取的长度是一致的
    // 所以可以在随机数后面加上一定位数的字符串的00000  防止生成的是1位数，务必多余9位，越多越好
    var random = Math.random() + '0000000000';
    return random.slice(0, 10);
}

for(var i = 0; i < 100; i++){
    console.log(getRanLeng())
}
```

## 7.  去掉一个数组的重复元素

```js
var arr = [1, 2, 3, 1, 43, 12, 12, 1, 2, 3, 4, 5];

var result=[];
for (var i=0;i<arr.length;i++){
    if(result.indexOf(arr[i])==-1){
        result.push(arr[i]);
    }
}
console.log(result)
```

## 8. 完成下列要求,函数返回扁平化后的数组如：[1, [2, [ [3, 4], 5], 6]] => [1, 2, 3, 4, 5, 6]。

```js
var arr = [1, [2, [ [3, 4], 5], 6]];

//用了什么方法？用了什么语法？不要纠结语法，但是要会说。
var newArr=[];
function fn() { 
    for(var i=0;i<arguments.length;i++){
        if(arguments[i] instanceof Array){
            fn.apply(null,arguments[i]);
        }else{
            newArr.push(arguments[i]);
        }
    }
}
fn.apply(null,arr);
console.log(newArr);
```

## 9.求数组中：最小的x坐标、最大的y坐标 

````js
var arr = [
    [1, 2],
    [22, 55],
    [66, 99],
    [-11, -100],
    [88, 22],
    [101, 89],
    [99, 98],
    [21, 77]
]

//要求：求数组中 最小的x坐标    最大的y坐标
// forEach map some every filter
// map会返回一个新数组
var min = Math.min.apply(null, arr.map(function (e) {
    return e[0]
}));
var max = Math.max.apply(null, arr.map(function (e) {
    return e[1]; //以为是每一项的第二个才是y
}));

console.log(min,max);
````

## 10.小米（拓展，别人写的博客） 

[为发烧而生的面试题](http://www.cnblogs.com/aaronjs/p/3172112.html)

