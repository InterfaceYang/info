# 								bind



> Nature and nature's laws, hidden in the dark. God said, let Newton go! So, all becomes bright.	
>
> ​																									bind可以说是js中最newton的存在。

[Function.prototype.bind()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

​		老规矩，文章开始之前 ，先放上mozilla的官方注解，毕竟最好的说明书就是说明书本身。

`		bind()` 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的 `this` 被指定为 `bind()` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。这一点和apply和call有点像。

###### apply/call

​	 最经典的例子是可以使用Math的max方法，实现数组最大值的求解.

​	两者接受的第一个参数都是函数目标指向的对象。两者不同的是apply接受的第二个参数，是数组类型，而call是字符串类型

```js
Math.max.appply(null,[1,2,3])
Math.max.call(null,1,2,3)		
```

​		手写一个bind方法，实现可以主动修改this的指向问题，可以利用跟bind有差不多效果的apply/call方法。

​	

```js
function myBind(fun,...args) {
  	let that = this ;
  	let _fun ;
  
  	_fun = that.apply(fun,args)
  	
  	return _fun
}
```

