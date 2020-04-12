# JavaScript中事件执行顺序

JavaScript作为单线程语言的代表，在处理复杂事件时，采用的是回调的方

```js
setInterval

function myInterval(fn,time) {
	setTimeout(fn,time)
	setTimeout(myInterval(),time)
}
```

