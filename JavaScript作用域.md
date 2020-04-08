# 			JavaScript作用域

##### 概念

​	JavaScript作用域是指函数运行时，变量的有效区间，落到函数运行范畴上，是指JavaScript的执行上下文。

可以分为全局，函数以及eval上下文

- 全局上下文

  全局上下文只有一个，是指整个JavaScript运行时。当执行JavaScript文件的时候，会将全局上下午压到当前的执行栈，this默认指想window对象

- 函数上下文

  ​		函数作用域是在函数执行的时候创建的函数执行上下文，this指向默认指向执行该函数的对象，可通过bind，apply等改变指向。当JavaScript执行引擎执行到函数的时候，会把函数上下文继续压到当前的执行栈

- eval上下文

  ​		eval函数也会产生新的作用域即函数执行上下文。

##### 执行栈管理过程即函数执行过程

```js
//1，首先JavaScript引擎创建全局上下文，并且将其压入到当前执行栈

//2，遇到函数，函数执行会生成自己的函数执行上下文，将函数上下文压入到当前执行栈
first()

function first() {
    
    console.log('i am first')
    // 3,又遇到了函数，继续生成属于自己的执行上下文，继续压入当前执行栈
    sencod()
    // 4，sencod函数执行完毕，推出执行栈
    
}
//5，first函数执行完毕，推出执行栈

function sencod() {
    console.log('i am sencod')
}
console.log('i am outside')

// 输出
// console.log('i am first'）=> console.log('i am sencod'）=> console.log('i am outside'）
```

```js
first()

function first() {
    console.log('i am first')
    sencod()
    
}
function sencod() {
    console.log('i am sencod')
    return function() {
 		console.log('i am third')       
    }
}
```



##### JavaScript创建执行栈过程

