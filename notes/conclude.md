1. call/apply/bind

-   都是用来改变相关函数 this 指向的；
-   call/apply 是直接进行相关函数调用;
-   bind 不会执行相关函数，而是返回一个新的函数，新函数已经自动绑定新的 this 指向；

2. 构造函数和 this

-   如果构造函数中显式返回一个值，且返回的是一个对象，那么 this 就指向这个返回的对象；
-   如果返回的不是一个对象，那么 this 仍然指向实例；

3. this 优先级

-   通过 call、apply、bind、new 对 this 绑定的情况称为显式绑定；
-   根据调用关系确定的 this 指向称为隐式绑定；

4. img 标签

-   alt 属性：替换文本，图片显示失败时显示；
-   title 属性：提示文本，鼠标放到图片上，显示的提示文字；

5. html 新特性

-   新增语义化标签；
-   新增媒体标签；
-   新增 input 类型；
-   新增表单属性；

6. script 标签：调整加载顺序提升渲染速度

-   async 属性：立即请求文件，但不阻塞渲染引擎，而是文件加载完毕后阻塞渲染引擎并立即执行文件内容；
-   defer 属性：立即请求文件，但不阻塞渲染引擎，等到解析完 HTML 之后再执行文件内容；
-   HTML5 标准 type 属性：对应值为“module”，让浏览器按照 ECMA Script 6 标准将文件当作模块进行解析，默认阻塞效果同 defer，也可以配合 async 在请求完成后立即执行；

7. vite

-   利用浏览器现在已经支持 es6 的 import，碰见 import 会发送一个 http 请求去加载文件；
-   vite 拦截这些请求，做一些预编译，省去了 webpack 冗长的打包时间，提升开发体验；

8. vue3 性能优势

-   vue2 初始化，所有的数据都要递归走 defineProperty 包；
-   vue3 用 proxy+动态的决定返回什么，做了拦截，初始工作量减少，组件实例化的提升还是很明显；

9. vue3 composition 的来源和细节

-   为了解决 option api 的 this 黑盒问题，引入了 composition api
-   为了解决 reactivity 操作简单数据结构的命名空间问题，引入新的 api ref
-   为了解决 composition 的统一 return 问题，引入了 script setup
-   为了解决 ref 的.value 副作用，引入了 ref sugar
