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

10. typeof 与 instanceof 区别：
- typeof：一般被用于判断变量的类型，但是在判断object的数据时，只能告诉我们这个数据是 object, 而不能细致的具体到是哪一种object；
- instanceof：用来判断对象的具体类型（判断一个实例是否属于某种类型）；
```
  typeof undefined   // 输出undefined
  typeof null        // 输出object

  let error = new Error()
  typeof error === 'object'   // 输出true
  error instanceof Error      // 输出true
```

11. 
- 事件传播：捕获-目标-冒泡阶段；

12. 
- 行内元素：a、span、label、strong、em、 br、 img、input、select、textarea等；
- 块级元素：div、h1~h6、p、form、ul、li、ol、dl、address、hr、menu、table等；

13. 
- 内存泄漏：无用的内存还在占用，得不到释放和归还，比较严重时，无用的内存会持续递增，从而导致整个系统卡顿，甚至崩溃；
- 内存泄漏场景：全局变量、计时器、事件监听器、闭包、ES6 Set相关和Map键名等；

14. 页面生成过程：
- HTML 被 HTML 解析器解析成 DOM 树；
- CSS 被 CSS 解析器解析成 CSSOM 树；
- 结合 DOM 树和 CSSOM 树，生成一棵渲染树(Render Tree)，这一过程称为 Attachment；
- 生成布局(flow)，浏览器在屏幕上“画”出渲染树中的所有节点；
- 将布局绘制(paint)在屏幕上，显示出整个页面；

15. 
- 重排：也叫回流，重新生成布局，重新排列元素；
- 重绘：当一个元素的外观发生改变，但没有改变布局，重新把元素外观绘制出来的过程；

16. 千位分隔符
```
  let a = 1206688
  a.toLocaleString()  // 输出"1,206,688"
```

17. 




