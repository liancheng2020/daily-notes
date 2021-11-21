1. 宏任务与微任务
- 宏任务：setInterval()、setTimeout()；
- 微任务：new Promise()；
- 宏任务会被丢到下一次事件循环，并且宏任务队列每次只会执行一个任务；
- 微任务会被丢到本次事件循环，并且微任务队列每次都会执行任务直到队列为空；
- 同一次事件循环中，微任务永远在宏任务之前执行。

2. js精度问题
```
  0.1 + 0.2 != 0.3
  0.1 + 0.2 !== 0.3
```

3. 事件传播
- 事件传播：捕获-目标-冒泡阶段；

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

7. Array.from()
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

9. js 数据类型
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

11. 行内元素与块级元素
- 行内元素：a、span、label、strong、em、 br、 img、input、select、textarea等；
- 块级元素：div、h1~h6、p、form、ul、li、ol、dl、address、hr、menu、table等；

12. 内存泄漏相关：
- 定义：无用的内存还在占用，得不到释放和归还，比较严重时，无用的内存会持续递增，从而导致整个系统卡顿，甚至崩溃；
- 场景：全局变量、计时器、事件监听器、闭包、ES6 Set相关和Map键名等；
- 避免：尽可能少创建全局变量、手动清除定时器、少用闭包、清除DOM引用等。

13. 页面生成过程：
- HTML 被 HTML 解析器解析成 DOM 树；
- CSS 被 CSS 解析器解析成 CSSOM 树；
- 结合 DOM 树和 CSSOM 树，生成一棵渲染树(Render Tree)，这一过程称为 Attachment；
- 生成布局(flow)，浏览器在屏幕上“画”出渲染树中的所有节点；
- 将布局绘制(paint)在屏幕上，显示出整个页面；

14. 重排与重绘
- 重排：也叫回流，重新生成布局，重新排列元素；
- 重绘：当一个元素的外观发生改变，但没有改变布局，重新把元素外观绘制出来的过程；

15. 千位分隔符
```
  let a = 1206688
  a.toLocaleString()  // 输出"1,206,688"
```

16. css 盒模型
- 标准盒子模型：width和height指的是content的宽度和高度；
- IE盒子模型：width和height指的是content + padding + border的宽度和高度；
- 在不设置box-sizing的情况下，box-sizing默认是content-box；
```
  box-sizing: content-box; // 标准盒子
  box-sizing: border-box;  // IE盒子
```

17. BFC 块级格式上下文
- 触发BFC的条件：
  - 浮动元素(float除了node以外的值)；
  - 定位元素(position: absolute/ fixed)；
  - display(值为inline-block/ table-cell/- table-caption/ flex/ inline-flex)；
  - overflow(值为hidden/atuo/srcoll)设置有这些属性的box，都会产生BFC；
- BFC特性：
  - 内部的盒子在垂直方向上一个接一个地放置；
  - 垂直方向上地距离由margin决定，在同一个BFC的box中，相邻的两个box边距会重叠；
  - BFC的区域不会与float box重叠；
  - 计算BFC的高度时，浮动元素也参与计算；
  - BFC就是一个独立的容器，里面的子元素不受外面的元素影响；
- BFC的作用：
  - 解决margin重叠问题（添加独立BFC）；
  - 解决浮动高度塌陷问题（在父元素添加overflow：hidden）。

18. 
```
  Boolean('false')   // 输出true
  Boolean(false)     // 输出false
  Boolean(null)      // 输出false
```

19. v-model 修饰符
- v-model.lazy：input框绑定数值在“change”时而非“input”时更新；
- v-model.number：自动将用户的输入值转为数值类型；
- v-model.trim：自动过滤用户输入的首尾空白字符；

20. async 和 await
- await只能在async函数中使用，不然会报错；
- async函数返回的是一个状态为fuifilled的Promise对象，有无值看有无return值；
- await后面只有接了Promise才能实现排队效果；
- async/await作用是用同步方式，执行异步操作；
```
  async fn () {
    const res1 = await query1()
    const res2 = await query2()
    const res3 = await query3()
    console.log(res3) // 依次执行query1、query2、query3方法后，输出res3
  }
```

21. Promise.all()
- 将多个 Promise 对象执行完毕后，生成返回一个新的 Promise 实例；
```
  let p1 = Promise.resolve(1)
  let p2 = Promise.resolve(2)
  let p3 = Promise.resolve(3)

  Promise.all([p1, p2, p3]).then((result: any) => {
    console.log(result)  // 输出[1, 2, 3]
  })
```

22. input框-回车事件
- input框的回车事件：@keydown.enter.native

23. display: none 与 visible: hidden的区别：
```
  display: none   --- 隐藏元素，不保留物理空间；
  visible: hidden --- 隐藏元素，物理空间还在；
```

24. Set 相关
- ES6提供了新的数据结构Set，它类似于数组，但是成员的值都是唯一的，没有重复的值；
- Set本身是一个构造函数，用来生成Set数据结构，不会添加重复的值；
- 向Set加入值的时候，不会发生类型转换，所以5和'5'是两个不同的值；
- Array.from方法可以将Set结构转为数组；
- Set 结构没有键名，只有键值（或者说键名和键值是同一个值）；

- add(value)：添加某个值，返回Set对象本身；
- delete(value)：删除某个值，成功返回true，失败返回false；
- has(value)：判断某个值是否在当前Set对象之中，是返回true，否返回false；
- clear()：删除所有的键/值对，没有返回值；
```
  const a = new Set([1, 2, 3])
  const b = new Set([4, 3, 2])
  const unionSet = new Set(...a, ...b)  // 并集 {1, 2, 3, 4} 
  const interSet = new Set([...a].filter(x => b.has(x)))  // 交集 {2, 3}

  const c = new Set('aaabbbbc')
  const duplSet = [...c].join('')  // 字符串去重 'abc'
```

25. String 实例方法
- includes()
  - 返回布尔值，表示是否找到了参数字符串；
- startsWith()
  - 返回布尔值，表示参数字符串是否在原字符串的头部；
- endsWith()
  - 返回布尔值，表示参数字符串是否在原字符串的尾部；

- 三个方法都支持第二个参数，表示开始搜索的位置；
- 使用第二个参数n时，endsWith的行为与其他两个方法有所不同，它针对前n个字符，而其他两个方法针对从第n个位置直到字符串结束；

- search()
  - 查找匹配的字符串，返回匹配的位置索引，失败时返回-1；

- repeat()
  - 返回一个新字符串，表示将原字符串重复n次；
  - 参数如果是小数，会被取整；
  - 参数是负数或Infinity，会报错；
```
  const str = 'abc'
  str.repeat(3)    // 'abcabcabc'
  str.repeat(1.8)  // 'abcabc'
  str.repeat(2.5)  // 'abcabc'
  str.repeat(-1)   // RangeError报错
```

- trimStart()、trimEnd()
  - trimStart()消除字符串头部的空格，trimEnd()消除尾部的空格；
  - 它们返回的都是新字符串，不会修改原始字符串；
  - 浏览器还部署了额外的两个方法，trimLeft()是trimStart()的别名，trimRight()是trimEnd()的别名；

- replaceAll()
  - 一次性替换所有匹配；
  - 用法与replace()相同，返回一个新字符串，不会改变原字符串；
```
  const str = 'aabbcc'
  str.replace('b', '_')      // 'aa_bcc'
  str.replace(/b/g, '_')     // 'aa__cc'
  str.replaceAll('b', '_')   // 'aa__cc'
```

26. Object.is()
- 比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致；
```
  +0 === -0     // true
  NaN === NaN   // false

  Object.is(+0, -0)    // false
  Object.is(NaN, NaN)  // true
```

27. Object.assign()
- 方法实行的是浅拷贝，而不是深拷贝；
- 可以用来处理数组，但是会把数组视为对象；
```
  const obj1 = {a: 1001}
  const obj2 = Object.assign({}, obj1)  // {a: 1001}
  obj1.a = 1002
  console.log(obj2)  // 输出{a: 1002}

  Object.assign([1, 2, 3], [4, 5])  // [4, 5, 3]
```

28. 指数运算符 **
- 多个运算符连用时，是从最右边开始计算的
```
  2 ** 3 ** 2   // 相当于2 **（3 ** 2）= 512
```

29. Promise.finally()
- Promise.finally()：不管promise状态如何，都会执行的操作；

30. 表单校验：clearValidate()用法
```
  <el-form-item ref="target"></el-form-item>

  this.$refs.target.clearValidate()  // 清除该表单的校验
```

31. iframe 优点和缺点：
- 优点：
  - 用来加载速度较慢的内容；
  - 可以使脚本并行下载；
  - 可以实现跨子域通信；
- 缺点：
  - iframe会阻塞主页面的onload事件；
  - 无法被一些搜索引擎识别；
  - 会产生很多页面，不容易管理。

32. 渐进增强和优雅降级的区别：
- 渐进增强：主要针对低版本的浏览器进行页面重构，再针对高级浏览器进行效果、交互等方面的改进和追加功能；
- 优雅降级：一开始就构建完整的功能，然后再针对低代码的浏览器进行兼容。

33. CSS 选择器优先级
- 内联样式 》id选择器 》类选择器、伪类选择器 》标签选择器、伪元素选择器；
- !important 声明的样式的优先级最高。

34. 伪类、伪元素：
- 伪类是通过在元素选择器上加入伪类改变元素状态；
- 伪元素是通过对元素的操作进行对元素的改变；
- 冒号（:）用于伪类，双冒号（::）用于伪元素。
```
  // 伪类
  a:hover { color: #ffffff }
  p:first-child { color: red }

  // 伪元素
  p::before { content: '一 ' }
  p::first-line { background: red }
```

35. CSS 预处理器 scss、less，为什么使用它们？
- 结构清晰，便于扩展；
- 可以很方便屏蔽浏览器私有语法之间的差异；
- 可以轻松实现多重继承；
- 完美的兼容了CSS代码，可以应用到老项目中。

36. Webpack能处理 CSS 吗？如何实现？
- Webpack在loader的辅助下，是可以处理CSS的；
- Webpack中操作CSS使用的两个关键的loader：css-loader 和 style-loader；
  - css-loader：导入CSS模块，对CSS代码进行编译处理；
  - style-loader：创建style标签，把CSS内容写入标签；
- 在实际使用中，css-loader的执行顺序一定排在style-loader之前，因为只有完成了编译过程，才能对css代码进行插入。

37. CSS 布局单位：
- em：相对于父元素；
- rem：相对于根元素；

38. 判断是数组的方式：
- 通过Object.prototype.toString.call()做判断；
- 通过原型链做判断；
- 通过ES6的Array.isArray()做判断；
- 通过instanceof做判断；
- 通过Array.prototype.isPrototypeOf做判断；
```
  const arr = [12, 30, 90]

  Object.prototype.toString.call(arr)   // 输出'[object Array]'
  Object.prototype.toString.call(arr).slice(8,-1) === 'Array'  // true

  arr.__proto__ === Array.prototype  // true

  Array.isArray(arr)     // true

  arr instanceof Array   // true

  Array.prototype.isPrototypeOf(arr)  // true
```

39. for in与for of的区别：
- for...in：可以遍历对象、数组，返回键名（key）；
- for...of：只能遍历数组，返回键值（value）；
- for...in 循环主要是为了遍历对象而生，不适用于遍历数组；
- for...of 循环可以用来遍历数组、类数组对象，字符串、Set、Map 以及 Generator 对象；

40. 
- 数组和字符串的转换方法：toString()、toLocalString()、join()；

41. git pull和git fetch区别：
- git pull会将远程仓库的变化下载下来，并和当前分支合并；
- git fetch只是将远程仓库的变化下载下来，并没有和本地分支合并；

42. git merge和 git rebase的区别：
- git merge和git rebase都是用于分支合并，关键在commit记录的处理上不同；
- git merge会新建一个新的commit对象，然后两个分支以前的commit记录都指向这个新commit记录，保留了之前每个分支的commit历史；
- git rebase会先找到两个分支的第一个共同的commit记录，再提取当前分支这之后的所有commit记录，然后将这个commit记录添加到目标分支的最新提交后面，经过这个合并后，两个分支合并后的commit记录就变为了线性的记录了；

43. 原型链相关：
- 原型定义：在JavaScript中是使用构造函数来新建一个对象的，每一个构造函数的内部都有一个 prototype 属性，它的属性值是一个对象，这个对象包含了可以由该构造函数的所有实例共享的属性和方法。当使用构造函数新建一个对象后，在这个对象的内部将包含一个指针，这个指针指向构造函数的 prototype 属性对应的值，在 ES5 中这个指针被称为对象的原型；

- 原型链定义：当访问一个对象的属性时，如果这个对象内部不存在这个属性，那么它就会去它的原型对象里找这个属性，这个原型对象又会有自己的原型，于是就这样一直找下去，也就是原型链的概念；

- 原型链的终点：由于Object是构造函数，原型链终点是Object.prototype.__proto__；而Object.prototype.__proto__=== null（结果为true），所以原型链的终点是null；原型链上的所有原型都是对象，所有的对象最终都是由Object构造的，而Object.prototype的下一级是Object.prototype.__proto__；

44. 闭包相关：
- 闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，创建的函数可以访问到当前函数的局部变量；











