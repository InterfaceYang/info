# 	JavaScript中call和apply的应用

##### 介绍作用

由于JavaScript中，this指向是在运行时确定的，指向执行者，这就导致有时候一些情况会产生不可控的情况，因此call和apppy应运而生，主要用来指定函数运行的时候的this指向。



```js
function sayHello() {
    name:''
    console.log('name is ', this.name)
}
const obj = {
    name: 'tom'
}
// 
obj.say = sayHello   
obj.say()

```



##### 一些常规操作

call和apply在实际使用中，主要用来改变this的指针方向。

##### 一些可以利用的特性



###### 求数组的最大值，最小值

```
Math.Max.apply(null, [1,2,,3])

Math.Max.call(null, 1,2,,3)
```

同样道理，也可以根据math的min方法，求数组的最小值

```js
这里延伸一下，求数组最大值，最小值的方法
// 求最大值
function getMax(arr) {
    let max = -Infinity;
    let len = arr.length
    while(len--) {
        if(arr[len] > max ) {
            max = arr[len]
        }
    }
    return max
}

```

