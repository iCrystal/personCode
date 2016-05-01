### 第五章  继承
Javascript是一门基于原型的语言，对象直接从其它对象继承

5.1 伪类

5.2 对象说明符

5.3 原型
一个新的对象可以继承旧对象的属性


	var myMammal = {
		name:'Herb the Mammal',
		get_name: function () {
			return this.name;
		},
		says: function () {
			return this.saying|| '';
		}
	};
	var myCat = object.beget(myMammal);
	myCat.name = 'Henrietta';
	myCat.saying = 'meow';
	myCat.purr = function(n) {
		var i, s = '';
		for(i = 0;i<n;i += 1) {
			if (s) {
				s +='-';
			};
			s += 'r';
		}
		return s;
	};
	myCat.get_name = function () {
		return this.says+ '' + this.name + ''+ this.says;
	};

这是一种差异化继承

5.4 函数化
模块模式的应用
构建一个将产生对象的函数开始









###第六章： 数组
数组是一段线性分配的内存，它通过整数去计算偏移并访问其中的元素。数组是很快的数据结构，但js没有像数组一样的数据结构，反而js提供了一些类数组特性的对象

6.1 数组字面量

数组字面量是一种很方便地创建新数组的表示法

两种创建方法：

var numbers = ['zero','one','two','three'];

或者

var number_object = { '0':'zero','1':'one'};

第一种继承自array.propertype,第二种继承自Object.propertype,所以第一种有length属性，第二种没有

Javascript允许数组包含任意混合的值


6.2 长度

+ Js数组的length属性时没有上限的，不会发生数组边界错误
+ 把下标指定为一个数组的当前length，可以附加一个新元素到该数组的尾部
+ push也可以完成往数组中添加新元素

6.3 删除

+ delete运算符可以用来从数组中移除元素,但是只是数组的值变为undefined,这个下边还在
		
		delete numbers[2];
		//numbers['zero','one','undefined','shi','go']

+ 可以用splice可以删除元素并将他们替换为其他元素


6.4 枚举

1. for in 语句。但是无法保证属性顺序
2. for语言便利


6.5 混淆的地方
当属性名是小而连续的整数时，应该使用数组；否则应该使用对象

自定义is_array（）函数区别数组和对象


	var is_array = function (value) {
		return value &&
			typeof value === 'object'&&value.constructor === Array;
	};


6.6  方法
数组其实就是对象，可以给一个单独的数组添加对象

6.7  维度




###第七章 正则表达式

正则表达式是一门简单语言的语法规范，它以方法的形式被用于对字符串中的信息进行查找。替换和提取操作


正则表达式是怎么工作的?

+ ^字符:表示这个字符串的开始，用来防止exec跳过不像URL的前缀
+ （？：（[A-Za-z]+):)？ 这个协议匹配一个协议名，但仅当它之后跟随一个：（冒号）的 时候才匹配。（？....)表示一个非捕获型分组。后缀？表示这个分组是可选的


第八章 方法
Javascript包含了少量可用在标准类型上面的标准方法


Array
	
+	array.concat()
+	array.join()
+	array.pop()
+	array.push()
+	array.reverse()
+	array.shift()
+	array.slice()
+	array.sort()
+	array.splice()
+	array.unshift()

Function

+ function.apply()

array方法调用函数function,传递一个将绑定到this上的对象和一个可选的参数数组。apply方法被用在apply调用模式中


Number

+ number.toExponentia
+ number.toFixed()
+ number.toPrecision()
+ number.toString()

Object

+ object.hasOwnPropertype()
 

RegExp

+ regexp.exec()
+ regexp.test()

String()

+ string.charAt()
+ string.charCodeAt()
+ string.concat()
+ string.indexOf()
+ string.lastIndexOf()
+ string.localCompare()
+ string.match()
+ string.replace()
+ string.search()
+ string.slice()
+ string.split()
+ string.substring()
+ string.toLocalLowerCase()
+ string.toLocalUpperCase()
+ string.toLowerCase()
+ string.toUpperCase()
+ string.formCharCode()







































附录E：JSON


> Javascript对象表示法（Javascript Object Notation,简称JSON)是一种轻量级的数据交换格式。它基于Javascript的对象字面表示法。那是Javascript最精华的部分之一。尽管只是Javascritpt的子集，但它与语言无关。它可以被用在所有的现代编程语言编写的程序中交换数据，只是一种文本格式，所以可以被机器阅读

1 JSON语法
2.安全使用JSON
3 一个JSON解释器