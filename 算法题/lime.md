1.重构代码

```js
var message
function someNewPower(name, age, sex, weight, height, info) {
    let classInfo = info.classInfo
    switch (name) {
        case '张三':
            message = 'hello' + name + '你的体重为' + (height * 100 - 100) * 2 + 'kg' || 'hello 你的体重为' + (1.75 * 100 - 100) * 2 + 'kg'
            break
        case '李四':
            message = 'hello' + name + '你的体重为' + (height * 100 - 100) * 2 + 'kg' || 'hello 你的体重为' + (1.75 * 100 - 100) * 2 + 'kg'
            break
        case '王五':
            message = 'hello' + name + '你的体重为' + (height * 100 - 100) * 2 + 'kg' || 'hello 你的体重为' + (1.75 * 100 - 100) * 2 + 'kg'
            break
    }
    return message
}
type {}
function introduceSelf(name, age, sex, weight, height, info):string{
    return  'hello' + name + '你的体重为' + (height * 100 - 100) * 2 + 'kg' || 'hello 你的体			重为' + (1.75 * 100 - 100) * 2 + 'kg'
}
```

- 说一说在提高前端性能上你有什么经验？

  1. 减少请求数量，主要包括js和css的打包，合理利用强缓存和协商缓存
  2. 合理使用 *defer*属性，将dom操作放在DOMContentLoaded回调会好一点
  3. 尽量减少reflow和repaint
  4. dns-prefetch标签对指定域名dns预解析
  5. 静态资源独立域名，cookie隔离，且突破浏览器下载数限制

- 请指出5种以上编码过程中人们最常犯的错误?

  1. 函数名，变量名命名不规范
  2. 不写注释，
  3. 一个方法干的事太多，缺乏合理模块化
  4. 

- 小张想要看看最近的大米价格，他打开了百度，进行了一番操作，最后获得最近的大米价格。请从技术的角度简述整个过程中，数据会流转过哪些地方？涉及到的软件、中间件、技术、流程，参与者都有哪些？尽可能的讲全，流程尽可能细化。500字以内。

- 如果你是 https://6eb.tsa.yiye.ai/IPF82Rih 页面的开发人员，想要缩短首屏时间，请给出尽可能准确的优化方案？（针对性的给方案）

  ​	网页一共耗时6.7秒，其中dns解析0.4s，下载脚本1.5s，执行脚本4.6s。

  1. 异步加载css和js

  2. 通过观察看到js脚本执行需要4.6s，尝试优化js代码，合理利用webwork，将耗时计算挪到计算线程

  3. dns-prefetch标签对域名dns预解析

     

- 请举个例子，说明自己的学习能力很强？再举个例子，说明自己的抗压能力很强？

  ​	17年入职第二份工作，完成基于weex的通讯录改造，当时weex刚开源不久，没有成熟的生态，很多问题甚至只能在github在提交issius才能得到解决，为了解决组件更新细粒度问题，使用各种办法求助，最后通过本地缓存解决。

  ​	 18年1024程序猿节，为了推广人脸识别技术，上线紧急需求，自己独立完成项目，每天一点回家，九点准准时到办公室。

- 未来五年，你想成为一个什么样的人？你打算为此付出什么？

  想做技术大牛，之前做地图开发，感觉地图开发偏应用，于是改行专业前端，所以一直有个技术梦，想追求技术的极限，当然，说技术极限可能话太大了，想追求自己的技术极限。

- 你对广告行业有什么了解吗？

- 

