##### 获取系统全局安装的依赖

`npm ls -g --depth=0`

##### 卸载wepy

`npm uninstall -g @wepy/cli`

注意如果-g后边的依赖输入错误，只会提示

`up to date in 0.045s`

##### 升级node之后，项目会提示一些报错，报错信息就不贴了，

这个时候的解决方案是 `node rebuild node-sass`