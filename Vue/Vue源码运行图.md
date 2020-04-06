# 						Vue源码浅尝辄止

​		最近一段时间，看了下vue源码，这里记录一下，供自己查缺补漏

​		组件加载之初，实例化watcher对象，初始化过程中，通过正则匹配，匹配中需要差值运算的表达式和文本，跟data中的数据对比，从而完成差值替换，而此时`data已完成了observer`，因此，取值触发get，完成数据的依赖收集。





前人写的vue源码接下，看作者个人主页，一系列文章；

https://juejin.im/post/5e6efe226fb9a07cc50f25fb



这个文章是讲vue源码中一些工具函数如何使用的；

https://juejin.im/post/5e897f746fb9a03c550fd4ea?utm_source=gold_browser_extension