##### keys  values entries 三个遍历函数

##### some every 

##### map和reduce

###### 用reduc写一个递归实现数组的扁平化处理

```js
function flatten(arr) {  
    return arr.reduce((result, item)=> {
        return result.concat(Array.isArray(item) ? flatten(item) : item);
    }, []);
}
// 这里直接拓展一下得了，使用其他方法实现数组的扁平化

1
function flatten(arr){
    return arr.toString().split(',')
}
2
function flatten(arr){
    return arr.join(',').split(',')
}
3
function flatten(arr) {
    var res = [];
    arr.map(item => {
        if(Array.isArray(item)) {
            res = res.concat(flatten(item));
        } else {
            res.push(item);
        }
    });
    return res;
}
```

##### 总结一下数组的各个方法都返回什么内容

##### 