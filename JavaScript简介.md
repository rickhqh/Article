#  JavaScript简介

# 1、起源

在**1995**年时，由**Netscape**公司的**Brendan Eich**，在网景导航者浏览器上首次设计实现而成。Netscape在最初将其脚本语言命名为LiveScript，因为Netscape与Sun合作，网景公司管理层希望它外观看起来像Java，因此取名为JavaScript、特性

### ①脚本语言

JavaScript是一种解释型的脚本语言。不同于C、C++、Java等语言先编译后执行, JavaScript不会产生编译出来的字节码文件，而是在程序的运行过程中对源文件逐行进行解释。

### ②基于对象

JavaScript是一种基于对象的脚本语言，它不仅可以创建对象，也能使用现有的对象。但是面向对象的三大特性：『封装』、『继承』、『多态』中，JavaScript能够实现封装，可以模拟继承，不支持多态，所以它不是一门面向对象的编程语言。

### ③弱类型

JavaScript中也有明确的数据类型，但是声明一个变量后它可以接收任何类型的数据，并且会在程序执行过程中根据上下文自动转换类型。

### ④事件驱动

JavaScript是一种采用事件驱动的脚本语言，它不需要经过Web服务器就可以对用户的输入做出响应。

### ⑤跨平台性

JavaScript脚本语言不依赖于操作系统，仅需要浏览器的支持。因此一个JavaScript脚本在编写后可以带到任意机器上使用，前提是机器上的浏览器支持JavaScript脚本语言。目前JavaScript已被大多数的浏览器所支持。

## 2、声明和使用变量

### ①JavaScript数据类型

- 基本数据类型

  - 数值型：JavaScript不区分整数、小数

  - 字符串：JavaScript不区分字符、字符串；单引号、双引号意思一样。

  - 布尔型：true、false

    在JavaScript中，其他类型和布尔类型的自动转换。

    true：非零的数值，非空字符串，非空对象

    false：零，空字符串，null，undefined

    例如："false"放在if判断中

    ```javascript
    // "false"是一个非空字符串，直接放在if判断中会被当作『真』处理
    if("false"){
    	alert("true");
    }else{
    	alert("false");
    }
    ```

    

- 引用类型

  - 所有new出来的对象
  - 用[]声明的数组
  - 用{}声明的对象

### ②变量

- 关键字：var

- 数据类型：JavaScript变量可以接收任意类型的数据

- 标识符：严格区分大小写

- 变量使用规则

  - 如果使用了一个没有声明的变量，那么会在运行时报错

    Uncaught ReferenceError: b is not defined

  - 如果声明一个变量没有初始化，那么这个变量的值就是undefined

## 3、函数

### ①内置函数

内置函数：系统已经声明好了可以直接使用的函数。

#### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_1-弹出警告框)[1]弹出警告框

```javascript
alert("警告框内容");
```

1

#### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_2-弹出确认框)[2]弹出确认框

用户点击『确定』返回true，点击『取消』返回false

```javascript
var result = confirm("老板，你真的不加个钟吗？");
if(result) {
	console.log("老板点了确定，表示要加钟");
}else{
	console.log("老板点了确定，表示不加钟");
}
```

#### [3]在控制台打印日志

```javascript
console.log("日志内容");
```

1

![./images](data:image/png;base64,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)

### ②声明函数

写法1：

```javascript
		function sum(a, b) {
			return a+b;
		}
```



写法2：

```javascript
		var total = function() {
			return a+b;
		};
```



写法2可以这样解读：

声明一个函数，相当于创建了一个『函数对象』，将这个对象的『引用』赋值给变量total。最后加的分号不是给函数声明加的，**而是给整体的赋值语句加的分号。**

### ③调用函数

JavaScript中函数本身就是一种对象，函数名就是这个**『对象』**的**『引用』**。而调用函数的格式是：**函数引用()**。

```javascript
		function sum(a, b) {
			return a+b;
		}
		
		var result = sum(2, 3);
		console.log("result="+result);
```

或：

```javascript
		var total = function() {
			return a+b;
		}
		
		var totalResult = total(3,6);
		console.log("totalResult="+totalResult);
```



## 4、对象

JavaScript中没有『类』的概念，对于系统内置的对象可以直接创建使用。

### ①使用new关键字创建对象

```javascript
//new创建对象
    var hqh = new Object();
    hqh.name = "贺启衡";
    hqh.age = "19";
    console.log(hqh);
    console.log(hqh.name);
    //{}创建对象
    var hjj2 = {
        "name": "黄嘉婕",
        "age": "37"
    }
    console.log(hjj2);
```

### ③给对象设置函数属性

```javascript
//对象函数属性
    hqh.study = function() {
        alert("with hjj study")
    }
    hqh.study(); //括号
```

或：

```javascript
// 创建对象
var obj02 = {
	"soldierName":"john",
	"soldierAge":35,
	"soldierWeapon":"gun",
	"soldierShoot":function(){
		console.log(this.soldierName + " is using " + this.soldierWeapon);
	}
};

// 在控制台输出对象
console.log(obj02);
// 调用函数
obj02.soldierShoot();
```

### ④this关键字

this关键字只有两种情况：

- **在函数外面：this关键字指向window对象（代表当前浏览器窗口）**
- **在函数里面：this关键字指向调用函数的对象**

```javascript
// 直接打印this
console.log(this);

// 函数中的this
// 1.声明函数
function getName() {
	console.log(this.name);
}

// 2.创建对象
var obj01 = {
	"name":"tom",
	"getName":getName
};
var obj02 = {
	"name":"jerry",
	"getName":getName
};

// 3.调用函数
obj01.getName();
obj02.getName();
```

## 5、数组

### ①使用new关键字创建数组

```javascript
// 1.创建数组对象
var arr01 = new Array();

// 2.压入数据
arr01.push("apple");
arr01.push("orange");
arr01.push("banana");
arr01.push("grape");

// 3.遍历数组
for (var i = 0; i < arr01.length; i++) {
	console.log(arr01[i]);
}

// 4.数组元素反序
arr01.reverse();
for (var i = 0; i < arr01.length; i++) {
	console.log(arr01[i]);
}

// 5.数组元素拼接成字符串
var arrStr = arr01.join(",");
console.log(arrStr);

// 6.字符串拆分成数组
var arr02 = arrStr.split(",");
for (var i = 0; i < arr02.length; i++) {
	console.log(arr02[i]);
}

// 7.弹出数组中最后一个元素
var ele = arr01.pop();
console.log(ele);
```

### ②使用[]创建数组

```javascript
// 8.使用[]创建数组
var arr03 = ["cat","dog","tiger"];
console.log(arr03);
```

## 6、JSON

### JSON格式的用途

在开发中凡是涉及到**『跨平台数据传输』**，JSON格式一定是首选。

### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_2json格式的说明)②JSON格式的说明

- JSON数据两端要么是**{}**，要么是**[]**
- **{}**定义JSON对象
- **[]**定义JSON数组
- JSON对象的格式是：

```json
{key:value,key:value,...,key:value}
```



- JOSN数组的格式是：

```json
[value,value,...,value]
```



- key的类型固定是字符串
- value的类型可以是：
  - 基本数据类型
  - 引用类型：JSON对象或JSON数组

正因为JSON格式中value部分还可以继续使用JSON对象或JSON数组，所以JSON格式是可以**『多层嵌套』**的，所以JSON格式不论多么复杂的数据类型都可以表达。

```json
{
	"stuId":556,
	"stuName":"carl",
	"school":{
		"schoolId":339,
		"schoolName":"atguigu"
	},
	"subjectList":[
		{
			"subjectName":"java",
			"subjectScore":50
		},
		{
			"subjectName":"PHP",
			"subjectScore":35
		},
		{
			"subjectName":"python",
			"subjectScore":24
		}
	],
	"teacherMap":{
		"aaa":{
			"teacherName":"zhangsan",
			"teacherAge":20
		},
		"bbb":{
			"teacherName":"zhangsanfeng",
			"teacherAge":108
		},
		"ccc":{
			"teacherName":"zhangwuji",
			"teacherAge":25
		}
	}
}
```

### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_3json对象和json字符串互转)③JSON对象和JSON字符串互转

#### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_1-json对象转json字符串)[1]JSON对象转JSON字符串

```javascript
var jsonObj = {"stuName":"tom","stuAge":20};
var jsonStr = JSON.stringify(jsonObj);

console.log(typeof jsonObj); // object
console.log(typeof jsonStr); // string
```



#### [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro001-javaweb/lecture/chapter03/verse03.html#_2-json字符串转json对象)[2]JSON字符串转JSON对象

```javascript
jsonObj = JSON.parse(jsonStr);
console.log(jsonObj); // {stuName: "tom", stuAge: 20}
```