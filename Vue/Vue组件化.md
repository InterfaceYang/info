# 							Vue组件化

> ​		组件化是所有前端框架的基石，组件化的目的归根结底是为了代码的复用，所以在组件化过程中，要充分考虑跟外部的解耦。

##### 组件之间的数据传递

###### 父子组件之间

父子之间数据传递，父往子主要通过props，子往父，主要采用数据派发的形式。

```vue

<template>
    <Son name="som" ></Son>
</temlate>

<template>
	<div>
    {{name}}  // son
  </div>
</template>



```

###### 兄弟组件之间传递

​		兄弟组件之间传递，主要通过父组件起中介作用，进行数据的派发和时间的监听.主要是使用  parent和   root

```vue
Father
<template>
  <div>
      <Son1></Son1>
      <Son2></Son2>
</div>

</temlate>


Son1
<template>
</template>



```

###### 祖后辈组件之间传递

```vue
provide
inject
```

###### 无关系组件之间传递

```javascript
Vue.prototype.$bus= new Vue()
```

