#### 路由跳转

```
- uni.navigateTo({ url: '/pages/home/Home' })   // 保留当前页面，跳转到应用内的某个页面
-
- uni.redirectTo({ url: '/pages/home/Home' })   // 关闭当前页面，跳转到应用内的某个页面
-
- uni.reLaunch({ url: '/pages/home/Home' })     // 关闭所有页面，打开到应用内的某个页面
-
- uni.switchTab({ url: '/pages/home/Home' })    // 跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面
-
- uni.navigateBack({ url: '/pages/home/Home' }) // 关闭当前页面，返回上一页面或多级页面
```
