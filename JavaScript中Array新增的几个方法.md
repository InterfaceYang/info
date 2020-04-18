##### 1.keys  values entries 三个遍历函数

##### 2.some every 

##### 3.flat

神奇，es6竟然有数组扁平化的处理函数

```js
const arr = [1, [2, [3]]]
ar.flat(Infinity) //参数的意思是要拉平多少层
```

##### 4.map和reduce

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

```js
let arr1 = [1,2,3,4]
let arr2 = [5,6,7,8]
arr1.concat(arr2)  //[1,2...] 返回连接后的新数组，不改变原数组

arr1.pop()         // 4 返回数组最后一项，原数组要素尾部-1
arr1.shift()       // 1 返回数组第一项，原数组要素头部-1

//经pop shift，原数组掐头去尾arr1 = [2,3]
arr1.push(9)        // 3 返回数组长度，原数组尾部+1
arr1.unshift(0)     // 4 返回数组长度，原数组头部+1

// 经过操作，原数组arr1 = [0,2,3,9]
arr1.slice(1,3)      // 返回截取的大小[2,3]，一般来说，在数组内部，返回个数是end-start，即所谓的不掐头，去尾巴，原数组不变，常用slice进行数组的复制,arr1.slice()返回undefined



arr1.splice(0,3)      // start，count, 返回从start开始count个，改变原数组， arr = [9]
总结来说。
会修改原本数组的方法，称作，修改器方法
pop push revert splice shift unshift
不能修改原数组的方法，称作，访问器方法
concat include join slice toString indexOf等
数组还有一些写迭代器方法，forEach，entries，every，some，filter，find，findIndex，key，map， reduce
```

##### 

[数组方法总览和耗时统计](https://juejin.im/post/5bb753bd6fb9a05d2272b673)

