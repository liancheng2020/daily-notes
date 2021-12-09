1. 对vue的认识？
- vue是一个渐进式的JS框架，它易用，灵活，高效； 
- 可以把一个页面分隔成多个组件，当其他页面有类似功能时，直接让封装的组件进行复用；
- 他是构建用户界面的声明式框架，只关心图层；不关心具体是如何实现的；

2. Vue生命周期的理解？
- Vue生命周期总共分为8个阶段，分别为创建前/后、载入前/后、更新前/后、销毁前/后；
- 创建前/后：
  - 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化；
  - 在created阶段，vue实例的数据对象data有了，$el还没有；
- 载入前/后：
  - 在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换；
  - 在mounted阶段，vue实例挂载完成，data.message成功渲染；
- 更新前/后：当data变化时，会触发beforeUpdate和updated方法；
- 销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在；

3. vue与react的区别？
- react整体是函数式的思想，把组件设计成纯组件，状态和逻辑通过参数传入，所以在react中，是单向数据流；
- vue的思想是响应式的，也就是基于是数据可变的，通过对每一个属性建立Watcher来监听，当属性变化的时候，响应式的更新对应的虚拟dom；
- 相同点：
  - 数据驱动页面，提供响应式的视图组件；
  - 都有virtual DOM,组件化的开发，通过props参数进行父子之间组件传递数据，都实现了webComponents规范；
  - 数据流动单向，都支持服务器的渲染SSR；
  - 都有支持native的方法，react有React native，vue有wexx；
- 不同点：
  - 数据绑定：Vue实现了双向的数据绑定，react数据流动是单向的；
  - 数据渲染：大规模的数据渲染，react更快；
  - 使用场景：React配合Redux架构适合大规模多人协作复杂项目，Vue适合小快的项目；
  - 开发风格：react推荐做法jsx + inline style把html和css都写在js了，vue是采用webpack + vue-loader单文件组件格式，html, js, css同一个文件；

4. MVVM框架？
- MVVM：是Model-View-ViewModel的缩写；
- Model：代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑；
- View：代表UI组件，它负责将数据模型转化成UI展现出来；
- ViewModel：监听模型数据的改变和控制视图行为、处理用户交互，简单理解就是一个同步View和Model的对象，连接Model和View；

5. Vue的双向数据绑定原理是什么？
- Vue的双向数据绑定是由数据劫持结合发布者-订阅者模式实现的；
- 数据劫持是通过Object.defineProperty()来劫持对象数据的setter和getter操作，在数据变动时发布消息给订阅者，触发相应的监听回调；
- 原理：
  - 通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化->视图更新；
  - 在初始化vue实例时，遍历data这个对象，给每一个键值对利用Object.definedProperty对data的键值对新增get和set方法，利用了事件监听DOM的机制，让视图去改变数据；

- 具体步骤：
  - 第一步：需要observe的数据对象进行递归遍历，包括子属性对象的属性，都加上setter和getter，这样的话给这个对象的某个值赋值，就会触发setter，那么就能监听到了数据变化；
  - 第二步：compile解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图；
  - 第三步：Watcher订阅者是Observer和Compile之间通信的桥梁，主要做的事情是：
    - 在自身实例化时往属性订阅器(dep)里面添加自己；
    - 自身必须有一个update()方法；
    - 待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退；
  - 第四步：MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，
    - 通过Observer来监听自己的model数据变化；
    - 通过Compile来解析编译模板指令；
    - 最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果；

6. Vue组件之间的通信？
- 父组件向子组件传值：父组件通过props向子组件传递数据；
- 子组件向父组件传值：子组件通过$emit触发事件，回调给父组件；
- 兄弟组件之间的通信：可以通过$emit自定义事件来解决；

7. v-if和v-show的区别？
- 手段：
  - v-if是动态的向DOM树内添加或者删除DOM元素；
  - v-show是通过设置DOM元素的display样式属性控制显隐；
- 编译过程：
  - v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件；
  - v-show只是简单的基于css切换；
- 编译条件：
  - v-if是惰性的，如果初始条件为假，则什么也不做，只有在条件第一次变为真时才开始局部编译；
  - v-show是在任何条件下，无论首次条件是否为真，都被编译，然后被缓存，而且DOM元素保留；
- 性能消耗：
  - v-if有更高的切换消耗；
  - v-show有更高的初始渲染消耗；
- 使用场景：
  - v-if适合运营条件不大可能改变；
  - v-show适合频繁切换；

8. Vue修饰符有哪些？
- 事件修饰符：
  - .stop：阻止事件继续传播；
  - .prevent：阻止标签默认行为；
  - .capture：使用事件捕获模式,即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理；
  - .self：只当在 event.target 是当前元素自身时触发处理函数；
  - .once：事件将只会触发一次；
  - .passive：告诉浏览器你不想阻止事件的默认行为；
- v-model的修饰符：
  - .lazy：通过这个修饰符，转变为在change事件再同步；
  - .number：自动将用户的输入值转化为数值类型；
  - .trim：自动过滤用户输入的首尾空格；
- 键盘事件的修饰符：.enter、.tab、.delete（补获删除键和退格键）、.up、.down；

9. computed和watch的区别？
- 如果一个数据依赖于其他数据，那么把这个数据设计为computed的；
- 如果你需要在某个数据变化时做一些事情，使用watch来观察这个数据变化；
- 两者区别：
  - computed主要用于对同步数据的处理；
  - watch则主要用于观测某个值的变化去完成一段开销较大的复杂业务逻辑；
  - computed和watch都起到监听/依赖一个数据，并进行处理的作用，它们其实都是vue对监听器的实现；

10. vue.extend和vue.component？
> - extend：是构造一个组件的语法器，然后这个组件你可以作用到Vue.component这个全局注册方法里，还可以在任意vue模板里使用组件，也可以作用到vue实例或者某个组件中的components属性中并在内部使用apple组件；
> - Vue.component：你可以创建，也可以取组件；

11. $nextTick原理及作用？
- Vue的nextTick其本质是对JavaScript执行原理EventLoop的一种应用；
- nextTick的核心是利用了如Promise、MutationObserver、setImmediate、setTimeout的原生JavaScript方法来模拟对应的微/宏任务的实现，本质是为了利用JavaScript的这些异步回调任务队列来实现Vue框架中自己的异步回调队列；
- nextTick不仅是Vue内部的异步队列的调用方法，同时也允许开发者在实际项目中使用这个方法来满足实际应用中对DOM更新数据时机的后续逻辑处理；

12. 为什么虚拟DOM会提高性能？
- 虚拟DOM相当于在js和真实dom中间加了一个缓存，利用dom diff算法避免了没有必要的dom操作，从而提高性能；
- 具体实现步骤：
  - 用JavaScript对象结构表示DOM树的结构；然后用这个树构建一个真正的DOM树，插到文档中；
  - 当状态变更的时候，重新构造一棵树的对象树，然后用新的树和旧的树进行对比，记录两棵树差异；
  - 把步骤2所记录的差异应用到步骤1所构建的真正的DOM树上，视图就更新了；

13. Vue3有什么更新？
- 监测机制的改变：
  - vue3将带来基于代理Proxy的observer实现，提供全语言覆盖的反应性跟踪；
  - 消除了Vue2当中基于Object.defineProperty的实现所存在的很多限制；
- 只能监测属性，不能监测对象：
  - 检测属性的添加和删除；
  - 检测数组索引和长度的变更；
  - 支持Map、Set、WeakMap和WeakSet；
- 模板：
  - 作用域插槽，Vue2.x的机制导致作用域插槽变了，父组件会重新渲染，而Vue3把作用域插槽改成了函数的方式，这样只会影响子组件的重新渲染，提升了渲染的性能；
   -同时，对于render函数的方面，Vue3也会进行一系列更改来方便习惯直接使用api来生成vdom；
- 对象式的组件声明方式：
  - Vue2.x中的组件是通过声明的方式传入一系列option，和TypeScript的结合需要通过一些装饰器的方式来做，虽然能实现功能，但是比较麻烦；
  - Vue3修改了组件的声明方式，改成了类式的写法，这样使得和TypeScript的结合变得很容易；
- 其它方面的更改：
  - 支持自定义渲染器，从而使得weex可以通过自定义渲染器的方式来扩展，而不是直接fork源码来改的方式；
  - 支持Fragment（多个根节点）和Protal（在dom其他部分渲染组建内容）组件，针对一些特殊的场景做了处理；
  - 基于tree shaking优化，提供了更多的内置功能；
