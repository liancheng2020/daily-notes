1. v-if 和 v-show 的区别？

- 手段：
  - v-if 是动态的向 DOM 树内添加或者删除 DOM 元素；
  - v-show 是通过设置 DOM 元素的 display 样式属性控制显隐；
- 编译过程：
  - v-if 切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件；
  - v-show 只是简单的基于 css 切换；
- 编译条件：
  - v-if 是惰性的，如果初始条件为假，则什么也不做，只有在条件第一次变为真时才开始局部编译；
  - v-show 是在任何条件下，无论首次条件是否为真，都被编译，然后被缓存，而且 DOM 元素保留；
- 性能消耗：
  - v-if 有更高的切换消耗；
  - v-show 有更高的初始渲染消耗；
- 使用场景：
  - v-if 适合运营条件不大可能改变；
  - v-show 适合频繁切换；

2. Vue 修饰符有哪些？

- 事件修饰符：
  - .stop：阻止事件继续传播；
  - .prevent：阻止标签默认行为；
  - .capture：使用事件捕获模式，即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理；
  - .self：只当在 event.target 是当前元素自身时触发处理函数；
  - .once：事件将只会触发一次；
  - .passive：告诉浏览器你不想阻止事件的默认行为；
- v-model 的修饰符：
  - .lazy：通过这个修饰符，转变为在 change 事件再同步；
  - .number：自动将用户的输入值转化为数值类型；
  - .trim：自动过滤用户输入的首尾空格；
- 键盘事件的修饰符：.enter、.tab、.delete（补获删除键和退格键）、.up、.down；

3. 对 SPA 单页面的理解，它的优缺点分别是什么？

- SPA（single-page application）仅在 Web 页面初始化时加载相应的 HTML、JavaScript 和 CSS；
- 一旦页面加载完成，SPA 不会因为用户的操作而进行页面的重新加载或跳转；
- 取而代之的是利用路由机制实现 HTML 内容的变换，UI 与用户的交互，避免页面的重新加载；
- 优点：
  - 用户体验好、快，内容的改变不需要重新加载整个页面，避免了不必要的跳转和重复渲染；
  - 基于上面一点 SPA 相对对服务器压力小；
  - 前后端职责分离，架构清晰，前端进行交互逻辑，后端负责数据处理；
- 缺点：
  - 初次加载耗时多：为实现单页 Web 应用功能及显示效果，需要在加载页面的时候将 JavaScript、CSS 统一加载，部分页面按需加载；
  - 前进后退路由管理：由于单页应用在一个页面中显示所有的内容，所以不能使用浏览器的前进后退功能，所有的页面切换需要自己建立堆栈管理；
  - SEO 难度较大：由于所有的内容都在一个页面中动态替换显示，所以在 SEO 上其有着天然的弱势；

4. 对 SSR 的理解？

- SSR 也就是服务端渲染，也就是将 Vue 在客户端把标签渲染成 HTML 的工作放在服务端完成，然后再把 html 直接返回给客户端；
- SSR 的优势：
  - 更好的 SEO；
  - 首屏加载速度更快；
- SSR 的缺点：
  - 开发条件会受到限制，服务器端渲染只支持 beforeCreate 和 created 两个钩子；
  - 当需要一些外部扩展库时需要特殊处理，服务端渲染应用程序也需要处于 Node.js 的运行环境；
  - 更多的服务端负载；

5. vue.extend 和 vue.component？

   > - extend：是构造一个组件的语法器，然后这个组件你可以作用到 Vue.component 这个全局注册方法里，还可以在任意 vue 模板里使用组件，也可以作用到 vue 实例或者某个组件中的 components 属性中并在内部使用 apple 组件；
   > - Vue.component：你可以创建，也可以取组件；

6. Vuex 有哪几种属性？

- 有五种，分别是 State、Getter、Mutation、Action、Module；
  - state => 基本数据(数据源存放地)；
  - getters => 从基本数据派生出来的数据；
  - mutations => 提交更改数据的方法，同步；
  - actions => 像一个装饰器，包裹 mutations，使之可以异步；
  - modules => 模块化 Vuex；

7. Vuex 中 action 和 mutation 的区别？

- Mutation 专注于修改 State，理论上是修改 State 的唯一途径，Action 业务代码、异步请求；
- Mutation：必须同步执行，Action：可以异步，但不能直接操作 State；
- 在视图更新时，先触发 actions，actions 再触发 mutation；
- mutation 的参数是 state，它包含 store 中的数据，store 的参数是 context，它是 state 的父级，包含 state、getters；

- 简单概述：
  - action 中处理异步，mutation 不可以；
  - mutation 作原子操作；
  - action 可以整合多个 mutation；

8. Vuex 和 localStorage 的区别？

- 最重要的区别：
  - vuex 存储在内存中；
  - localstorage 则以文件的方式存储在本地，只能存储字符串类型的数据，存储对象需要 JSON 的 stringify 和 parse 方法进行处理，读取内存比读取硬盘速度要快；
- 应用场景：
  - Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式，它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化，vuex 用于组件之间的传值；
  - localstorage 是本地存储，是将数据存储到浏览器的方法，一般是在跨页面传递数据时使用；
  - Vuex 能做到数据的响应式，localstorage 不能；
- 永久性
  - 刷新页面时 vuex 存储的值会丢失，localstorage 不会；

9. 路由的 hash 和 history 模式？

- Vue-Router 有两种模式：hash 模式和 history 模式，默认的路由模式是 hash 模式；
- hash 模式：
  - 开发中默认的模式，它的 URL 带着一个#，例如：`http://www.abc.com/#/vue，它的hash值就是#/vue`；
  - 特点：
    - hash 值会出现在 URL 里面，但是不会出现在 HTTP 请求中，对后端完全没有影响，所以改变 hash 值，不会重新加载页面；
    - 这种模式的浏览器支持度很好，低版本的 IE 浏览器也支持这种模式；
    - hash 路由被称为是前端路由，已经成为 SPA（单页面应用）的标配；
- history 模式：
  - history 模式的 URL 中没有#，它使用的是传统的路由分发模式，即用户在输入一个 URL 时，服务器会接收这个请求，并解析这个 URL，然后做出相应的逻辑处理；
  - 特点：
    - 当使用 history 模式时，URL 就像这样：`http://abc.com/user/id`，相比 hash 模式更加好看；
    - 但是 history 模式需要后台配置支持，如果后台没有正确配置，访问时会返回 404；

10. params 和 query 的区别？

- 用法：query 要用 path 来引入，params 要用 name 来引入，接收参数都是类似的，分别是`this.$route.query.name`和`this.$route.params.name`；
- url 地址显示：query 更加类似于 ajax 中 get 传参，params 则类似于 post，说的再简单一点，前者在浏览器地址栏中显示参数，后者则不显示；
- 注意：query 刷新不会丢失 query 里面的数据，params 刷新会丢失 params 里面的数据；

11. $route和$router 的区别？

- $route：是“路由信息对象”，包括 path，params，hash，query，fullPath，matched，name 等路由信息参数；
- $router：是“路由实例”对象包括了路由的跳转方法，钩子函数等；

12. created 和 mounted 的区别？

- created：在模板渲染成 html 前调用，即通常初始化某些属性值，然后再渲染成视图；
- mounted：在模板渲染成 html 后调用，通常是初始化页面完成后，再对 html 的 dom 节点进行一些需要的操作；

13. 为什么 data 是一个函数而不是对象？

- 组件中的 data 写成一个函数，数据以函数返回值形式定义，这样每复用一次组件，就会返回一份新的 data，类似于给每个组件实例创建一个私有的数据空间，让各个组件实例维护各自的数据；
- 而单纯的写成对象形式，就使得所有组件实例共用了一份 data，就会造成一个变了全都会变的结果；

14. 一般在哪个生命周期请求异步数据？

- 我们可以在钩子函数 created、beforeMount、mounted 中进行调用，因为在这三个钩子函数中，data 已经创建，可以将服务端返回的数据进行赋值；
- 推荐在 created 钩子函数中调用异步请求，因为在 created 钩子函数中调用异步请求有以下优点：
  - 能更快获取到服务端数据，减少页面加载时间，用户体验更好；
  - SSR 不支持 beforeMount、mounted 钩子函数，放在 created 中有助于一致性；

15. 对 Vue 的认识？

- vue 是一个渐进式的 JS 框架，它易用，灵活，高效；
- 可以把一个页面分隔成多个组件，当其他页面有类似功能时，直接让封装的组件进行复用；
- 他是构建用户界面的声明式框架，只关心图层；不关心具体是如何实现的；

16. MVVM 框架？

- MVVM：是 Model-View-ViewModel 的缩写；
- Model：代表数据模型，也可以在 Model 中定义数据修改和操作的业务逻辑；
- View：代表 UI 组件，它负责将数据模型转化成 UI 展现出来；
- ViewModel：监听模型数据的改变和控制视图行为、处理用户交互，简单理解就是一个同步 View 和 Model 的对象，连接 Model 和 View；

17. vue 与 react 的区别？

- react 整体是函数式的思想，把组件设计成纯组件，状态和逻辑通过参数传入，所以在 react 中，是单向数据流；
- vue 的思想是响应式的，也就是基于是数据可变的，通过对每一个属性建立 Watcher 来监听，当属性变化的时候，响应式的更新对应的虚拟 dom；
- 相同点：
  - 数据驱动页面，提供响应式的视图组件；
  - 都有 virtual DOM，组件化的开发，通过 props 参数进行父子之间组件传递数据，都实现了 webComponents 规范；
  - 数据流动单向，都支持服务器的渲染 SSR；
  - 都有支持 native 的方法，react 有 React native，vue 有 wexx；
- 不同点：
  - 数据绑定：Vue 实现了双向的数据绑定，react 数据流动是单向的；
  - 数据渲染：大规模的数据渲染，react 更快；
  - 使用场景：React 配合 Redux 架构适合大规模多人协作复杂项目，Vue 适合小快的项目；
  - 开发风格：react 推荐做法 jsx + inline style 把 html 和 css 都写在 js 了，vue 是采用 webpack + vue-loader 单文件组件格式，html，js，css 同一个文件；

18. Vue 的基本原理？

- 当一个 Vue 实例创建时，Vue 会遍历 data 中的属性，用 Object.defineProperty（vue3.0 使用 proxy）将它们转为 getter/setter，并且在内部追踪相关依赖，在属性被访问和修改时通知变化；
- 每个组件实例都有相应的 watcher 程序实例，它会在组件渲染的过程中把属性记录为依赖，之后当依赖项的 setter 被调用时，会通知 watcher 重新计算，从而致使它关联的组件得以更新；

19. Vue 的双向数据绑定原理是什么？

- Vue 的双向数据绑定是由数据劫持结合发布者-订阅者模式实现的；
- 数据劫持是通过 Object.defineProperty()来劫持对象数据的 setter 和 getter 操作，在数据变动时发布消息给订阅者，触发相应的监听回调；

- 原理：

  - 通过 Observer 来监听自己的 model 数据变化，通过 Compile 来解析编译模板指令，最终利用 Watcher 搭起 Observer 和 Compile 之间的通信桥梁，达到数据变化->视图更新；
  - 在初始化 vue 实例时，遍历 data 这个对象，给每一个键值对利用 Object.definedProperty()对 data 的键值对新增 get 和 set 方法，利用了事件监听 DOM 的机制，让视图去改变数据；

- 具体步骤：
  - 第一步：需要 observe 的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter 和 getter，这样的话给这个对象的某个值赋值，就会触发 setter，那么就能监听到了数据变化；
  - 第二步：compile 解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图；
  - 第三步：Watcher 订阅者是 Observer 和 Compile 之间通信的桥梁，主要做的事情是：
    - 在自身实例化时往属性订阅器(dep)里面添加自己；
    - 自身必须有一个 update()方法；
    - 待属性变动 dep.notice()通知时，能调用自身的 update()方法，并触发 Compile 中绑定的回调，则功成身退；
  - 第四步：MVVM 作为数据绑定的入口，整合 Observer、Compile 和 Watcher 三者，
    - 通过 Observer 来监听自己的 model 数据变化；
    - 通过 Compile 来解析编译模板指令；
    - 最终利用 Watcher 搭起 Observer 和 Compile 之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据 model 变更的双向绑定效果；

20. Vue 生命周期的理解？

- Vue 生命周期总共分为 8 个阶段，分别为创建前/后、载入前/后、更新前/后、销毁前/后；
- 创建前/后：
  - 在 beforeCreated 阶段，vue 实例的挂载元素$el 和数据对象 data 都为 undefined，还未初始化；
  - 在 created 阶段，vue 实例的数据对象 data 有了，$el 还没有；
- 载入前/后：
  - 在 beforeMount 阶段，vue 实例的$el 和 data 都初始化了，但还是挂载之前为虚拟的 dom 节点，data.message 还未替换；
  - 在 mounted 阶段，vue 实例挂载完成，data.message 成功渲染；
- 更新前/后：当 data 变化时，会触发 beforeUpdate 和 updated 方法；
- 销毁前/后：在执行 destroy 方法后，对 data 的改变不会再触发周期函数，说明此时 vue 实例已经解除了事件监听以及和 dom 的绑定，但是 dom 结构依然存在；

21. Vue 组件之间的通信？

- 父子组件间通信：
  - 子组件通过 props 属性来接受父组件的数据，通过$emit 触发事件来向父组件发送数据；
  - 通过 ref 属性给子组件设置一个名字，父组件通过$refs组件名来获得子组件，子组件通过$parent 获得父组件，这样也可以实现通信；
  - 使用 provide/inject，在父组件中通过 provide 提供变量，在子组件中通过 inject 来将变量注入到组件中，不论子组件有多深，只要调用了 inject 那么就可以注入 provide 中的数据；
- 兄弟组件间通信：
  - 使用 eventBus 的方法，它的本质是通过创建一个空的 Vue 实例来作为消息传递的对象，通信的组件引入这个实例，通信的组件通过在这个实例上监听和触发事件，来实现消息的传递；
  - 通过$parent/$refs 来获取到兄弟组件，也可以进行通信；
- 任意组件之间：
  - 使用 eventBus，其实就是创建一个事件中心，相当于中转站，可以用它来传递事件和接收事件；

22. computed 和 watch 的区别？

- computed：
  - 它支持缓存，只有依赖的数据发生了变化，才会重新计算；
  - 不支持异步，当 Computed 中有异步操作时，无法监听数据的变化；
  - 如果一个数据依赖于其他数据，那么把这个数据设计为 computed 的；
- watch：
  - 它不支持缓存，数据变化时，它就会触发相应的操作；
  - 支持异步监听，监听的函数接收两个参数，第一个参数是最新的值，第二个是变化之前的值；
  - 监听数据必须是 data 中声明的或者父组件传递过来的 props 中的数据，当发生变化时，会触发其他操作，函数有两个的参数：
    - immediate：组件加载立即触发回调函数；
    - deep：深度监听，发现数据内部的变化，在复杂数据类型中使用，例如数组中的对象发生变化，需要注意的是，deep 无法监听到数组和对象内部的变化；
  - 如果你需要在某个数据变化时做一些事情，使用 watch 来观察这个数据变化；
- 两者区别：
  - computed 主要用于对同步数据的处理；
  - watch 则主要用于观测某个值的变化去完成一段开销较大的复杂业务逻辑；
  - computed 和 watch 都起到监听/依赖一个数据，并进行处理的作用，它们其实都是 vue 对监听器的实现；

23. Vue 如何监听数组变化？

- Object.defineProperty()不能监听数组变化；
- 重新定义原型，重写 push、pop 等方法，实现监听；
- Proxy 可以原生支持监听数组变化；

24. $nextTick 原理及作用？

- Vue 的 nextTick 其本质是对 JavaScript 执行原理 EventLoop 的一种应用；
- nextTick 的核心是利用了如 Promise、MutationObserver、setImmediate、setTimeout 的原生 JavaScript 方法来模拟对应的微/宏任务的实现，本质是为了利用 JavaScript 的这些异步回调任务队列来实现 Vue 框架中自己的异步回调队列；
- nextTick 不仅是 Vue 内部的异步队列的调用方法，同时也允许开发者在实际项目中使用这个方法来满足实际应用中对 DOM 更新数据时机的后续逻辑处理；

25. 对虚拟 DOM 的理解？

- 从本质上来说，Virtual Dom 是一个 JavaScript 对象，通过对象的方式来表示 DOM 结构；
- 将页面的状态抽象为 JS 对象的形式，配合不同的渲染工具，使跨平台渲染成为可能；
- 通过事务处理机制，将多次 DOM 修改的结果一次性的更新到页面上，从而有效的减少页面渲染的次数，减少修改 DOM 的重绘重排次数，提高渲染性能；

26. 为什么虚拟 DOM 会提高性能？

- 虚拟 DOM 相当于在 js 和真实 dom 中间加了一个缓存，利用 dom diff 算法避免了没有必要的 dom 操作，从而提高性能；
- 具体实现步骤：
  - 用 JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档中；
  - 当状态变更的时候，重新构造一棵树的对象树，然后用新的树和旧的树进行对比，记录两棵树差异；
  - 把步骤 2 所记录的差异应用到步骤 1 所构建的真正的 DOM 树上，视图就更新了；

27. DIFF 算法的原理？

- 在新老虚拟 DOM 对比时：
  - 首先，对比节点本身，判断是否为同一节点，如果不为相同节点，则删除该节点重新创建节点进行替换；
  - 如果为相同节点，进行 patchVnode，判断如何对该节点的子节点进行处理，先判断一方有子节点一方没有子节点的情况(如果新的 children 没有子节点，将旧的子节点移除)；
  - 比较如果都有子节点，则进行 updateChildren，判断如何对这些新老节点的子节点进行操作（diff 核心）；
  - 匹配时，找到相同的子节点，递归比较子节点；
- 在 diff 中，只对同层的子节点进行比较，放弃跨级的节点比较，使得时间复杂从 O(n3)降低值 O(n)，也就是说，只有当新旧 children 都为多个子节点时才需要用核心的 Diff 算法进行同层级比较；

28. Vue3 有什么更新？

- 监测机制的改变：
  - vue3 将带来基于代理 Proxy 的 observer 实现，提供全语言覆盖的反应性跟踪；
  - 消除了 Vue2 当中基于 Object.defineProperty 的实现所存在的很多限制；
- 只能监测属性，不能监测对象：
  - 检测属性的添加和删除；
  - 检测数组索引和长度的变更；
  - 支持 Map、Set、WeakMap 和 WeakSet；
- 模板：
  - 作用域插槽，Vue2.x 的机制导致作用域插槽变了，父组件会重新渲染，而 Vue3 把作用域插槽改成了函数的方式，这样只会影响子组件的重新渲染，提升了渲染的性能；
  - 同时，对于 render 函数的方面，Vue3 也会进行一系列更改来方便习惯直接使用 api 来生成 vdom；
- 对象式的组件声明方式：
  - Vue2.x 中的组件是通过声明的方式传入一系列 option，和 TypeScript 的结合需要通过一些装饰器的方式来做，虽然能实现功能，但是比较麻烦；
  - Vue3 修改了组件的声明方式，改成了类式的写法，这样使得和 TypeScript 的结合变得很容易；
- 其它方面的更改：
  - 支持自定义渲染器，从而使得 weex 可以通过自定义渲染器的方式来扩展，而不是直接 fork 源码来改的方式；
  - 支持 Fragment（多个根节点）和 Protal（在 dom 其他部分渲染组建内容）组件，针对一些特殊的场景做了处理；
  - 基于 tree shaking 优化，提供了更多的内置功能；

29. Vue3 为什么要用 proxy？

- 在 Vue2 中，0bject.defineProperty()会改变原始数据，而 Proxy 是创建对象的虚拟表示，并提供 set、get 和 deleteProperty 等处理器，这些处理器可在访问或修改原始对象上的属性时进行拦截，有以下特点 ∶
  - 不需用使用 Vue.$set或Vue.$delete 触发响应式；
  - 全方位的数组变化检测，消除了 Vue2 无效的边界情况；
  - 支持 Map，Set，WeakMap 和 WeakSet；
  - Proxy 实现的响应式原理与 Vue2 的实现原理相同，实现方式大同小异：
    - get 收集依赖、Set、delete 等触发依赖；
    - 对于集合类型，就是对集合对象的方法做一层包装：原方法执行后执行依赖相关的收集或触发逻辑；

30. Vue 的性能优化？

- 代码层面的优化：
  - v-if 和 v-show 区分使用场景；
  - computed 和 watch 区分使用场景；
  - v-for 必须为 item 添加 key；
  - 长列表性能优化；
  - 事件的销毁；
  - 图片资源懒加载；
  - 路由懒加载；
  - 第三方插件的按需引入；
  - 服务端渲染 SSR 或预渲染
- webpack 层面的优化：
  - 对图片进行压缩；
  - 提取公共代码；
  - 模板预编译；
  - 提取组件的 CSS；
  - 构建结果输出分析；
- 基础优化：
  - CDN 使用；
  - 开启 gzip 压缩；
  - 浏览器缓存；
