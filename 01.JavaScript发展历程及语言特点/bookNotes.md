# 《深入理解JavaScript》第一部分

#### 1. 语句和表达式

语句“做事情”，程序就是一系列语句的集合

表达式返回值，它们通常是函数的参数，或是赋值的右边部分，**表达式可以用在所有需要语句的地方**

#### 2. 标识符与变量名

变量的名字就是一个标识符，**标识符区分大小写**

#### 3. 原始值和对象

原始值包括布尔值、数字、字符串、null和undefined

其他的值都是对象

这两者之间最主要的区别在于它们的比较方式

```javascript
var obj1 = {};
var obj2 = {};
obj1 === obj2;//false
obj1 === obj1;//true
```

每个对象都有唯一的标识且只（严格的）等于自己；相反，所有的原始值，只要编码相同，则被认为相等。

原始值具有以下特点：

（1）按值进行比较

```javascript
3 === 3;//true
"abc" === "abc";//true
```

（2）不可改变

其属性不能被改变、添加或移除

```javascript
var str = "abc";
str.length = 1;//尝试改变length属性
console.log(str.length);//3
str.foo = 3;//尝试添加属性foo
console.log(str.foo);//undefined
```

#### 4. null

typeof  value 它的返回值会是一个表示这个值“类型”的**字符串**

```javascript
typeof null;//object
null instanceof Object;//false
```

typeof null返回object是一个bug，并不代表null是一个对象

#### 5. 数字

JavaScript中所有数字都是浮点数

#### 6. 函数

函数表达式会产生一个值，因此可以将函数作为参数直接传递给另外的函数

实参比形参少的情况下，丢失的参数会得到undefined这个值

arguments不是数组，只是类似于数组。不能移除它的元素，也不能对它调用数组的方法

#### 7. 变量提升

所有变量声明都会被提升：声明会被移动到函数的开始处，而赋值则仍然会在原来的位置进行

#### 8. 对象

对象的每个属性都是一个（键，值）对

键名都是字符串，而值可以是JavaScript的任意值

**以函数作为值的属性被称为方法**

使用this对调用函数的对象进行引用

使用in运算符检查属性是否存在

```javascript
var jane = {
	name:"jane";
	discribe:function(){
		return "person name" + this.name;
	}
};
"name" in jane;//true
"age" in jane;//false

```



#### 9. 数组

```javascript
var arr = ['a','b','c'];
arr[0];//'a'
a[0] = 'x';
arr;//['x','b','c']
arr.length;//3
arr[arr.length] = 'd';
arr;//['x','b','c','d']
'c' in arr;//true
arr.length;//4
arr.length = 1;
arr;//['x']

```