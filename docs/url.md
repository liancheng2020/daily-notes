#### 页面跳转

```
    window.location.href = "url";
```

#### 返回上一页

```
    window.history.back();
    window.history.go(-1);
    // back和go里面都可以放数值，-1返回上一级，-2返回上上级
```

#### 重新加载当前页

```javascript
    window.location.reload();
```

#### 打开新标签页

```
    const { href } = this.$router.resolve({
      path: '/orderDtl',
      query: { id: '', shop: '' }
    })
    window.open(href, '_blank')
```