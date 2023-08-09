---
layout: post
title:  "Javascript代码简写技巧"
tags: Javascript 编程
---

### 关于只用6个字符+!([])写Javascript代码
```
    false       ->  ![]
    true        ->  !![]
    undefined   ->  [][[]]
    NaN         ->  +[![]]
    0           ->  +[]
    1           ->  +!+[] , +!![]
    2           ->  !+[]+!+[]
    '10'        ->  [+!+[]]+[+[]]

    Number, 23          ->  +['23']
    String, 'filter12'  ->  ['filter']+['12']
    Function, ƒ filter() { [native code] }   ->  []["filter"]
    eval        ->  []["filter"]["constructor"]( CODE )()
    window      ->  []["filter"]["constructor"]("return this")() , Function("return this")()

    Infinity    -> +(+!+[]+(!+[]+[])[!+[]+!+[]+!+[]]+[+!+[]]+[+[]]+[+[]]+[+[]]) // +"1e1000"
    RegExp /false/ ->   Function("return/"+false+"/")()

    'a':   (false+"")[1],
    'b':   ([]["entries"]()+"")[2],
    'c':   ([]["flat"]+"")[3],
    'd':   (undefined+"")[2],
    'e':   (true+"")[3],
    'f':   (false+"")[0],
    ...
    'NaNfunction flat() { [native code] }':   (NaN+[]["flat"]),
    '/(?:)/':   (RegExp()+""),
```
### 逻辑空赋值（??=）
逻辑空赋值运算符（x ??= y）仅在 x 是空值（null 或 undefined）时对其赋值
```
const a = { duration: 50 };

a.duration ??= 10;
console.log(a.duration);
// Expected output: 50

a.speed ??= 25;
console.log(a.speed);
// Expected output: 25
```
### 使用「OR ( || ) 短路求值」的逻辑，来给定一个默认值
```
imagePath = getImagePath() || 'default.jpg';
```
### 使用「AND(&&)短路求值」, 只在前面值为真时才调用某个函数
```
isLoggedin && goToHomepage();
```
### 使用数组解构赋值，为多个变量赋值,或交换变量的值
```
//为a,b,c分别赋值
let [a, b, c] = [5, 8, 12];
//交换两个变量的值
[x, y] = [y, x];
```
### 模板字符串和多行字符串
```
console.log(`You got a missed call from ${number}
 at ${time}`);
```
### 对于多值匹配，我们可以把所有的值放在数组中，使用数组提供的indexOf()或includes()方法来简写

```
// 常规写法
if (value === 1 || value === 'one' || value === 2 || value === 'two') { 
     // 执行一些代码
} 

// 简写1
if ([1, 'one', 2, 'two'].indexOf(value) >= 0) { 
    // 执行一些代码 
}
// 简写2
if ([1, 'one', 2, 'two'].includes(value)) { 
    // 执行一些代码 
}
```
### 对象属性分配
如果变量名和对象的属性名相同，那么我们可以在对象的中只写变量名，而不用同时写出属性名和属性值（变量的值）。JavaScript会自动将属性名设置为与变量名相同，并将属性值分配为变量值。

```
let firstname = 'Amitav'; 
let lastname = 'Mishra'; 

// 常规写法 
let obj = {firstname: firstname, lastname: lastname}; 

// 简写 
let obj = {firstname, lastname};
```
### 杂项
```
let total = +'453'; //字符串转整数
let average = +'42.6'//字符串转浮点数
'sorry\n'.repeat(100);// 字符串重复, 想跟你说100声抱歉！
const power = 4**3; // 64 幂
const floor = ~~6.8; // 6, 双NOT位运算符（~~）实现 Math.floor()，但注意对负浮点数结果不同
~~-6.8 === -6 ; Math.floor(-6.8)=== -7

const arr = [2, 8, 15, 4]; 
Math.max(...arr);  // 最大值 15 
Math.min(...arr);  // 最小值 2

a=[1,2];b=[3,4];[...a,...b] //[1,2,3,4] array concat
```

### 多层次对象的深拷贝
```
let obj = {x: 20, y: {z: 30}}; 

// 常规写法，递归
const makeDeepClone = (obj) => { 
  let newObject = {}; 
  Object.keys(obj).map(key => { 
    if(typeof obj[key] === 'object'){ 
      newObject[key] = makeDeepClone(obj[key]); 
    } else { 
      newObject[key] = obj[key]; 
    } 
  }); 
 return newObject; 
} 
const cloneObj = makeDeepClone(obj); 

// 特殊情况下(对象中属性值没有函数、undefined或NaN的情况下)的简写
const cloneObj = JSON.parse(JSON.stringify(obj));

// 单层对象（无嵌套对象）情况下的简写
let obj = {x: 20, y: 'hello'};
const cloneObj = {...obj};
```
