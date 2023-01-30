1. JavaScript 有哪些数据类型？它们有哪些区别？

-   JavaScript 共有八种数据类型，分别是 Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt；
-   其中 Symbol 和 BigInt 是 ES6 中新增的数据类型：
    -   Symbol 代表创建后独一无二且不可变的数据类型，它主要是为了解决可能出现的全局变量冲突的问题；
    -   BigInt 是一种数字类型的数据，它可以表示任意精度格式的整数，使用 BigInt 可以安全地存储和操作大整数，即使这个数已经超出了 Number 能够表示的安全整数范围；
-   这些数据可以分为原始数据类型和引用数据类型：
    -   栈：原始数据类型（Undefined、Null、Boolean、Number、String）；
    -   堆：引用数据类型（对象、数组和函数）；

2. 数据类型检测的方式有哪些？

-   typeof：其中数组、对象、null 都会被判断为 object；

```
    console.log(typeof 2)              // number
    console.log(typeof true)           // boolean
    console.log(typeof 'str')          // string
    console.log(typeof [])             // object
    console.log(typeof function(){})   // function
    console.log(typeof {})             // object
    console.log(typeof undefined)      // undefined
    console.log(typeof null)           // object
```

-   instanceof：可以正确判断对象的类型，其内部运行机制是\*\*\*\*判断在其原型链中能否找到该类型的原型；
    -   instanceof 只能正确判断引用数据类型，而不能判断基本数据类型；
    -   instanceof 运算符可以用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性；

```
    console.log(2 instanceof Number)                // false
    console.log(true instanceof Boolean)            // false
    console.log('str' instanceof String)            // false

    console.log([] instanceof Array)                // true
    console.log(function(){} instanceof Function)   // true
    console.log({} instanceof Object)               // true
```

-   constructor：有两个作用，一是判断数据的类型，二是对象实例通过 constructor 对象访问它的构造函数；
    -   如果创建一个对象来改变它的原型，constructor 就不能用来判断数据类型了；

```
    function Fn(){}
    Fn.prototype = new Array()
    var f = new Fn()

    console.log(f.constructor === Fn)      // false
    console.log(f.constructor === Array)   // true
```

-   Object.prototype.toString.call()：使用 Object 对象的原型方法 toString 来判断数据类型；

```
    var a = Object.prototype.toString

    console.log(a.call(2))              // [object Number]
    console.log(a.call(true))           // [object Boolean]
    console.log(a.call('str'))          // [object String]
    console.log(a.call([]))             // [object Array]
    console.log(a.call(function(){}))   // [object Function]
    console.log(a.call({}))             // [object Object]
    console.log(a.call(undefined))      // [object Underfined]
    console.log(a.call(null))           // [object Null]
```

3. 判断数组 arr 的方式有哪些？

-   通过 Object.prototype.toString.call()做判断：

```
    Object.prototype.toString.call(arr).slice(8,-1) === 'Array'
```

-   通过原型链做判断：

```
    arr.__proto__ === Array.prototype
```

-   通过 ES6 的 Array.isArray()做判断：

```
    Array.isArrray(arr)
```

-   通过 instanceof 做判断：

```
    arr instanceof Array
```

-   通过 Array.prototype.isPrototypeOf()做判断：

```
    Array.prototype.isPrototypeOf(arr)
```

4. undefined 与 null 之间的区别？

-   undefined：表示"缺少值"，就是此处应该有一个值，但是还没有定义；
-   null：表示"没有对象"，即该处不应该有值；
-   undefined 的类型（typeof）是 undefined，null 的类型 (typeof) 是 object；
-   undefined 转换数值时为 NaN，null 转换数值时为 0；
-   js 将未赋值的变量默认值设为 undefined，js 从来不会将变量设为 null，它是用来表明某个用 var 声明的变量时没有值的；

5. JavaScript object？

-   JavaScript 中无论是字符串、数值、数组还是函数，其本质都是对象；
-   JavaScript 允许自定义对象，对象只是带有属性和方法的特殊数据类型；
-   属性是与对象相关的值，方法是能够在对象上执行的操作；

6. let、var 与 const 的区别？

-   let 和 const 声明的变量只在它所在的代码块内有效；
-   let 和 const 不允许在相同作用域内，重复声明一个变量；
-   let 和 const 不存在“变量提升”现象，即变量一定要在声明后使用，否则报错；
-   var 命令会发生“变量提升”现象，即变量可以在声明之前使用，值为‘undefined’；
-   const 声明一个只读的变量，一旦声明，常量的值就不能改变，且只声明不赋值，也会报错；

7. for...in 与 for...of 的区别？

-   for...in 遍历后返回键名（key），for...of 遍历后返回键值（value）；
-   for...in 会遍历对象的整个原型链，性能非常差不推荐使用，而 for...of 只遍历当前对象不会遍历原型链；
-   for...in：主要是为了遍历对象而生，不适用于遍历数组；
-   for...of：可以用来遍历数组、类数组对象，字符串、Set、Map 以及 Generator 对象，普通的对象用 for...of 遍历是会报错的；

8. new 操作符的执行过程？

-   首先创建了一个新的空对象；
-   设置原型，将对象的原型设置为函数的 prototype 对象；
-   让函数的 this 指向这个对象，执行构造函数的代码（为这个新对象添加属性）；
-   判断函数的返回值类型，如果是值类型，返回创建的对象；如果是引用类型，就返回这个引用类型的对象；

9. 箭头函数与普通函数的区别？

-   箭头函数没有 prototype，也没有自己的 this 指向；
-   箭头函数继承来的 this 指向永远不会改变；
-   call()、apply()、bind()等方法不能改变箭头函数中 this 的指向；
-   箭头函数不能作为构造函数使用，使用 new 调用箭头函数会报错；

10. JavaScript 的原型、原型链有什么特点？

-   原型：
    -   简单概括：每个对象都会在内部初始化一个属性，就是 prototype（原型）；
    -   js 中是使用构造函数来新建一个对象，每一个构造函数都有一个 prototype 属性，它的属性值是一个对象，这个对象包含了由该构造函数的所有实例共享的属性和方法；
    -   使用构造函数创建一个对象后，在对象内部将包含一个指针，这个指针指向构造函数 prototype 属性对应的值，即所谓的原型；
-   原型链：
    -   当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么它就会去它的 prototype（原型对象）里找这个属性，这个 prototype 又会有自己的 prototype，于是这样一直找下去，也就是我们所说的原型链的概念。
-   原型链特点：
    -   JavaScript 对象是通过引用来传递的，我们创建的每个新对象实体中并没有属于自己的原型副本；
    -   当我们修改原型时，与之相关的对象也会继承这一改变；

11. 什么是闭包（closure），为什么要用它？

-   闭包是指有权访问另一个函数作用域中变量的函数；
-   创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量；
-   利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
-   闭包的特性：
    -   函数内再嵌套函数；
    -   内部函数可以引用外层的参数和变量；
    -   参数和变量不会被垃圾回收机制回收；

12. 对 this 对象的理解?

-   this 总是指向函数的直接调用者（而非间接调用者）；
-   如果有 new 关键字，this 指向 new 出来的那个对象；
-   在事件中，this 指向触发这个事件的对象，特殊的是，IE 中的 attachEvent 中的 this 总是指向全局对象 Window；

13. 对 JSON 的了解？

-   JSON(JavaScript Object Notation)是一种轻量级的数据交换格式；
-   它是基于 JavaScript 的一个子集，数据格式简单, 易于读写, 占用带宽小；

14. document.write 和 innerHTML 的区别？

-   document.write 只能重绘整个页面；
-   innerHTML 可以重绘页面的一部分；

15. setInterval()与 setTimeout()的区别？

-   setInterval()：循环调用，将一段代码，每隔一段时间执行一次（循环执行）；
-   setTimeout()：延时调用，将一段代码，等待一段时间之后再执行（只执行一次）；

16. Javscript 的事件？

-   JavaScript 使我们有能力创建动态页面，事件是可以被 JavaScript 侦测到的行为；
-   网页中的每个元素都可以产生某些可以触发 JavaScript 函数的事件，比方说，我们可以在用户点击某按钮时产生一个 onClick 事件来触发某个函数，事件在 HTML 页面中定义；
-   当用户进入或离开页面时就会触发 onload 和 onUnload 事件；
-   表单里面使用的 onFocus、onBlur、onChange；

17. Javascript 绑定事件的方法?

-   嵌入 DOM：

```
    <button onclick="open()">按钮</button>
    <script>
        function open(){
            alert(1);
        }
    </script>
```

-   直接绑定：

```
    <button id="btn">按钮</button>
    <script>
        document.getElementById('btn').onclick = function(){
            alert(1);
        }
    </script>
```

-   事件监听：

```
    <button id="btn">按钮</button>
    <script>
        document.getElementById('btn').addEventListener('click',function(){
            alert(1);
        })
        document.getElementById('btn').attachEvent('click',function(){
            alert(1);
        })
    </script>
```

18. 同步和异步的区别?

-   同步强调的是顺序性，谁先谁后，异步则不存在这种顺序性；
-   同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求，等请求完，页面刷新，新内容出现，用户看到新内容，进行下一步操作；
-   异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求；等请求完，页面不刷新，新内容也会出现，用户看到新内容；

19. JavaScript 异步加载的方式有哪些?

-   利用 setTimout 实现异步；
-   动态创建 script 标签；
-   利用 script 标签提供的 async；
-   使用 Promise 对象；

20. Proxy 的了解？

-   Vue3.0 要使用 Proxy 替换原本的 API 原因在于：
    -   Proxy 无需一层层递归为每个属性添加代理，一次即可完成以上操作，性能上更好，并且原本的实现有一些数据更新不能监听到，但是 Proxy 可以完美监听到任何方式的数据改变，唯一缺陷就是浏览器的兼容性不好；

21. 类数组如何转换为数组？

-   通过 call 调用数组的 slice()方法来实现转换；
-   通过 call 调用数组的 splice()方法来实现转换；
-   通过 apply 调用数组的 concat()方法来实现转换；

```
    Array.prototype.slice.call(arrayLike)
    Array.prototype.splice.call(arrayLike, 0)
    Array.prototype.concat.apply([], arrayLike)
```

-   使用 Array.from()方法将类数组转化成数组；
-   使用展开运算符（...）将类数组转化成数组；

22. Promise 的理解？

-   Promise 对象是异步编程的一种解决方案，有三种状态：pending（进行中）、fulfilled（已成功）和 rejected（已失败）；
-   Promise 是一个构造函数，接收一个函数作为参数，返回一个 Promise 实例；
-   Promise 实例有三种状态，分别是 pending、resolved 和 rejected，分别代表了进行中、已成功和已失败；

23. async 和 await 的理解？

-   async/await 其实是 Generator 的语法糖；
-   async 函数返回的是一个 Promise 对象；
-   await 等待的是一个表达式，这个表达式的计算结果是 Promise 对象或者其它值；
