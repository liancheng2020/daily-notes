#### CSS

- 单行超出省略
```
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
```
- 双行超出省略
```
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
  // autoprefixer: on
  -webkit-line-clamp: 2;
```
- 三角形
```
  width: 0;
  height: 0;
  border-width: 0 40px 40px;
  // border-width: 0 40px 40px 0;
  // 设置左边border宽度为0，则为直角三角形
  border-style: solid;
  border-color: transparent transparent red;
```


#### Regex校验

- 表情包校验
```
  value = value
    .replace(
      /\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDE4F]|[\uD800-\uDBFF]|[\uDC00-\uDFFF]|[^\u0020-\u007E\u00A0-\u00BE\u2E80-\uA4CF\uF900-\uFAFF\uFE30-\uFE4F\uFF00-\uFFEF\u0080-\u009F\u2000-\u201f\u2026\u2022\u20ac\r\n]/g,
        ''
      )
    .trim() 
```
- 只允许输入正整数
```
  value = value.replace(/[^\d]/g, '') 
```
- 字符串去掉首尾空格
```
  str = str.replace(/(^\s*)|(\s*$)/g, '')   
```
- 保留两位小数校验
```
  regex = /^(([1-9]{1}\d*)|(0{1}))(\.\d{1,2})?$/
```
- 6位连续重复的数字校验
```
  regex = /^(?=\d+)(?!([\d])\1{5})[\d]{6}$/
```
- 手机号校验正则表达式
```
  regex = /^1[3-9][0-9]{9}$/
```
- 8-16位数字、大小写英文或二者的结合正则表达式
```
  regex = /^[A-Za-z0-9]{8,16}$/
```
- 8-16位数字、字母组合密码正则表达式
```
  regex = /^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z]{8,16}$/
```


#### Url相关

- 页面跳转
```
    window.location.href = "url"
```
- 返回上一页
```
    window.history.length  // 当前页的历史列表长度
    window.history.back()  // 返回上一页
    window.history.go(-1)  // 返回上一页
    // 注：back和go里面都可以放数值，-1返回上一级，-2返回上上级
```
- 重新加载当前页
```
    window.location.reload()
```
- 打开新标签页
```
    const { href } = this.$router.resolve({
      path: '/orderDtl',
      query: { id: '', shop: '' }
    })
    window.open(href, '_blank')
```
- 关闭当前标签页
```
    window.location.href = 'about:blank'
    window.close()
```
- uniapp上的路由跳转
```
  uni.navigateTo({ url: '/pages/home/Home' })    // 保留当前页面，跳转到应用内的某个页面
  uni.redirectTo({ url: '/pages/home/Home' })    // 关闭当前页面，跳转到应用内的某个页面
  uni.reLaunch({ url: '/pages/home/Home' })      // 关闭所有页面，打开到应用内的某个页面
  uni.switchTab({ url: '/pages/home/Home' })     // 跳转到tabBar页面，并关闭其他所有非tabBar页面
  uni.navigateBack({ url: '/pages/home/Home' })  // 关闭当前页面，返回上一页面或多级页面
```