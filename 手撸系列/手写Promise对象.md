# 							Promise





[手写async await的最简实现（20行搞定）面试必考！](https://juejin.im/post/5e79e841f265da5726612b6e)

[详解promise](https://juejin.im/post/5e888002e51d4546bd34f6cc?utm_source=gold_browser_extension)

[手写一个Promise/A+,完美通过官方872个测试用例](https://juejin.im/post/5e8bec156fb9a03c4d40f4bc)

```js
const getData = () => new Promise(resolve => setTimeout(() => resolve("data"), 1000))

async function test() {
  const data = await getData()
  console.log('data: ', data);
  const data2 = await getData()
  console.log('data2: ', data2);
  return 'success'
}

// 这样的一个函数 应该再1秒后打印data 再过一秒打印data2 最后打印success
test().then(res => console.log(res))

```

