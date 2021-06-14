1. 宏任务与微任务
- 宏任务：setInterval()、setTimeout()
- 微任务：new Promise()
- 同一次事件循环中，微任务永远在宏任务之前执行；

2. js精度问题
```
  0.1 + 0.2 != 0.3
  0.1 + 0.2 !== 0.3
```

3. 如何避免内存泄露：
- 尽可能少创建全局变量；
- 手动清除定时器；
- 少用闭包；
- 清除DOM引用；

4. Virtual DOM和真实DOM的区别和优化：
- 虚拟DOM不会立马进行排版和重绘操作；
- 虚拟DOM进行频繁修改，然后一次性比较并修改真实DOM中需要改的部分，最后在真实DOM中进行排版与重绘，减少过多DOM节点排版与重绘损耗；
- 虚拟DOM有效降低大面积真实DOM的重绘与排版，因为最终与真实DOM比较差异，可以只渲染局部；

5. call与bind函数
- call()方法在使用一个指定的this值和若干个指定的参数值的前提下调用某个函数或方法，call改变了this的指向；
- bind()方法会创建一个新函数，可以返回一个函数，可以传入参数；
```
  let foo = { value: 1 }
  function bar() {
    console.log(this.value)
  }

  bar.call(foo)   // 输出1

  let bindFoo = bar.bind(foo)
  bindFoo()   // 输出1
```

6. new 运算符
- new 运算符创建一个用户定义的对象类型的实例或具有构造函数的内置对象类型之一；
- new 的结果是一个新对象；

7. 
- 类数组对象：最基本的要求就是具有length属性的对象；
- Array.from()方法：将一个类数组对象或者可遍历对象转换成一个真正的数组；
```
  let array = {0: 'name', 1: 'age', 2: 'sex'}
  Array.from(array)   // 输出["name", "age", "sex"] 
  Array.prototype.slice.call(array)      // 输出["name", "age", "sex"] 
  Array.prototype.splice.call(array, 0)  // 输出["name", "age", "sex"] 
```

8. ES6 ...扩展运算符
- 合并数组；
- 与解构赋值结合起来，生成数组；
- 将字符串转为真正的数组；
```
  let arr1 = [10, 20, 30]
  let arr2 = [12, ...arr1]  // 输出[12, 10, 20, 30]
  let [...arr3] = arr2 
  console.log(arr3)  // 输出[12, 10, 20, 30]
  let [arr4, ...arr5] = arr3
  console.log(arr4, arr5)   // 输出12, [10, 20, 30]
  [...'hello']       // 输出['h', 'e', 'l', 'l', 'o']
```

9. 
- JavaScript共7种数据类型：Undefined、Null、Boolean、Number、String、Object、Symbol；
```
  console.log(null + 1)  // 输出1
  console.log([] + [])   // 输出空字符串""
  console.log([] + {})   // 输出[object Object]
  console.log({} + [])   // 输出[object Object]
  console.log(null == undefined)  // 输出true
  console.log('1' == 1)  // 输出true
```

