1. JavaScript有哪些数据类型？它们有哪些区别？
- JavaScript共有八种数据类型，分别是Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt；
- 其中Symbol和BigInt是ES6中新增的数据类型：
    - Symbol代表创建后独一无二且不可变的数据类型，它主要是为了解决可能出现的全局变量冲突的问题；
    - BigInt是一种数字类型的数据，它可以表示任意精度格式的整数，使用BigInt可以安全地存储和操作大整数，即使这个数已经超出了Number能够表示的安全整数范围；
- 这些数据可以分为原始数据类型和引用数据类型：
    - 栈：原始数据类型（Undefined、Null、Boolean、Number、String）；
    - 堆：引用数据类型（对象、数组和函数）；

2. 数据检测的方式有哪些？
- typeof：其中数组、对象、null都会被判断为object；
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

- instanceof：可以正确判断对象的类型，其内部运行机制是****判断在其原型链中能否找到该类型的原型；
    - instanceof只能正确判断引用数据类型，而不能判断基本数据类型；
    - instanceof运算符可以用来测试一个对象在其原型链中是否存在一个构造函数的prototype属性；
```
    console.log(2 instanceof Number)                // false
    console.log(true instanceof Boolean)            // false 
    console.log('str' instanceof String)            // false 
    
    console.log([] instanceof Array)                // true
    console.log(function(){} instanceof Function)   // true
    console.log({} instanceof Object)               // true
```

- constructor：有两个作用，一是判断数据的类型，二是对象实例通过constructor对象访问它的构造函数；
    - 如果创建一个对象来改变它的原型，constructor就不能用来判断数据类型了；
```
    function Fn(){}
    Fn.prototype = new Array()
    var f = new Fn()

    console.log(f.constructor === Fn)      // false
    console.log(f.constructor === Array)   // true
```

- Object.prototype.toString.call()：使用Object对象的原型方法toString来判断数据类型；
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

3. 判断数组的方式有哪些？
- 通过Object.prototype.toString.call()做判断：
```
    Object.prototype.toString.call(obj).slice(8,-1) === 'Array'
```
- 通过原型链做判断：
```
    obj.__proto__ === Array.prototype
```
- 通过ES6的Array.isArray()做判断：
```
    Array.isArrray(obj)
```
- 通过instanceof做判断：
```
    obj instanceof Array
```
- 通过Array.prototype.isPrototypeOf()做判断：
```
    Array.prototype.isPrototypeOf(obj)
```

4. undefined与null之间的区别？
- undefined：表示"缺少值"，就是此处应该有一个值，但是还没有定义；
- null：表示"没有对象"，即该处不应该有值； 
- undefined的类型（typeof）是undefined，null的类型 (typeof) 是object；
- undefined转换数值时为NaN，null转换数值时为0；
- js将未赋值的变量默认值设为undefined，js从来不会将变量设为null，它是用来表明某个用var声明的变量时没有值的；

5. JavaScript obiect？
- JavaScript中无论是字符串、数值、数组还是函数，其本质都是对象；
- JavaScript允许自定义对象，对象只是带有属性和方法的特殊数据类型；
- 属性是与对象相关的值，方法是能够在对象上执行的操作；

6. let、var与const的区别？
- let和const声明的变量只在它所在的代码块内有效；
- let和const不允许在相同作用域内，重复声明一个变量；
- let和const不存在“变量提升”现象，即变量一定要在声明后使用，否则报错；
- var命令会发生“变量提升”现象，即变量可以在声明之前使用，值为‘undefined’；
- const声明一个只读的变量，一旦声明，常量的值就不能改变，且只声明不赋值，也会报错；

7. new操作符的执行过程？
- 首先创建了一个新的空对象；
- 设置原型，将对象的原型设置为函数的prototype对象；
- 让函数的this指向这个对象，执行构造函数的代码（为这个新对象添加属性）；
- 判断函数的返回值类型，如果是值类型，返回创建的对象；如果是引用类型，就返回这个引用类型的对象；

8. 箭头函数与普通函数的区别？
- 箭头函数没有prototype，也没有自己的this指向；
- 箭头函数继承来的this指向永远不会改变；
- call()、apply()、bind()等方法不能改变箭头函数中this的指向；
- 箭头函数不能作为构造函数使用，使用new调用箭头函数会报错；

9. JavaScript的原型、原型链有什么特点？
- 每个对象都会在其内部初始化一个属性，就是prototype（原型）；
- 当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，于是这样一直找下去，也就是我们所说的原型链的概念。
- 特点：
  - JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有属于自己的原型副本；
  - 当我们修改原型时，与之相关的对象也会继承这一改变；

10. 什么是闭包（closure），为什么要用它？
- 闭包是指有权访问另一个函数作用域中变量的函数；
- 创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量；
- 利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
- 闭包的特性：
  - 函数内再嵌套函数；
  - 内部函数可以引用外层的参数和变量；
  - 参数和变量不会被垃圾回收机制回收；

11. 对this对象的理解?
- this总是指向函数的直接调用者（而非间接调用者）；
- 如果有new关键字，this指向new出来的那个对象；
- 在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；

12. 对JSON的了解？
- JSON(JavaScript Object Notation)是一种轻量级的数据交换格式；
- 它是基于JavaScript的一个子集，数据格式简单, 易于读写, 占用带宽小；

13. document.write和innerHTML的区别？
- document.write只能重绘整个页面； 
- innerHTML可以重绘页面的一部分；

14. Javscript的事件？
- JavaScript 使我们有能力创建动态页面，事件是可以被 JavaScript 侦测到的行为；
- 网页中的每个元素都可以产生某些可以触发 JavaScript 函数的事件，比方说，我们可以在用户点击某按钮时产生一个 onClick 事件来触发某个函数，事件在 HTML 页面中定义；
- 当用户进入或离开页面时就会触发 onload 和 onUnload 事件；
- 表单里面使用的onFocus、onBlur、onChange；

15. Javascript绑定事件的方法?
- 嵌入DOM：
```
    <button onclick="open()">按钮</button>
    <script>
        function open(){
            alert(1);
        }
    </script>
```
- 直接绑定：
```
    <button id="btn">按钮</button>
    <script>
        document.getElementById('btn').onclick = function(){
            alert(1);
        }
    </script>
```
- 事件监听：
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

16. 同步和异步的区别?
- 同步强调的是顺序性，谁先谁后，异步则不存在这种顺序性；
- 同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求，等请求完，页面刷新，新内容出现，用户看到新内容，进行下一步操作；
- 异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求；等请求完，页面不刷新，新内容也会出现，用户看到新内容；

17. JavaScript异步加载的方式有哪些?
- 利用setTimout实现异步；
- 动态创建script标签；
- 利用script标签提供的async；
- 使用Promise对象；
