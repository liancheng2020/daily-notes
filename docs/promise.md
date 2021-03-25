#### promise基本用法

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