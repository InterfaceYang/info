# 	JavaScript中call和apply的应用

##### 介绍作用

##### 一些常规操作

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

