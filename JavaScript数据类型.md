# JavaScript数据类型

​	JS是弱类型的语言，变量的类型是动态的。变量的类型由其值得类型决定。按照大类，可以分为值类型和引用类型。

###### 	值类型：

​	NULL类型，undefined类型，Number类型，String类型，Boolean类型，Symbol类型

```javascript
let num1 = 123;             
let num2 = new Number(123)

let string1 = "hello"
let string2 =  new String("world")

let b1 = true;
let b2 = new Boolean(false)
```

  当我们使用方法1进行数据初始化的时候，后台会自动生成方法2的构造函数，这就解释了，为什么
  string.toString()不会报错

###### 	引用类型：

​	Function类型，Object类型，Array类型等
​	针对Number类型，String类型，Boolean类型还衍生出三个包装类型，即


​	js有检查数据类型的函数，typeof和instanceof，还可以通过constructar来判断，亦或者是可以通过Object.prototype.toString.call()判断

##### 一、typeof

###### 1，针对简单数据类型：

typeof用来判断非Null的简单类型是没有问题的，而在处理null的时候会造成困扰，typeOf null 返回object
这里的原因主要是因为typeof主要通过判断存储变量的机器码来判断数据类型，在js底层，会有机器码的前三位
存储数据的类型信息：
000：对象
010：浮点数
100：字符串
110：布尔
1：整数

因为null的存储码是000，所以typeOf null会返回object
而，其他的简单类型，用typeof判断是没有问题的

```javascript
number, string, , boolean, undefined, symbol
typeof  1    // number
typeof '1'   // string
typeof true   // boolean
typeof undefined   // undefined
typeof new Symbol()   // symbol
```



###### 2，针对引用数据类型：

typeof判断一些数据类型会造成困扰，举例子说明。

```javascript
typeof new Function   // function
typeof {}   // object
typeof []   // object
```

并且typeof在处理自定义类型的时候不能正确显示，只会返回object

##### 二、instanceof 

instanceof的原理主要是看是不是在原型链上，instanceof主要是为了判断是否属于某一类型，这本来无可厚非，但是他还可以判断是否是某类型的子类，这就造成，如果存在继承关系，
在使用instanceof进行判断的时候，就会产生困扰，可能会造成非预期的效果。

###### 1，针对简单数据类型：

因为instanceof的判断原理，所以在处理诸如Number，String，和Boolean的时候会有一些需要注意的点。

```javascript
let num1 = 123;              
let num2 = new Number(123)
num1 instanceof Number  //false
num2 instanceof Number  //true

let string1 = "hello"
let string2 =  new String("world")
string1 instanceof String  //false
string2 instanceof String  //true

let b1 = true;
let b2 = new Boolean(false)
b1 instanceof Boolean  //false
b2 instanceof Boolean  //true

let sy = Symbol()
sy instanceof Symbol  // false
```

因为众所周知的原因，js一切对象都来源于null，是不是 sy instanceof null 也会返回true呢？
这里不会，这里会提示 Right-hand side of 'instanceof' is not an object

###### 2，针对引用数据类型：

```js
let fn = new Function()
let arr = new Array([1,2,3])
let obj = new Object({b:1})

fn instanceof Function // true
arr instanceof Array   // true
obj instanceof Object  // true


let Person = function(){}
let Student = function(){}
Student.prototype = new Person()
let st = new Student()

st instanceof Person  // true
st instanceof Student // true
```



##### 三、constructor方法判断

constructor代表构造函数，在通过new命令进行对象初始化的时候执行，任何具有原型对象的对象都会自动继承这个方法、
对象的constructor属性会返回这个对象的构造函数，因此可以通过这个判断对象的类型

###### 1，针对简单数据类型：

```js
let num1 = 123;             
let num2 = new Number(123)
num1.constructor === Number  // true
num2.constructor === Number  // true

let string1 = "hello" 
let string2 =  new String("world")
string1.constructor === String  // true
string2.constructor === String  // true


let b1 = true;
let b2 = new Boolean(false)
b1.constructor === Boolean  // true
b2.constructor === Boolean  // true

let sy = Symbol()
b1.constructor === Symbol  // true
```


null，undefined没有constructor属性

###### 2，针对引用数据类型：



##### 四、Object.prototype.toString.call

这个方法是目前来说，最全面最准确的方法，他的原理是首先调用object对象原型链上的toString方法，然后通过call改变函数执行主体的指向，让待检测对象执行这个方法，进而可以打印出待检测对象的属性

```javascript
let toString = Object.prototype.toString
toString.call(**).slice(8,-1)
```