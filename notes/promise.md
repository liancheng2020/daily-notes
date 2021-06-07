#### Promise 基本用法

```
  getUuid() {
    return new Promise((resolve, reject) => {
      SkuApi.getUuid()
        .then((resp) => {
          resolve(resp.data)
        })
        .catch((error) => {
          reject(error)
        })
    })
  }
```

#### Promise.all 用法

```
  Promise.all([this.query1(), this.query2(), this.query3()]).then(() => {
      this.queryAll()  // 执行完query1、query2、query3函数后，再执行queryAll函数
    })
```