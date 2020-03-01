# 包装对象和数据类型转换

#### （1）  包装对象  

\1. 对象：一个单独拥有**属性**和**方法**的实体  

为什么基本数据类型可以使用方法？包装对象的存在

\2. 包装对象：存取**字符串、数字或布尔值**的属性时创建的**临时对象**称为包装对象

没有undefined和null——会报错

用来处理属性的引用，**一旦属性引用结束，包装对象就会销毁**

![img](file:///C:/Users/LEN/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

\3. 包装类型和引用类型的区别：主要区别是对象的生存期

\4. 

```javascript

```

Var str = ‘hello’;

Var stt = new String(‘hello’);

Console.log(typeof str); //string

Console.log(typeof str);//object

Stt = null;//手动销毁堆内存中的对象

```

```

（2）  数据类型转换

\1. 转换为Object类型

对象转为自身

Undefined和null转换为空对象{}

String/number/boolean转换为包装对象

强制转换：Object()

\2. Object 转换为 Number

先调用 valueOf() 方法，结果为原始值，返回；

再调用 toString() 方法，结果为原始值，返回；

原始值转换为 Number 类型

![img](file:///C:/Users/LEN/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg) 

A = [] —— 0

a = [2] —— 2

A = [2,3] ——NaN

\3.   Object 转换为 String

先调用 toString() 方法，结果为原始值，返回；

再调用 valueOf() 方法，结果为原始值，返回；

原始值转换为 String 类型

![img](file:///C:/Users/LEN/AppData/Local/Temp/msohtmlclip1/01/clip_image011.jpg) ![img](file:///C:/Users/LEN/AppData/Local/Temp/msohtmlclip1/01/clip_image013.jpg) ![img](file:///C:/Users/LEN/AppData/Local/Temp/msohtmlclip1/01/clip_image015.jpg)

A = [] —— “”

a = [2] —— “2”

A = [2,3] —— “2,3”

\4. Object 转换为 Boolean

**任意对象转换为布尔值为** **true****，包括空对象**

真值与假值：在 JavaScript 中，真值指的是在强制转换布尔值时，转换后的值为真的值。所有值都是真值，除非它们被定义为假值（即除 false、0、""、null、undefined 和 NaN 以外皆为真值）。

\5. 练习

分析 console.log([] == []) 输出的值  false

两个值都是对象 (引用值) 时，比较的是两个引用值在内存中是否是同一个对象。 虽然左操作数和右操作数同为空数组， 但此 [] 非彼 []，在内存中是两个互不相关的空数组， 所以结果为 false。

分析 console.log([] == ![]) 输出的值  true

涉及到了 JavaScript 的运算符优先级 、宽松相等（即 ==）的判断过程以及类型转换①等号右边有 ! ，优先级比 == 更高，优先计算右边的结果。 [] 为非假值，所以右边的运算结果为 false，即：![] ==> false② == 的两边分别是 object 和 boolean 类型的值，把 object 转换成 number 类型，需要对 object 进行 ToNumber 操作，即Number([].valueOf()) ==> 0。boolean 类型的值时先把这这个值转换成 number 类型，右边转换成了 0，即Number(false) ==> 0

var str = "hello"

var stt = new String("hello");

str == stt  ——true