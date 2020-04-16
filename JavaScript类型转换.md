# 				JavaScript类型转换

​		由于JavaScript的弱类型特点，导致他的数据类型是由他的值决定的，所以在使用过程中，JavaScript会存在一些让人迷惑的类型转换过程。

​		说到类型转换，两个常用的函数是toString()和valueOf()。见文知意，对于前者toString()，主要是获得表示该对象的字符串，对于后者valueOf()，主要是获得该对象的原始数据，数据类型转换是指在有+运算的时候，

```javascript
var bar=true;

console.log(bar+0);
//准从表达式中有数字的情况，对将bar转换成数字，1，所以结果是1

console.log(bar+"xyz");
//准从表达式中有字符串的情况，对将bar转换成字符串，结果是truexyz

console.log(bar+true);
//表达式中有布尔类型的情况，两者都转换成数字，结果是2

console.log(bar+false);
//表达式中有布尔类型的情况，两者都转换成数字，结果是1

console.log('1'>bar);
// 不知道为啥，但是是false

console.log(1+'2'+false);
// 根本从左到右的计算规则，首先将false转字符传，然后再进行字符串的拼接 12false

console.log('2' + ['koala',1]);
// 将数组转换成toString()  2koala,1

var obj1 = {
   a:1,
   b:2
}
console.log('2'+obj1)；
// 对obj1执行toString()方法，所以是2ObjectObjecy

var obj2 = {
    toString:function(){
        return 'a'
    }
}
console.log('2'+obj2)
// 对obj1执行toString()方法，所以是2a
```





[从206个console.log()完全弄懂数据类型转换的前世今生(]: https://juejin.im/post/5e7f8314e51d4546fa4511c9

> 作者：ikoala
> 链接：https://juejin.im/post/5d030e03518825361817032f
> 来源：掘金
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。