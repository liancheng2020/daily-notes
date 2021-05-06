#### vue项目添加两个iconfont库

##### 前言：有的项目常常需要用到引入两个或多个iconfont库，

- 将下载下来的文件夹命名为baseicon；
- 找到iconfont.css文件，修改以下：
将原来的iconfont![iconfont](/blogs/images/iconfont.png)
改为baseicon![baseicon](/blogs/images/baseicon.png)
- 找到iconfont.json文件，将
```
  "font_family": "iconfont",
```
改为
```
  "font_family": "baseicon",
```
- 记得在 main.ts 中引入修改后的 baseicon 文件夹路径；
```
  import './assets/baseicon/iconfont.css'
```