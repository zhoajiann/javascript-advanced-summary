# JavaScript发展历程及语言特点  
#### （1）JavaScript发展历程  
1.前端JavaScript由ECMAScript（ES是JavaScript的语法标准）、DOM（文档对象模型）、BOM（浏览器对象模型）构成  
客户端JavaScript（宿主环境是浏览器）：ES（核心语言）、BOM和DOM是宿主对象（宿主环境提供的对象）即客户端JavaScript（宿主环境是浏览器）  
JavaScript在不同的运行环境，有着不同的内置宿主对象  
JavaScript 和 DOM 并不是不可分割的，它们的语言标准相互独立  
DOM 对 JavaScript 来说，是宿主对象，是语言中可更换的部分  
**ECMAScript 对 JavaScript 来说，是核心语言，是不可被替代的功能**  
**一个语言能做什么取决于运行平台（宿主环境），宿主环境提供宿主对象，宿主对象帮助完成不同的功能**  
服务端JavaScript（宿主环境是node.js）：ES（核心语言）、fs等是宿主对象（宿主环境提供的对象）  
2.JavaScript在客户端如何运行？**浏览器下载JavaScript脚本文件后，由浏览器 JavaScript 引擎解释执行。浏览器中的JavaScript引擎将JavaScript语言进行解释（解释成浏览器认识的）执行。**  
Chrome的JavaScript实现方式（JS引擎）是V8（浏览器不同其JS引擎也不同），Node也用V8解释执行  
不同的浏览器对JS的支持力度不同，即存在兼容  
3.ECMAScript每年更新一个版本  
ES5（2009年12月发布）当前网络上大部分用的是ES5  
ES6（ES2015，2015年6月发布）增加了许多新特性，并解决了很多ES5中的缺陷，逐渐流行开来   
……  
ES10（2019年6月发布）  
#### （2）	JavaScript语言特点  
##### 1.直译式脚本语言  
在宿主环境（浏览器、Node）中解释执行  
非编译语言， 不是在执行前编译成可执行文件或字节码  
解释执行——JavaScript，解释（转机器语言）一行执行一行，速度更慢  
编译执行——C语言，一次全部编译再执行，速度更快  
##### 2.弱类型、动态类型语言  
动态类型：写程序时不用给变量指定特定的数据类型  
弱类型：可以动态的更改变量的类型  
因此不适合开发大型项目，TypeScript解决此缺点  
##### 3.JavaScript语言特点  
ES5没有块作用域，即在{ }外仍可访问{ }内的变量
