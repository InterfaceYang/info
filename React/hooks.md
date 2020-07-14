React增加了钩子，可以更方便的进行一些数据管理

```js
// 无清除函数，第二个参数不为空[]
  // 每次count变化都变化
  /*
  useEffect(()=>{
    console.log('useEffected')
  }, [count])
  */

  // 无清除函数，第二个参数为空[]
  // 只在初始化时候执行一次
  /*
  useEffect(()=>{
    console.log('useEffected no []')
  }, [])
  */

  // 无清除函数，第二个参数不为空[]
  // 每次count变化都变化
  /*
 useEffect(()=>{
  console.log('useEffected  [count]')
  return ()=>{
    console.log('return effected [count]')
  }
 }, [count])
  */

// 页面初始化时执行一次，
// 卸载时候估计也会执行一次
/*
useEffect(()=>{
  console.log('useEffected  []')
  return ()=>{
    console.log('return effected []')
  }
}, [])
*/
```

