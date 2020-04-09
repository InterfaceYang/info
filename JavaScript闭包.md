# JavaScript闭包

> ​		闭包，简单来说就是通过函数内返回函数，由于外部函数的命名空间被内部函数所引用，来达到就算函数执行完毕，也不会清除内存空间的目的。
>
> [文章所有内容来自于这篇短文，本文只做本人的碎碎念](https://zhuanlan.zhihu.com/p/56490498)

##### 知识储备

1. 了解函数执行时，js引擎做了什么

   执行到函数，将创建函数作用域，其内部的变量作为作用域内的本地变量，直到函数结束才释放

2. 函数什么时候开始，什么时候结束

   函数一般是以函数名后边有左括号（为开始执行标识，结束是遇到return函数或者}

   ```js
   //js引擎执行到这，会用一个叫sayHello的变量盛放这个函数
   function sayHello() {
     console.log('helo world')
   }
   // 执行到这，会在全局中寻找sayHello的变量，找到原来是个函数，
   // 并且看到（，执行他
   sayHello()
   ```

   

##### 基础例子

```js
//1.全局上下文声明变量 a，赋值为3
1: let a = 3

//2.全局上下文声明变量 addTwo ，赋值为一个函数
2: function addTwo(x) {
3:   let ret = x + 2
4:   return ret
5: }

// 3.首先，全局上下文声明变量b，变量一经声明，其值就是undefined
// 4.第六行，我们看到=赋值运算符，准备把后边的东西赋值给b，突然意识到后边的东西是个函数，并且看到函数开始的标志双括号，于是乎，不论addTwo函数返回啥，最后都要赋值给b
// 5.函数名叫addTwo，我们在全局上下文找找，突然发现，在第二行的时候赋值了一个，于是就要执行这个函数
// 6.看到这个函数参数里有个a，于是在全局上下文找这个a，在第一行就看到了a=3，于是把这个3带入到函数里，开始执行他,就像之前说的，执行函数需要生成函数执行的上下文，并且推入到执行栈里。于是这里addTwo执行上下文被推到了执行栈
// 7.仔细研究2-5行，就会看到第二行，函数参数里有个x，这个时候已经把3传递过来了，所以把3赋值给x
// 8.在addTwo执行栈里，声明一个ret，声明之后默认是undefined，
// 9.第三行赋值运算符的右边有个x，在addTwo执行栈中找x是何物，找到解析7中。将3赋值给x，于是x+2 = 3+2。执行相加操作，把5赋值给ret
// 10.return ret，这里在addTwo作用域内找本地变量ret，找到第3行已经被赋值为5的ret，返回函数
// 11.函数结束。addTwo执行上下文被推出执行栈，内部变量失效，返回值5返回给调用上下文，并且赋值给b
6: let b = addTwo(a)

// 执行console.log函数，全局作用域内寻找b，然后打印出b
7: console.log(b)   // =>5
```

##### 进阶例子

```js
 // //1.全局上下文声明变量 val，赋值为7
 1: let val = 7
 
 //2.全局上下文声明变量 addTwo ，赋值为一个函数
 2: function createAdder() {
 3:   function addNumbers(a, b) {
 4:     let ret = a + b
 5:     return ret
 6:   }
 7:   return addNumbers
 8: }

 
  // 3,首先全局上下文声明变量adder，为undefined
  // 4，准备给adder赋值，发现右边是个函数，于是在全局上下文中寻找createAdder，发现果真有，并且之后还有双         括号，这可是函数的执行标识，所以会将函数的返回值赋值给adder
  // 5，找到createAdder，并且执行他，产生createAdder函数上下文
  // 6，在createAdder函数上下文中，第三行，看到函数生命addNumbers，因此把函数赋值给addNumbers
  // 7，第七行，发现return方法，这是函数执行结束的标识，createAdder函数上下文被清理，
  //    但是addNumbers因为已经被赋值给adder，没被清理
 9: let adder = createAdder()
 
 // 同样的，先声明sum为undefined，之后赋值，发现是函数，这执行他。
 // adder 已经被赋值为addNumbers，然后是7+8
10: let sum = adder(val, 8)

11: console.log('example of function returning a function: ', sum)
```

