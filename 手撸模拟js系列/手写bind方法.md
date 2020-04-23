# 								bind

##### bind官方定义		

​		老规矩，文章开始之前 ，先放上mozilla的官方注解，毕竟最好的说明书就是说明书本身。

​		[Function.prototype.bind()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

`		bind()` 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的 `this` 被指定为 `bind()` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。这一点和apply和call有点像。

##### 书写方法模拟bind

​		手写一个bind方法，实现可以主动修改this的指向问题，可以利用跟bind有差不多效果的apply/call方法。

```js
    // myBind简单实现，这里有三个问题，
	// 如果bind绑定后的函数被new了，那么此时this指向就发生改变。此时的this就是当前函数的实例
	// 有保留原函数在原型链上的属性和方法
	// bind之后的方法可以继续添加参数，这里没有考虑
	function myBind(fun,...args) {
        let _fun =  this.apply(fun,args)
        return _fun
    }
```

​	

```js
function myBind(fun,...args) {
    let that = this;
    let _fn  = function () {
	// bind之后的方法可以继续添加参数，这里没有考虑
    that.apply(this instanceof that ? this : args, args.concat(Array.prototype.slice.call(arguments)))
    }
	// 有保留原函数在原型链上的属性和方法
    _fn.prototype = Object.create(that)
    
    return _fn
}
```

