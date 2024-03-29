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
-   call、apply 的显式绑定一般来说优先级更高；
-   new 绑定的优先级比显式 bind 绑定更高；

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

-   vue2 中全部属性都挂载在 this 之上，而 this 可以说是一个黑盒，没有办法预先知道 this 上有什么数据
-   为了解决 option api 的 this 黑盒问题，引入了 composition api
-   为了解决 reactivity 操作简单数据结构的命名空间问题，引入新的 api ref
-   为了解决 composition 的统一 return 问题，引入了 script setup
-   为了解决 ref 的.value 副作用，引入了 ref sugar

10. vue3 新特性

-   Composition API 组合语法：更好的代码组织方式
-   新的组件：Fragment、Teleport、Suspense
-   全新的响应式系统：基于 Proxy，可以独立使用
-   自定义渲染器：方便开发跨端应用
-   全部模块使用 TypeScript 重构：更好的可维护性
-   工程化工具 Vite：更丝滑的开发体验，通用的工程化工具
-   RFC 工作机制：所有人都可以参与新特性讨论

11. vue3 响应式系统

-   reactive：基于 Proxy 实现真正的拦截，兼容不了 IE11
-   ref：利用对象的 get 和 set 属性进行监听，只拦截了 value 属性
-   ref 也可以包裹复杂的数据结构，内部会直接调用 reactive 实现

12. vite

-   webpack 启动服务器之前需要进行项目的打包，而 vite 可以直接启用服务
-   vite 通过浏览器运行时的请求拦截，实现首页文件的按需加载
-   vite 使用了 esbuild 去解析 javascript 文件

13. webpack

-   Loaders：支持其他文件类型并把他们转换成有效的模块

    -   babel-loader：转换 ES6、ES7 等新特性语法
    -   css-loader：支持.css 文件等加载和解析
    -   less-loader：将 less 文件转换为 css 文件
    -   ts-loader：将 TS 转换为 JS
    -   file-loader：进行图片、字体等的打包
    -   raw-loader：将文件以字符串的形式导入
    -   thread-loader：多进程打包 JS 和 CSS

-   Plugin：用于 bundle 文件的优化，资源管理和环境变量注入，作用于整个构建过程

    -   CommonsChunkPlugin：将 chunks 相同的模块代码提取成公共 js
    -   CleanWebpackPlugin：清理构建目录
    -   ExtractTextWebpackPlugin：将 CSS 从 bundle 文件里提取成一个独立的 CSS 文件
    -   CopyWebpackPlugin：将文件或文件夹拷贝到构建的输出目录
    -   HtmlWebpackPlugin：创建 html 文件去承载输出的 bundle
    -   UglifyjsWebpackPlugin：压缩 js
    -   ZipWebpackPlugin：将打包出的资源生成一个 zip 包

14. SSR

    -   服务端渲染 (SSR) 的核⼼是减少请求；
    -   SSR 的优势：减少白屏时间，对于 SEO 友好；

15. reactive() 的局限性

    -   仅对对象类型有效（对象、数组和 Map、Set 这样的集合类型），而对 string、number 和 boolean 这样的 原始类型 无效；
    -   因为 Vue 的响应式系统是通过属性访问进行追踪的，因此我们必须始终保持对该响应式对象的相同引用；

16. vue2 Mixin 缺点

-   不清晰的数据来源：当使用了多个 mixin 时，实例上的数据属性来自哪个 mixin 变得不清晰，这使追溯实现和理解组件行为变得困难；
-   命名空间冲突：多个来自不同作者的 mixin 可能会注册相同的属性名，造成命名冲突；
-   隐式的跨 mixin 交流：多个 mixin 需要依赖共享的属性名来进行相互作用，这使得它们隐性地耦合在一起；

17. vue3 生命周期钩子：

-   onMounted()：在组件挂载完成后执行；
-   onUpdated()：在组件因为响应式状态变更而更新其 DOM 树之后调用；
-   onUnmounted()：组件实例被卸载之后调用；
-   onBeforeMount()：在组件被挂载之前被调用；
-   onBeforeUpdate()：在组件即将因为响应式状态变更而更新其 DOM 树之前调用；
-   onBeforeUnmount()：在组件实例被卸载之前调用；

18. html5 新增功能：

-   新增语义化标签：nav、header、footer、aside、section、article；
-   音频、视频标签：audio、video；
-   数据存储：localStorage、sessionStorage；
-   canvas（画布）、Geolocation（地理定位）、websocket（通信协议）；
-   input 标签新增属性：placeholder、autocomplete、autofocus、required；
-   history API：go、forward、back、pushstate；

19. BFC

-   BFC 是一个独立的布局环境，可以理解为一个容器，在这个容器中按照一定规则进行物品摆放，并且不会影响其它环境中的物品。如果一个元素符合触发 BFC 的条件，则 BFC 中的元素布局不受外部影响

20. data 更新 view

-   实现一个监听器 observer，用来劫持并监听所有属性，如果有变动的，就通知订阅者；
-   实现一个订阅者 watcher，可以收到属性变化通知并执行相应的函数，从而更新视图；
-   实现一个解析器 compile，可以扫描和解析每个节点的相关指令，并根据初始化模板数据以及初始化相应的订阅器；
