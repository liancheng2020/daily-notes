#### Array遍历方法

- forEach()
  - 不会改变原来的数组，也没有返回值；
  - 无法使用break、continue跳出循环；

- map()
  - 遍历数组，返回一个新数组，不会改变原数组；

- filter()
  - 过滤数组，返回由符合条件的元素组合的新数组，不会改变原数组；
  - 适用于检测数组，不会对空数组检测；

- some()、every()
  - some(): 遍历数组的每一项，只要有一个元素符合条件，就返回true，否则返回false；
  - every(): 遍历数组的每一项，只有所有元素都符合条件，才返回true，否则返回false；
  - 两者都不改变原数组，只会返回一个布尔值；
  - 两者都适用于检测数组，不会对空数组检测；

- find()、findIndex()
  - find(): 返回数组中符合条件的第一个元素的值，否则返回 undefined；
  - findIndex(): 返回数组中满足符合条件的第一个元素的索引，否则返回 -；
  - 两者都不会改变原数组，对空数组不执行；

- reduce()、reduceRight()
  - reduce(): 为数组中的每一个元素依次执行回调函数；
  - reduceRight()方法与reduce()用法几乎一致，只是该方法是对数组进行倒序遍历的，而reduce()方法是正序遍历的；
  - 两者都不会改变原数组，对空数组不执行；
```
  let arr = [1, 2, 3, 4]
  let sum = arr.reduce((prev, cur, index, arr) => {
      return prev + cur
  })  
  console.log(arr, sum)  // 输出结果：[1, 2, 3, 4] 10

  let arr = [1, 2, 3, 4]
  let sum = arr.reduce((prev, cur, index, arr) => {
      return prev + cur
  }, 5)  
  console.log(arr, sum)  // 输出结果：[1, 2, 3, 4] 15
```

- keys()、values()、entries()
  - keys() 返回数组的索引值；
  - values() 返回数组的元素；
  - entries() 返回数组的键值对；
```
  let arr = ['Red', 'Green', 'Blue']
  const arr1 = arr.keys()
  const arr2 = arr.values() 
  const arr3 = arr.entries() 

  for (let item of arr1) {
    console.log(item)
  }
  // 输出结果：0 1 2 

  for (let item of arr2) {
    console.log(item)
  }
  // 输出结果：Red Green Blue

  for (let item of arr3) {
    console.log(item)
  }
  // 输出结果：[0, 'Red'] [1, 'Green'] [2, 'Blue']
```

#### Array常用方法

- join: 通过指定连接符生成字符串；

- push / pop: 末尾推入和弹出，改变原数组， 返回推入/弹出项；

- unshift / shift: 头部推入和弹出，改变原数组，返回操作项；

- sort / reverse: 排序与反转，改变原数组；

- concat: 连接数组，不影响原数组， 浅拷贝；

- slice(start, end): 返回截断后的新数组，不改变原数组；

- splice(start, number, value...): 返回删除元素组成的数组，value 为插入项，改变原数组；

- indexOf / lastIndexOf(value, fromIndex): 查找数组项，返回对应的下标；

- includes: 判断数组中是否包含指定的元素，如果是返回 true，否则返回 false；


#### Array.from()方法

- 将一个类数组对象或者可遍历对象转换成一个真正的数组；
- 还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组；

#### Math()相关方法大全

- Math.random(): 返回一个0到1之间的随机数；
- Math.ceil(): 返回一个大于或等于当前数字的整数；
- Math.floor(): 返回一个小于或等于当前数字的整数；
- Math.round(): 返回一个四舍五入最接近当前数字的整数；

#### 保留小数位数

- toFixed(n): 保留 n 位小数（仅适用于Number类型）；
