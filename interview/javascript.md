1. javascript有哪些基本类型?
- Undefined、Null、Boolean、Number、String；
- Object是复杂数据类型，其本质是由一组无序的名值对组成的；

2. javascript有哪些内置对象？
- Obiect是JavaScript 中所有对象的父对象；
- 数据封装类对象：Object、Array、Boolean、Number、String；
- 其它对象：Function、Argument、Math、RegExp、Error等；

3. JavaScript的原型、原型链有什么特点？
- 每个对象都会在其内部初始化一个属性，就是prototype（原型），
- 当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的 prototype ，于是这样一直找下去，也就是我们所说的原型链的概念。
- 特点：
  - JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有属于自己的原型副本；
  - 当我们修改原型时，与之相关的对象也会继承这一改变；

4. 谈谈this对象的理解?
- this 总是指向函数的直接调用者（而非间接调用者）；
- 如果有 new 关键字，this 指向 new 出来的那个对象；
- 在事件中，this 指向触发这个事件的对象，特殊的是，IE中的 attachEvent 中的 this 总是指向全局对象 Window。

5. 什么是闭包（closure），为什么要用它？
- 闭包是指有权访问另一个函数作用域中变量的函数；
- 创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量；
- 利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
- 闭包的特性：
  - 函数内再嵌套函数；
  - 内部函数可以引用外层的参数和变量；
  - 参数和变量不会被垃圾回收机制回收；

6. 对JSON的了解？
- JSON(JavaScript Object Notation)是一种轻量级的数据交换格式；
- 它是基于JavaScript的一个子集，数据格式简单, 易于读写, 占用带宽小；

7. undefined与null之间的区别？
- undefined：表示"缺少值"，就是此处应该有一个值，但是还没有定义；
- null：表示"没有对象"，即该处不应该有值； 
- undefined的类型（typeof）是 undefined，null的类型 (typeof) 是object；
- undefined转换数值时为NaN，null转换数值时为0；
- js 将未赋值的变量默认值设为 undefined；js 从来不会将变量设为 null，它是用来表明某个用 var 声明的变量时没有值的。

8. document.write和innerHTML的区别？
- document.write 只能重绘整个页面； 
- innerHTML 可以重绘页面的一部分。

9. Javscript的事件？
- JavaScript 使我们有能力创建动态页面，事件是可以被 JavaScript 侦测到的行为；
- 网页中的每个元素都可以产生某些可以触发 JavaScript 函数的事件，比方说，我们可以在用户点击某按钮时产生一个 onClick 事件来触发某个函数，事件在 HTML 页面中定义；
- 当用户进入或离开页面时就会触发 onload 和 onUnload 事件；
- 表单里面使用的onFocus、onBlur、onChange;

10. Javascript绑定事件的方法?
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

11. 同步和异步的区别?
- 同步强调的是顺序性，谁先谁后，异步则不存在这种顺序性；
- 同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求，等请求完，页面刷新，新内容出现，用户看到新内容，进行下一步操作；
- 异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求；等请求完，页面不刷新，新内容也会出现，用户看到新内容；

12. 如何解决跨域问题？
- jsonp、iframe、window.name、window.postMessage、服务器上设置代理页面等；

13. JavaScript 异步加载的方式有哪些?
- 利用setTimout实现异步；
- 动态创建script标签；
- 利用script标签提供的async；
- 使用Promise对象。
