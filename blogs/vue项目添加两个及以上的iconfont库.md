### vue项目添加两个及以上的iconfont库

##### 前言：有的项目常常需要用到多个icon图标，但是可能有些icon图标不在同一个iconfont库里面，那么就需要引入两个或多个iconfont库，这里引入的第二个iconfont库修改为baseicon库为例。

1. 将下载下来的iconfont文件夹命名为baseicon；

2. 找到文件夹中的iconfont.css文件，修改以下相关信息：
将原来的iconfont
![iconfont](/blogs/images/iconfont.png)
修改为baseicon
![baseicon](/blogs/images/baseicon.png)

3. 打开文件夹里的iconfont.json文件，修改 `font-family` 信息：
```
  "font_family": "iconfont"  改为  "font_family": "baseicon"
```

4. 记得在 main.ts 中引入修改后的baseicon文件夹路径；
```
  import './assets/baseicon/iconfont.css'
```

5. 相关的 baseicon 用法如下（以图标 ic-ui-time 为例）：
```
  <i class="baseicon ic-ui-time"></i>
```