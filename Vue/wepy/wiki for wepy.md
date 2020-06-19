### 主要写一些wepy学习过程中需要注意的地方

1. ##### wepy事件执行顺序

   混入onload→父组件onLoad→子组件onLoad→混入onShow→父组件onShow

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200619143921700.png" alt="image-20200619143921700" style="zoom:30%;" />

2. ##### wepy组件一旦引入则会执行onLoad方法，不管有没有使用。

3. ##### wepy中，被重写的mixin中函数首先执行，然后执行mixin原生方法

   <img src="/Users/yang/Library/Application Support/typora-user-images/image-20200619144123226.png" alt="image-20200619144123226" style="zoom:33%;" />

4. ##### wepy中一些数据更改后，为了确保脏数据对比，需要显式的调用$apply()方法进行应用

5. ##### 混入模式mixin的时候，可以通过this.$mixin[].methods.method()循环调用，但是只是会继续调两次机会停止

6. ##### wepy采用中间件模式，可以引用中间件实现一些全局功能或者polyfil，最常用的是

   ```js
   this.use('promisify');  //使用wepy.xxx的方式请求小程序原生API都将Promise化。
   this.use('requestfix'); // 修复小程序请求并发问题。
   ```

7. `intercept(api:String, provider:Object)`：使用拦截器对原生API请求进行拦截（待研究）



