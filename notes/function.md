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

#### ES6 解构赋值相关

- 数组的解构赋值

```
  const arr1 = [12, 34, 30]
  const arr2 = [10, 20, 30, 40]
  const arr3 = [...arr1, ...arr2]  // [12, 34, 30, 10, 20, 30, 40]
```

- 对象的解构赋值（根据key值--后面的合并前面的）

```
  const str1 = {1: 'aa', 2: 'bb', 3: 'cc'}
  const str2 = {1: 'abc', 2: 'bbc', 3: 'aa', 4: 'bb'}
  const str3 = {...str1, ...str2}   // {1: 'abc', 2 'bbc' 3: 'aa', 4: 'bb'}
  const str4 = {...str2, ...str1}   // {1: "aa", 2: "bb", 3: "cc", 4: "bb"}
```

#### vue 强制更新相关操作

```
  this.$forceUpdate()   // 强制视图刷新
  this.$set(Array, index, newValue)  // 强制更新数组中的某个元素
  this.$set(Object, key, value)      // 强制更新对象中的某个元素
```

#### setTimeout 基础用法

```
  setTimeout(() => {
    console.log(123)  // 500ms后输出123
  }, 500)
```

#### debounce 用法

- 引入 ts-debunce
```
  npm install ts-debounce    // npm安装
  import { debounce } from 'ts-debounce'  // 使用时引入
```
- 相关用法如下：
```
  debounceExport = debounce(this.doExport, 300)  // 300ms后执行
  debounceExport = debounce(this.doExport, 300，{ isImmediate: true })  // 立即执行
```

#### vue 父子组件间的通信

> - 父组件向子组件传值：父组件可以使用props向子组件传递数据；
> - 
> - 子组件向父组件传值：子组件通过$emit触发事件，回调给父组件；
> - 
> - 父组件调用子组件方法：父组件通过$refs调用子组件函数。


#### js 获取本周一所属日期

```
  const today = new Date()  // 今天
  today.setDate(today.getDate() - today.getDay() + 1)  // 设置周一日期
  const month = today.getMonth() + 1  // 所属月份（纯数字）
  const day = today.getDate() >= 10 ? today.getDate() : '0' + today.getDate() // 获取所属日期（dd格式）
  const startDate = today.getFullYear() + '-' + (month >= 10 ? month : '0' + month) + '-' + day  // 获取本周一所属日期（yyyy-MM-dd格式）
```