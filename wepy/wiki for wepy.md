#### 							wepy学习过程中需要注意的地方

> 自说自话，如果对你有所帮忙，不胜荣幸.

1. ##### wepy事件执行顺序

   混入onload→父组件onLoad→子组件onLoad→混入onShow→父组件onShow

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200619143921700.png" alt="image-20200619143921700" style="zoom:30%;" />

2. ##### wepy组件一旦引入则会执行onLoad方法，不管有没有使用。

3. ##### wepy中，被重写的mixin中函数首先执行，然后执行mixin原生方法

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200619144123226.png" alt="image-20200619144123226" style="zoom:33%;" />

4. 手动调用`$apply`方法

   ​		wepy中一些数据更改后，正常流程下，改变数据后，组件会在流程结束时自动触发脏检查。 在异步或者回调流程中改变数据时，需要手动调用`$apply`方法。需要显式的调用$apply()方法进行应用

5. ##### 混入模式mixin的时候，可以通过this.$mixin[].methods.sayHello()循环调用，但是只是会继续调两次机会停止

6. ##### wepy采用中间件模式，可以引用中间件实现一些全局功能或者polyfil，最常用的是

   ```js
   this.use('promisify');  //使用wepy.xxx的方式请求小程序原生API都将Promise化。
   this.use('requestfix'); // 修复小程序请求并发问题。
   ```

7. `intercept(api:String, provider:Object)`：使用拦截器对原生API请求进行拦截（待研究）

8.  wx.uploadFile的success回调跟的onProgressUpdate钩子返回的进度不一致，导致进度百分百后，其实接口并没有返回200。[UploadTask.onProgressUpdate 安卓进度问题，为什么到现在还没解决？](https://developers.weixin.qq.com/community/develop/doc/0000482097c0b0ab502ad58e151000)

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200629211058478.png" alt="image-20200629211058478" style="zoom:50%;" />

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200629211152661.png" alt="image-20200629211152661" style="zoom:40%;" />

9. wepy组件传值跟vue完全不同，可以说完全不能跟vue相比，特别是object的传参，经常有问题，这里有问题一定要注意。

   





