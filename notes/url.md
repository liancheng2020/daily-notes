#### 页面跳转

```
    window.location.href = "url"
```

#### 返回上一页

```
    window.history.length  // 当前页的历史列表长度
    window.history.back()  // 返回上一页
    window.history.go(-1)  // 返回上一页
    // 注：back和go里面都可以放数值，-1返回上一级，-2返回上上级
```

#### 重新加载当前页

```
    window.location.reload()
```

#### 打开新标签页

```
    const { href } = this.$router.resolve({
      path: '/orderDtl',
      query: { id: '', shop: '' }
    })
    window.open(href, '_blank')
```

#### 关闭当前标签页

```
    window.location.href = 'about:blank'
    window.close()
```

#### uniapp上的路由跳转

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
