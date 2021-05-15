#### 输入查询匹配或下拉选择

    <el-select
      ref="customer"
      v-model="customer"
      filterable
      clearable
      remote
      placeholder="输入查询匹配或下拉选择"
      :remote-method="doCustomerFilter"
      :loading="loading"
    >
      <el-option v-for="item in customerList" :key="item.uuid" :value="item.uuid" :label="'[' + item.code + ']' + item.name"></el-option>
    </el-select>

```
    doCustomerFilter(query: string = '') {
      const param = new QueryParam()
      param.start = 0
      param.limit = 20
      query && param.filters.push({ property: 'keyword:%=%', value: query })
      this.customerList = []
      this.loading = true
      CustomerApi.query(param)
        .then((resp) => {
          this.loading = false
          this.customerList = resp.data || []
        })
        .catch((e) => {
          this.loading = false
          this.$message.error(e.message)
        })
    }
```

#### 输入框保留两位小数

```
  handle(data: any) {
    if (!isNaN(data) && data > 0) {
      //
    } else {
      this.amount = null
    }
    const a = data.toString().indexOf('.') // 判断是否是小数
    if (!isNaN(data) && a > 0) {
      const b = String(data).length - a - 1 // 判断是几位小数
      const c = Number(data)
      if (b > 2) {
        const d = c.toFixed(2) // 保留两位小数
        this.amount = Number(d)
      }
    }
  }

```

#### watch 监听事件

```
  @Watch('saveReq.cycle')
  onChange(val: string, oldVal: string) {
    console.log(val, newVal)   // 监听对象saveReq中的cycle字段的原值、现值 
  }
```

#### Object.assign 用法

- Object.assign() 方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象，它将返回目标对象；
- 
- 如果目标对象中的属性具有相同的键，则属性将被源中的属性覆盖，即后来的源的属性将类似地覆盖早先的属性；
- 
- Object.assign 方法只会拷贝源对象自身的并且可枚举的属性到目标对象；
- 
- Object.assign 不会跳过那些值为 [null] 或 [undefined]的源对象。

```
  Object.assign(target, ...sources)  // target: 目标对象，sources: 源对象
```