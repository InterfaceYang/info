# 					一些简单的ES6特性

##### let

​		let跟var最大的不同是在定义变量的时候，给变量指定的作用域不同，let指定块状作用域，var指定函数作用域

```js
	
```

##### const

​	const是es6中定义常量的修饰符，用于表示新建的变量不可更改，这里的**不可更改**实际上指的是**内存地址不变**，而不是指变量的值不变。因此在定义Object以及Array为常量的时候，需要特别注意。

```  js
const name = "Tom"
name = "j1eey"  //报错

const person = {name:'Tom'}
person.name = "jerry"  // {name:'Jerry'}
person = {}      // 报错

const items = ['apple']
items.push('orange')  // ['apple','orange']
items = ['orange']    // 报错
```