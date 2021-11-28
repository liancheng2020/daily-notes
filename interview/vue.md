1. Vue生命周期的理解？
- Vue生命周期总共分为8个阶段，分别为创建前/后、载入前/后、更新前/后、销毁前/后；
- 创建前/后：
  - 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化；
  - 在created阶段，vue实例的数据对象data有了，$el还没有；
- 载入前/后：
  - 在beforeMount阶段，vue 实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换；
  - 在mounted阶段，vue实例挂载完成，data.message成功渲染；
- 更新前/后：当data变化时，会触发beforeUpdate和updated方法；
- 销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在；

2. Vue组件之间的数据通信？
- 父组件向子组件传递数据：通过prop数据传递；
- 子组件向父组件传递数据：通过$on和$emit数据传递；
- 兄弟组件之间传递数据：通过$emit自定义事件来解决；

3. Vue的双向数据绑定原理是什么？
- Vue.js是采用数据劫持结合发布者-订阅者模式的方式，通过 Object.defineProperty()来劫持各个属性的setter、getter，在数据变动时发布消息给订阅者，触发相应的监听回调；
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

4. 对Vuex的认识？
- vuex可以理解为一种开发模式或框架，比如PHP有thinkphp，java有spring等；
- 通过状态（数据源）集中管理驱动组件的变化（好比spring的IOC容器对bean进行集中管理）；
- 应用级的状态集中放在store中； 改变状态的方式是提交mutations，这是个同步的事物； 异步逻辑应该封装在action中；
