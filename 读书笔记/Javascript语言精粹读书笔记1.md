---
layout: post
title: "Javascript 语言精粹读书笔记"
date: 2016-04-14 01:39
comments: true
tags: -读书笔记
tags: -Javascript 

---


###第一章  精华

+ 为什么要使用Javascript?
+ 分析Javascript中的精华，鸡肋，糟粕
	+ 精华：函数，动态对象，弱类型，富有表现力的面向对象表示法
	+ 鸡肋：基于全局变量的编程模型
	+ 使用Jslint



###第二章 语法

使用铁路图来表示语法

2.1. 空白<br/>
    + 避免使用/* */注释。使用//替代它
    + var 和 标识符之间的空格不可以去除
    
2.2. 标识符<br/>

2.3. 数字<br/>

+ 值NaN（Not a Number)表示一个不能产生正常结果的运算结果。它不等于任何值，包括自己。使用`isNaN(number)`来检测NaN
+ `Infinity`
+ Math方法

2.4. 字符串

+ 包围在单括号或者双括号里
+ 转义字符
+ 可通过+号去连接其他字符串，两个包含着完全相同的字符而且字符顺序也相同的字符串也被认为是相同的
+ 字符串有一些方法

2.5. 语句

+ 函数的私有变量
+ 条件语句（if 和switch)
+ 循环语句(while,for,do)
+ 强制跳转语句（break,return,throw)
	+ return，break语句不能在关键字和表达式里换行
+ for in 语句枚举一个对象的所有属性名（或键名）
+ `object.hasOwnProperty(variable)`确定这个属性名就是该对象成员，还是从其原型链里找到的
+ `try..catch`:try执行一个代码块，并捕获该代码块并抛出一个异常。Catch从句定义了一个新的变量，他将接收该异常对象

2.6 表达式

1. 表达式包括：
	+ 字面量值（比如字符串或者数字）
	+ 变量
	+ 内置的值（true,false,null,undefined,NaN,Infinity)
	+ 以new前导的调用表达式
	+ 以delete前导的属性存取表达式
	+ 包在圆括号中的表达式
	+ 以一个前缀运算符作为前导的表达式，或者表达式后面跟着：
	
		+ 一个插入运算符与另外一个表达式
		+ 三元运算符？后面跟着另外一个运算符，然后接一个：，再然后接第三个表达式
		+ 一个函数调用
		+ 一个属性存取表达式
	
2. 运算符优先级：加括号，防止出错

3. typeof运算符：产生的值有“number”，“string","boolean","undefined","function","object",如果运算符是null，那么返回一个object;

4. ！操作

5. +运算符:进行加法连接或者字符串连接

6. 短路问题：<br/>
   + 如果第一个运算符的值为假，那么运算符&&产生他的第一个运算符的值，否则产生第二个运算符的值<br/>
   + 如果第一个运算符的值为真，那么运算符||产生它的第一个运算符的值，否则它产生第二个运算符的值
   
7. 函数调用

8. 属性存取表达式

2.7 字面量

+ 数字字面量是一种方便指定新数组的表示法，详情见第六章
+ 正则表达式在第七章讲解

2.8. 函数

+ 函数字面量定义了函数值，他有一个自定义的名字，用于递归调用自己
+ 可以指定一个参数列表，这些参数将作为变量由调用时传递的实际参数（arguments)初始化
+ 函数的主题包括变量定义或者语句
函数更内容见第四章


### 第三章 对象

Javascript的简单类型包括数字，字符串，布尔值（true，false),null值和undefined值。其他所有的值都是对象。。数组、字符串和布尔值“貌似：对象，因为他们拥有方法，但它们是不可变的。Javascript中的对象是可变的键控集合。在Javascript中，数组是对象，函数是对象，正则表达式是对象，对象也是对象

Javascript中的对象是无类别的，它的新属性名字和值没有约束。对象适合用于收集和管理数据。对象可以包含其他对象，所以他们可以容易的表示成树形或图形结构

Javascript包括一个原型链特性，允许对象继承另一对象的属性，正确地使用能减少对象初始化的时间和内存消耗

3.1 对象字面量<br/>

+ 一种非常方便的创建新对象值的表示法，就是包围在一对花括号中的零或多个"名/值"对.
+ 对象是属性的容器，其中每一个属性都拥有名字和值，属性的名字可以是包括空字符串在内的任意字符串。属性值可以是除undefined值之外的任何值
+ 对象是可嵌套的

3.2检索

+ []或者.表示法
+ 检索一不存在的属性值会返回undefined

3.3 更新

 + 通过赋值语句来更新

3.4 引用

 + 对象通过引用来传递，他们永远不会被拷贝
 
3.5 原型

+ 原型连接在更新时是不起作用的，当我们对某个对象作出改变时，不会触及到该对象的原型
+ 委托
+ 原型关系是动态的关系<br/>
关于原型链的更多内容请看第六章

3.6 反射  <br/>
有两种方法去处理这些不需要的属性 

+ 方法一：让程序检查比剔除函数值，一般来说，做反射的目标是数据，因此你应该意识到一些值可能会是函数
+ 方法二：使用hasOwnProperty方法，它不会检查原型链

3.7  枚举
for in 语句遍历一个对象中所有的属性名。该枚举对象中会列出所有属性，所以有必要过滤掉你不想要的值。最常用的过滤器是hasOwnProperty方法，以及使用typeof来排除函数

	var name;
	for (name in another_stooge) {
		if(typeof another_stooge[name] !== 'function'）{    //typeof排除函数
			document.writeln(name +':' +another_stooge[name]);
		}
	}

但是注意，for in 返回的属性顺序是不确定的，可以把你想要的顺序放在一个数组里，然后通过for来得到属性

3.8 删除
 
delete 运算符可以用来删除对象的属性，它会移除对象中确定包含的属性，不会触及原型链中的对象
它可能让来自原型链的属性浮现出来（委托原理）

3.9 减号全局变量污染

+ 全局变量削弱了程序的灵活性，应该避免
+ 使用闭包来进行信息隐藏的方式，它可以有效减少全局污染的方法


		var a = 1;
		var b = function（）{
			console.log(this.a);
			var hehe =function （）{
				console.log(this.a);
			}     //不知道哪里有错
		}

###第四章  函数
编程就是将一组需求分解成一组函数与数据结构的技能


4.1 函数对象 <br/>

+ 每个函数在创建时附有两个附加的隐藏属性；函数的上下文和实现函数行为的代码
+ 函数可以存放在变量，对象和数组中。函数可以被当做参数传递给其他函数，函数也可以返回函数。而且函数是对象，可以拥有方法
+ 函数可以被调用（与众不同）

4.2 函数字面量

函数对象可以通过字面量方法来创建：

		// 创建一个名为add的变量，并用来把两个数字相加的函数赋值给他
		var add = function(a,b） {
			return a+b;
		};
函数字面量包括四个部分：
  
 + 保留字function
 + 第二部分是函数名，可以被省略（匿名函数）
 + 包围在圆括号中的参数，在调用时初始化为实际提供的函数的值
 + 包围在花括号中的一组语句。这些语句是函数的主体，他们在函数被调用时执行

函数字面量可以出现在任何允许表达式出现的地方。函数可以被定义在一个其他函数中，一个内部参数自然可以访问自己的参数和变量，同时它也能方便的访问它被嵌套在其中的那个函数的参数与变量。通过函数字面量创建的函数对象包含一个连到外部上下文的连接。
 
4.3 调用
调用一个函数将暂停当前函数的执行，传递控制权和参数给新函数。除了声明时定义的形式参数，每个函数会接受两个的参数：this,arguments.参数this在面向对象编程中极为重要，它取决于调用的模式
不同模式在初始化关键函数参数this上会有差异

调用运算符是跟在任何产生一个函数值的表达式之后的一对圆括号。圆括号内可包含0个或者多个用
括号隔开的表达式。每个表达式产生一个参数值。每个参数值被赋予函数声明时定义的形式参数名.

实参数>形参数：超出的参数值会被忽略
形参数>实参数:缺少的值会被替换为undefined


+ 方法调用模式
   + 当一个函数被保存为对象的一个属性时，我们称它为方法，当一个方法被调用时，this被绑定到该对象
   + 如果一个调用表达式包含一个属性存取表达式，那么它当做一个方法来调用
   + 方法可以通过使用this去访问对象，所以他能从对象中取值或修改该对象。通过this可取的他们所属属性对象上下文的方法称为公共对象
     
			//创建myObject.它有一个value属性和increment方法
			//increment方法接受一个可选的参数，如果参数不是数字，那么默认使用数字1

			var myObject = {
				value:0;
				increment:function(inc) {
					this.value += typeof inc === 'number' ? inc:1;
				}
			};
			myObject.increment();   
			document.writeln(myObject.value);  //1
			myObject.increment();
			document.writeln(myObject.value);  //3
+ 函数调用模式
	+ 当一个函数并非对象是属性时，那么他被当做一个函数来调用,当函数以此模式调用时，this被
绑定到全局变量。这是Javascript语法设计上的一个错误，如果语言设计正确，this应该绑定到外部函数的this变量。
			var sun = add（3,4);

	+解决方案:
		
		//给myObject增加一个double方法。 
		myObject.double = function(){
			var that = this;  //解决方法
			var helper = function () {
				that.value = add(that.value,that.value);
			};
			helper();   //以函数的形式调用helper.
		};
		//以方法的形式调用double.	
		myObject.double();
		document.writeln(myObject.getValue());    //6
	
+ 构造器模式

	+ 如果在一个函数前面带上new来调用，那么将创建一个隐藏连接到该函数的propertype成员的新对象，同时this会绑定到那个新对象上
	+ new前缀也会改变return语句的行为
		
			//创建一个名为Quo的构造器函数。它构造一个带有status属性的对象
			var Quo = function (string) {
					this.status = string;
			};
			//给	Quo的所有实例提供一个名为get_status的公共方法
			Quo.prototype.get_status = function() {
				return this.status;
			};
			//构造一个Quo实例
			var myQuo = new Quo("confused");
			document.writeln(myQuo.get_status());  //令人困惑

	+ 结合new 前缀调用的函数称为构造器函数。按照约定，它们保存在以大写格式命名的变量里。如果调用构造器函数时没有在前面加上new可能会发生非常糟糕的事情
	
+ apply调用模式

	+ Javascript是一门函数式的面向对象编程语言，所以函数拥有方法
	+ apply方法让我们构建一个参数数组并用其去调用其他函数，他也允许我们选择this的值。
	+ apply接受两个参数，第一个是将被绑定给this的值，第二个就是参数数组

	 	
			//构造一个包含两个数字的数组，并把他们相加
			var array = [3,4];
			var sum = add.apply(null,array); //sum值为7
			//构造一个包含status成员的对象
			var statusObject = {
				status:'A-OK'
			};
			//statusObject并没有继承自Que.prototype,但我们可以在statusObjects上调用-get_status方法，尽管statusObject并没有一个名为get_status的方法
			var status = Quo.prototype.get_status.apply(statusObject);
			//status值为'A-OK'

4.4  参数

argument拥有length属性，但他缺少所有的数组方法

4.5 返回

+ 当一函数被调用，它从第一个语句开始执行，遇到关闭函数体的}时结束。那使得函数把控制权交还给调用该函数的程序部分
+ reutrn语句可用来使函数提前返回，当return被执行时，函数立即返回而不是执行余下的语句
+ 一个函数总会返回一个值，如果没有指定返回值，则返回undefined
+ 如果函数以在前面加上new前缀的方式来调用，则返回值不是一个对象，则返回this(该新对象）


4.6 异常

Js异常处理机制：异常是干扰程序的正常流程的非正常（但并非完全是出乎意料）的事故。当查出这样的事故时，你的程序应该抛出一个异常

	var add = function(a,b) {
		if(typeof a !=='number' || typeof b !== 'number') {
			throw {
				name:'TypeError',
				message:'add needs numbers'
			};  //throw语句中断函数的执行，抛出一个exception对象
		}
		return a+b;
	}
该expection对象将被传递到一个try语句的catch从句

    
 	//构造一个try_it函数，用不正确的方式调用之前的add函数
	var try_it = function () {
		try{
			add("seven");
		} catch(e) {
			document.writeln(e.name+':'+e.message);
		}
	}   //如果try代码块抛出一个异常，控制权就会跳转到它的catch函数



4.7 给类型添加方法
通过给Function.propertype增加方法来使得该方法对所有函数有用

	Function propertype.method = function (name,func) {
		this.propertype[name] = func;
		return this;
	};
	//通过给Function.propertype增加method,就不必键入propertype这个属性值
	
	//通过给Number.propertype增加一个interge方法来改善它，它会根据数字的正负来判断是
	使用Math.ceiling还是Math.floor
	Number.method9'integer',function() {
		return Math[this<0?'ceiling':'floor'](this);
	});
	document.writeln((-10/3).integer());  //3


还有其他一些例子，不一个个细说


4.8 递归

递归函数是会直接或者间接调用自身的一种函数	
不太懂

4.9 作用域
作用域控制着变量与参数的可见性及生命周期，减少命名冲突，提供了自动内存管理

+ Js有函数作用域，那意味着定义一在函数中的参数和变量在函数外面是不可见的，定义在函数作用域内部的变量在执行借宿后会被销毁
+ 最好在函数体的顶部声明函数中可能用到的所有变量
		 
		var foo =function () {
			var a = 3,b=5;
			var bar = function(){
				var b = 7,c = 11;
			//此时，a=3,b=7,c为11
				a += b+c;
			//此时，a为21，b为7，c为11
			}；
			//此时，a为3，b为5,而c没有定义
			bar();
			//此时，a=21,b=5;
		};

4.10 闭包

+ 作用域的好处是内部函数可以访问定义他们外部函数的参数和变量（除了this和argument)
+ 函数可以访问它被创建时所处的上下文环境，成为闭包

	
		//定义一个函数，它设置一个DOM节点为黄色，然后把它渐变为白色
		var fade = function (node) {
			var level = 1;
			var step = function () {
				var hex = level.toString(16);
				node.style.backgroundColor = '#FFFF' +hex+hex;
				if(level<15) {
					level +=1;
					setTimeout（step,100);
				}
			};
			setTimeout(step,100);
	    };
	    fade(document.body);

4.11 回调（callbacks)

+ 函数可以让不连续的事情的处理变得更容易
  
+ 更好的方式是发布异步的请求，提供一个当服务器的响应到达时将被调用的回调函数，异步的函数立即返回，这样客户端不会阻塞

		
		request = prepare_the_request();
		send_request_asynchronously(request,function(response) {
			display(response);
		});
		//我们传递了一个函数作为参数给send_request_asynchronously函数，它将在收到响应时被调用

4.12 模块（Module)

我们可以通过使用函数和闭包来构造模块。模块是一个提供接口却并隐藏状态与实现的函数或对象，通过使用函数去产生模块，我们可以完全去除全局变量的使用


eg:
          
		String.method('deentityify',function() {
		//字符实体表。它映射字符实体的名字到对应的字符
			var entity = {
				quot: '"',
				lt:   '"',
				gt:   '>'
			};
		//返回deentityfy方法
			return function () {
		//这才是deentityify方法。它调用字符串的replace方法
		//查找'&'开头和';'结束的子字符串。如果这些字符可以在字符实体表中找到
		//那么就将该字符实体替换为映射表中的值。它用到了一个正则表达式	
				return this.replace(/&（[^&;]+0；/g,
					function (a,b) {
						var r = entity[b];
						return typeof r === 'string'?r:a;
					}
				);
			}；
		}());
模块模式利用了函数作用域和闭包来创建绑定对象和私有成员的关联，在这个例子中，只有deentifyify方法有权访问字符实体表这个数据对象

模块模式的一般形式是：一个定义了私有变量和函数的函数；利用闭包创建可以访问私有变量和函数的特权函数；最后返回这个特权函数，或者把它们保存到一个可以访问到地方

对于应用程序的封装，或者构造其他单例对象，模块模式非常有效

	eg:模块模式也可以用来产生安全的对象
	var serial_maker = function () {

		//返回一个用来产生唯一字符串的对象
		//唯一字符串由两个部分组成：前缀+序列号
		//该对象包含一个设置前缀的方法，一个设置序列号的方法
		//和一个产生唯一字符串的gensym
		var perfix = '';
		var seq = 0;
		return {
			set_prefix:function (p) {
				prefix = String(p);
			},
			set_seq:function () {
				seq = s;
			},
			gensym:function () {
				var result = prefix +seq;
				seq += 1;
				reutrn reslut;
			}
		};
	};
	var seqer = serial_maker();
	seqer.set_prefix（'Q');
	seqer.set_seq(1000);
	var uniques = seqer.gensym();  //unique is 'Q1000'

4.13 级联

有一些方法没有返回值，如果我们让我们让这些方法返回this而不是undefined，就可以返回级联

在一个级联中，我们可以在单独一条语句中依次调用一个对象的很多一个方法

级联可以产出具有很强表现力的接口。它也能帮助控制那种构造图一次做太多事情的接口的趋势

4.14 套用

套用允许我们将函数与传递给它的参数相结合会产生出一个新的函数

4.15 记忆
函数可以用对象去记住先前操作的结果，从而能避免无谓的运算（返回已经缓存结果）。这种优化被称为记忆

