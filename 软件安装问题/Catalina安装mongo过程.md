1. 苹果更新最新Catalina之后，安装mongo失败，执行下边命令，将mongo的默认目录挪到家目录

   ```js
   sudo mkdir -p ~/data/db  // 创建家目录下data文件夹
   mongod --dbpath ~/data/db // 挪过去
   ```

   ​		<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gdrrigui4ej31180hqta6.jpg" style="zoom: 50%;" />
   

2.

