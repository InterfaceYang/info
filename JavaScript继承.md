# js继承的三种常见方法

##### 前言

​		在了解js的继承之前，需要搞清楚几个概念，亦或者属性，方便之后的讲解、

`prototype`：每个函数被new出来都有`prototype`属性，既函数的类有`protytype`属性
`proto`：所有对象都包含一个`__proto__`属性指向它的构造函数的`prototype`。
`constructor`：所有对象都包含`constructor`属性,这个属性包含一个指向`prototype`属性所在函数的指针。



```js
var Fn = function() {}
var fn = new Fn()

Fn.prototype === fn.__proto__    //true
```

##### 正式内容

​		js在es6之前甚至没有类的概念，在实现继承的时候依据原型链原则。

```javascript
// 这是个祖元素
var Person = function(name) {
    this.name = name ;
    this.introduce = function(name) {
        console.log('my name is ', name)
        return name
    }
}
// 添加原型链方法
Person.prototype.eat = function(food) {
    console.log('i am eatting' , food)
}
```

###### 一、继承，使用原型链继承

```js
// 初始化子元素
function Student(name) {
    this.name = name
}
//讲Student的原型链指向需要继承父类的实例上，就可以实现集成
Student.prototype = new Person()
//实例化子元素
var student = new Student('Tom')

student.introduce('jerry')
student.eat('nodejs')
```

缺点：

###### 二、使用构造方式的函数



###### 三，使用组合方式实现js的继承

```js
function Student(name) {
    Person.call(this,name)
}
var student = new Student('Tom')
student.introduce()
student.eat()
```
