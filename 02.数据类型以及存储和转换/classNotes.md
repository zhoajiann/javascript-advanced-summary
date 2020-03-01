# 数据类型存储和转换  

#### （1）	数据类型分类  
1.	基本（原始）数据类型：Number、String、Boolean、Null、Undefined  
引用（对象）数据类型：Object（Array、Function、Date等）  
2.	Typeof运算符：返回一个字符串，**表示未经计算的操作数的类型**，但无法区分Date()与Array()  
Typeof 变量名  or   Typeof ( 变量名 )   
Var a = 1; var b = ‘hello’; alert(a+b); typeof a  ——number（未经计算的操作数的类型）  
JavaScript中的变量没有类型，JavaScript中的数值有类型，变量可以随时持有任何类型的值，**typeof检测的是数据的类型，而变量与数据关联起来，即在对变量执行 typeof 操作时，得到的结果并不是该变量的类型，而是该变量持有的值的类型**  
特殊  **Typeof null  得”object”**  
	（2）	数据类型存储  
1.	变量声明：使用变量标识符，用于引用计算机内存地址，变量声明指向一块内存空间，用于保存数据  
变量赋值：向变量指向的内存空间中存放数据  
2.	堆栈内存  
栈内存:存储的值大小固定\由系统自动分配内存空间\空间小，运行效率高  
堆内存:存储的值大小不定，可动态调整\由程序员通过代码进行分配\空间大，运行效率相对低  
基本数据类型（5种）的变量存放在栈区，基本类型的值是不可变的  
Var name = “tracy”;name.toUpperCase();console.log(name);  ——“tracy”  
**引用数据类型的值是同时保存在栈内存和堆内存中的对象**   
3.	基本类型与引用类型的区别  
	a.	访问机制不同  
基本类型的值直接访问  
引用类型的值通过引用访问，不能直接访问（首先从栈中获取该对象的地址引用，再从堆内存中取得我们需要的数据）  
	b.	复制变量不同  
基本类型复制相互独立互不影响，各有各的栈内存  
引用类型复制的是栈区内保存的堆区的地址，即两个变量指向同一块堆内存  
	c.	比较变量不同  
基本类型是判断变量的值是否相等（值比较）  
引用类型是判断所指的内存空间（地址）是否相同（引用比较）  
	d.	参数传递不同  
**ECMAScript中所有函数的参数都是按值（栈内存绑定的值）来传递的**  
基本类型值：把变量里的数据值传递给参数，之后参数和变量互不影响  
引用类型值：吧对象的引用（地址）值传递给参数，参数和对象都指向同一个对象，相互影响  
	（3）	数据类型转换  
1.	转换为Number类型  
	a.	隐式转换  
|      值    |    结果|
|:-----------: | :-------------------------------------------|
|Undefined   |   NaN|
|Null        |  0|
|布尔值      |  false转换成0，true转换成1|
|数字        |  保持不变|
|字符串      |  解析字符串中的数字（忽略开头和结尾的空格），空字符转换成0，比如”2.15”转换成2.15|

用1快速转换  
b.	强制转换  
ParseInt()、parseFloat()、Number()  
c.	NaN  
表示一个没有意义、不正确的**数值**  
console.log( typeof  NaN);//Number  
**NaN != NaN**  
isNaN( ) 函数用来检测参数是否为 NaN 值，参数是 "NaN" 时返回 true，否则返回 false  
isNaN("123abc");//true  
```JavaScript
var a1;
if (a1 == a1) {
    console.log(a1 * 1);//NaN,执行(undefined==undefined)
} else {
    console.log(a1 + 1);
}
```
2.	转换为String类型  
	a.	隐式转换  
|      值    |    结果|
|:-----------: | :-------------------------------------------|
|Undefined   |   “undefined”|
|Null        |  “null”|
|布尔值      |  false转换成”false”,true转换成”true”|
|数字        |  例如3.15转换成”3.15”|
|字符串      |   输入即输出（不转换）|

b.	强制转换  
String()  
c.	“+”运算符左右两侧（有一侧就算）有字符串时为拼接运算符。  
 运算符等级相同时，从左往右计算。  
3.	转换为Boolean类型  
	a.	隐式转换  
|      值    |    结果|
|:-----------: | :-------------------------------------------|
|Undefined   |   false|
|Null        |  false|
|布尔值      |  输入即输出（不转换）|
|数字        |  0和NaN转换成false，其他数字转换为true|
|字符串      |    “”转换成false，其他字符串转换成true|

b.	强制转换  
Boolean()  
c.	逻辑运算符会将数据类型转换为布尔类型之后再做运算  
```javascript
Var a;
Console.log(a+1);//NaN
Console.log(!a+1);//2,
Console.log(!!a+1);//1
        var a;
        var b = a * 0;
        console.log(a);//undefined
        console.log(b);//NaN
        console.log(!b);//true
        if (b == b) {
            console.log(b * 2 + "2" - 0 + 4);
        } else {
            console.log(!b * 2 + "2" - 0 + 4);//26
        }
```
