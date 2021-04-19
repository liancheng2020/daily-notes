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