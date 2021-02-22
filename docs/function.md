#### 输入查询匹配

    <el-select
      ref="customer"
      v-model="customer"
      filterable
      clearable
      remote
      placeholder="客户代码/名称"
      :remote-method="doCustomerFilter"
      :loading="loading"
    >
      <el-option v-for="item in customerList" :key="item.uuid" :value="item.uuid" :label="'[' + item.code + ']' + item.name"></el-option>
    </el-select>

```javascript

  doCustomerFilter(query: string) {
    if (query !== '') {
      const param = new QueryParam()
      param.start = 0
      param.limit = 20
      param.filters.push({ property: 'keyword:%=%', value: query })
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
    } else {
      this.loading = false
      this.customerList = []
    }
  }
```