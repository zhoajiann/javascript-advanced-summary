# 《你不知道的JavaScript（中卷）》

## · 第一章  类型

### 1. 内置类型

JavaScript有七种内置类型：

* 空值（null）
* 未定义（undefined）
* 布尔值（boolean）
* 数字（number）
* 字符串（string）
* 对象（object）
* 符号（symbol，ES6中新增）

function（函数）也是JavaScript的一个内置类型，它实际上是object的一个“子类型”。具体来说，函数是“可调用对象”，它有一个内部属性[[call]]，该属性使其可以被调用

### 2. 值和类型

JavaScript中的变量是没有类型的，只有值才有

变量可以随时持有任何类型的值

**在对变量执行typeof操作时，得到的结果并不是该变量的类型，而是该变量持有的值的类型，因为JavaScript中的变量是没有类型的**

typeof运算符总会返回一个字符串

```javascript
typeof typeof 123;//"string"
```

### 3. undefined 与 undeclared

已在作用域中声明但还没有赋值的变量，是undefined的

相反，还没有在作用域中声明过的变量，是undeclared的

```javascript
var a;
a;//undefined
b;//ReferenceError: b is not defined

var c;
typeof c;//"undefined"
typeof d;//"undefined"
```

d虽然是一个undeclared变量，但typeof并没有报错，这是因为typeof有一个特殊的安全防范机制

```javascript
if(typeof atob === "undefined"){
	atob = function(){
		...
	};
}
```

与undeclared变量不同，访问不存在的对象属性（甚至是在全局对象window上）不会产生ReferenceError错误

ReferenceError（引用错误）对象代表当一个不存在的变量被引用时发生的错误

***

## · 第二章   值

### 1. 数组

在JavaScript中，数组可以容纳任何类型的值，可以是字符串、数字、对象（object）、甚至是其他数组（多维数组的实现）

对数组声明后即可向其加入值，不需要预先设定大小

```javascript
var a = [1,'2',[3]];
a.length;//3
a[0] === 1;//true
a[2][0] === 3;//true
```

使用delete运算符可以将单元从数组中删除，但是请注意，**单元删除后，数组的length属性并不会发生变化**

```javascript
var a = [];
a[0] = 1;
//注意此处没有设置a[1]单元
a[2] = 3;
a[1];//undefined
a.length;//3
```

数组通过数字进行索引，数组也是对象，可以包含字符串键值和属性**（但这些并不计算在数组长度内）**

```javascript
var a = [];
a[0] = 1;
a["foobar"] = 2;
a.length;//1
a.foobar;//2
a["foobar"];//2
```

**如果字符串键值能够被强制类型转换为十进制数字的话，它就会被当做数字索引来处理**

```javascript
var a = [];
a["13"] = 42;
a.length;//14
```

将类数组转换为数组

```javascript
function foo(){
	var arr = Array.prototype.slice.call(arguments);
	arr.push("bam");
	console.log(arr);
}
foo("bar","baz");//["bar","baz","bam"]
```

### 2. 字符串

JavaScript中的字符串时不可变的，而数组是可变的

字符串不可变是指字符串的成员函数不会改变其原始值，而是创建并返回一个新的字符串。而数组的成员函数都是在其原始上进行操作

### 3. 数字

JavaScript没有真正意义上的整数

JavaScript中的“整数”就是没有小数的十进制，42.0即等同于“整数”42

JavaScript中的数字类型是基于IEEE754标准来实现的，该标准也被称为“浮点数”

JavaScript使用的是“双精度”格式（即64位二进制）

* tofixed(...)方法可指定小数部分的显示位数

```javascript
var a = 42.95;
a.tofixed(0);//"43"
a.tofixed(1);//"42.6"
a.tofixed(2);//"42.95"
a.tofixed(3);//"42.950"
//注意输出结果是给定数字的字符串形式
```

* toPrecision(...)方法用来指定有效数位的显示位数

```javascript
var a = 42.95;
a.toPrecision(1);//"4e+1"
a.toPrecision(2);//"43"
a.toPrecision(3);//"42.6"
a.toPrecision(4);//"42.59"
a.toPrecision(5);//"42.590"
```

对于（.）运算符需要给予特别注意，因为它是一个有效的数字字符， 会优先识别为数字常量的一部分，然后才是对象属性

```javascript
//无效语法
42.tofixed(3);//SyntaxError
//有效语法
(42).tofixed(3);//"42.000"
0.42.tofixed(3);//"0.420"
42..tofixed(3);//"42.000"
```

