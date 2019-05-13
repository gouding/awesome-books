# JS中数据类型和数据结构

## 目录 


### [基本概念](#基本概念)

>javascript是一种弱类型或者说是一种动态类型语言。意味不用提前声明变量的类型，程序fctffp程中，类型会被自动确定，也意味着你可以使用一个变量去存储不同类型的值，嗨不嗨（其实这是另一种痛苦）。


### [数据类型](#数据类型)

### js中定义了`7种`标准数据类型

>#### 6种原始基本类型(值类型)
- [Boolean](#Boolean类型)
- [String](#String类型)
- [Number](#Number类型)
- [Null](#Null类型)
- [Undefined](#Undefined类型)
- [Symbol(ES6新定义)](#Symbol类型)

>#### 1种对象类型（引用类型）
- Object
  - [Object对象](#Object对象)
  - [Array](#Array类型)
  - [Function](#Function类型)
  - [RegExp](#RegExp类型)
  - [Date](#Date类型)

### 原始值（值类型）

>#### Boolean类型

布尔用于判断逻辑，只有两个值。即`true`和`false`。true和false也可用相应数字1和0进行进行判断（只能做值比较，不能做类型比较）

```
  let boo = true
  boo == 1 // true
  boo === 1 // false
  boo = 0
  boo == false // true
```

>#### String类型

字符串类型是最常见的类型，它有很多属性和方法,最常用的是`length`、`search`、`toLocaleUpperCase`、`toLocaleLowerCase`、`substr`、`substring`、`join`等。字符串是值类型，也就是一个变量一旦赋了初始值，若对它进行修改，那么其实是在内存的栈上重新复制了一个副本，然后把该值赋值给该变量，而之前的变量由于没有变量指向它，它会被内存进行回收。
```
let str = 'abc'
let str2 = str
str = '123'
str == str2   //false 任何的赋值操作都是重新拷贝一份副本而不是对原始值进行操作
```

>#### Number类型

Number表示数字类型，包含整数和浮点数（浮点数是指小数且小数点后必须有一个数字）两种值。

数字类型有一个特殊的类型NaN(非数字类型)
- 有关NaN的操作，都会返回NaN
- NaN不等于自身
```
  let no = NaN
  no == NaN   // false
```
isNaN()函数可用于检查传入的参数是否是非数字值
```
let no = NaN
isNaN(no) // true
isNaN(1)  // false
```

>#### Null类型

对于业务逻辑来说，Null跟Undefined的作用差不多，都可用于空值逻辑判断,可用`==`进行判断，它们的功能一样。但是它们之间也有一些区别，Null是指的空对象指针，即你引用了一个本身并不存在的对象。该变量不指向任何对象。
```
let foo = null
foo   // null
```

>#### Undefined类型

undefined它是一个全局对象的一个属性，功能跟null差不多，对值进行逻辑判断,它是表示声明了一个变量，但是并未对它进行赋值
```
let foo 
console.log(foo)  //  undefined
typeof null   // "object" 因为一些js的历史原因返回的是object
typeof undefined  // "undefined"
null == undefined // true
null === undefined // false
isNaN(1+null) // false
isNaN(1+undefined)  // true
```

### 对象（引用类型）

>#### Object对象

对象是无序键值对（key-value）的集合，
```
let person ={
  name:'denzel',
  age:18,
  'w-eight':101
}
//取值一
person.name   //denzel
//取值二
person['age'] //18    
person['w-eight']   // 101 若key中出现横线，要使用下标的形式进行访问

delete person['age']
person.age //undefined

'name' in person  //false  该key已经删除
////////
person.age = undefined
person.age   //undefined
'name' in person //true //这个上边不一样  只是值不存在，但key是存在的
```

object对象天生支持遍历获取每一个值，使用`for-in`
```
let items ={name:'denzel',age:18,weight:101,height:177}
for(let item in items){
  console.log(`${item}--${items[item]}`)
}
typeof items //'object'
```

>#### Array类型

数组类型
```
let array =[1,2,3,4,5]
let arrar2 =[6,7]
array.length  //5
array[1]  //2

array.concat(array2)  //1 2 3 4 5 6 7 数组相连
```
数组还有很多属性和方法具体可参考[MDN Array](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)

>#### Function类型

函数类型 即使用关键字申明
```
let fn = function (a,b){
  return a+b
}

fn(2,3) //5
typeof fn // 'function'

```

>#### RegExp类型

正则表达式，是对字符串执行模式匹配的工具
常用的匹配关键修饰符

| 修饰符 |  描述 |
| ----- | ---- |
| i | 执行对大小写不敏感的匹配 |
| g | 执行全局的匹配 |
| m | 执行多行匹配 |

```
let str = 'hello denzel,hello,it\' me'
str.replace(/hello/g,'hi')  // 'hi denzel,hi it\'s me'
```
具体可参考
- [MDN 正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
- [我博客-最全正则表达式大全](http://dinglo.top/2019/04/28/reg/)

>#### Date类型

日期类型，取自于1970年1月1日开始的时间
```
var date1 = new Date('December 17, 1995 03:24:00');
// Sun Dec 17 1995 03:24:00 GMT...

var date2 = new Date('1995-12-17T03:24:00');
// Sun Dec 17 1995 03:24:00 GMT...

console.log(date1 === date2);
// expected output: false;

console.log(date1 - date2);
// expected output: 0

//获取一个不tgtjr字符串
let str = (+new Date()).toString()  //"1557727727556"
```
具体可参考[MDN Date](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)



