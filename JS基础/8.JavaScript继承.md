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
var Person = function(name ="defaultName", gifts = ['eat','reading'] ) {
    this.name = name;
    this.gifts = gifts;
    this.introduce = function() {
        console.log('my name is ',name)
        console.log('my gifts is ',gifts)
        //return name
    }
}
// 添加原型链方法
Person.prototype.eat = function() {
    console.log('i am eatting')
}
```

###### 一、继承，使用原型链继承

​		将父类的实例作为子类的原型

```js
// 初始化子元素
function Student(grade) {
    this.grade = grade
}
//讲Student的原型链指向需要继承父类的实例上，就可以实现集成
Student.prototype = new Person()
//实例化子元素

var student = new Student('grade1')

student.introduce()
student.eat()
```

缺点：

1. 共享父类的属性，如果一个子类修改，其他也会修改，这不符合预期
2. 无法向父类方法传参，即没有办法给name赋值。

###### 二、使用构造方式的函数

​		使用构造函数的方法实现继承，主要是在子类内部执行父类的构造方法，并且将在子类中利用call方法改变this指向，实现继承。

```js
function Student(name,gifts) {
    Person.call(this, name,gifts)
}

let st1 = new Student('tom', ['catching mouse'])
let st2 = new Student('jerry', ['dring milk'])

st1.introduce()
//st1.eat()
st2.introduce()
//st2.eat()

```

缺点：可以看到，这种方法无法实现原型链上的方法的继承。eat方法执行时会报错



###### 三，使用组合方式实现js的继承

```js
function Student(name) {
    Person.call(this,...arguments)
}
Student.prototype = Person.prototype
```

组合使用原型链继承和构造函数继承方法，

将Studen之类的prototype指向Person的prototype，

在子类内部通过call将改变this的执行

缺点：通过Student构造函数new出来的实例，student.__proto.constructor.name == Person，显然这不符合预期

###### 四，寄生组合继承

既然通过组合方式实现js继承无法维护之类的构造函数，那么，在组合完之后，将`_proto_.constructo`r修改一下不就得了，于是有了终极方案：

```js
function Student(name) {
    Person.call(this,...arguments)
}
Student.prototype = Object.create(Person.prototype)
// 然后_proto.constructor指向Student就可以了。
Son.prototype.constructor = Son;
```

###### 五，ES6的extend方法



前人写的集成方面的好文

https://juejin.im/post/5e8aa20651882573a343d089?utm_source=gold_browser_extension