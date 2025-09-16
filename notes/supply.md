1. 微信小程序生命周期

- 应用生命周期：全局初始化、错误监控、后台状态管理（onLaunch、onShow、onHide）；
- 页面生命周期：页面数据加载、DOM 操作、资源清理（onLoad、onShow、onReady、onUnload）；
- 页面附加函数：交互逻辑，如下拉刷新、分享、滚动监听等（onPullDownRefresh、onShareAppMessage）；

2. Promise 方法

- Promise.all()：全部成功时返回结果数组，任意一个失败则立即失败；
- Promise.race()：返回第一个完成（成功或失败）的 Promise 的结果；

3. watch 和 watchEffect 区别

- watch：
  - 需要精确控制监听的数据源；
  - 需要对比旧值和新值；
  - 监听深层对象或数组（配合 deep: true）；
- watchEffect：
  - 依赖自动追踪，适合执行副作用逻辑；
  - 不需要旧值，只需响应数据变化；

4. v-model 自定义组件实现

- vue2：
  - <CustomInput v-model="message" />
  - <CustomInput :value="message" @input="message = $event" />
- vue3：
  - <CustomInput v-model="message" />
  - <CustomInput :modelValue="message" @update:modelValue="message = $event"/>

5. ref 和 reactive 区别

- ref：
  - 支持基本类型和对象，返回 { value: ... } 对象；
  - 可以直接替换整个对象；
  - 适用于简单数据、需要明确控制响应式的情况；
- reactive：
  - 仅支持对象或数组，返回响应式代理对象；
  - 不能直接替换整个对象（需用 Object.assign 或解构）；
  - 适用于复杂对象、嵌套数据；

6. webpack 打包原理

- 初始化：读取配置，初始化编译器和插件；
- 构建依赖图：从入口文件开始，递归解析依赖，生成模块依赖图；
- 分块：根据规则将模块分组为 Chunk（如入口文件、动态导入、公共依赖）；
- 生成资源：调用 Loader 和插件处理模块，生成优化后的资源（如 JS、CSS）；
- 输出文件：将资源写入磁盘，触发插件钩子（如 emit）；

7. vue3 为什么要有 hooks

- 逻辑聚合：相关代码集中，提高可读性；
- 逻辑复用：通过自定义 Hooks 实现高效复用；
- 更好的 TS 支持：函数式编程风格更贴合 TypeScript；
- 更灵活的架构：适合大型项目，便于团队协作和维护；

8. vue3 原理？

- 响应式系统：基于 Proxy 实现，自动追踪依赖，变化自动更新 UI；
- Composition API：更灵活的逻辑组织方式，方便复用和维护；
- 性能优化：静态提升、Tree-shaking、Diff 算法优化，整体性能提升；
- 跨平台能力：通用渲染架构，支持多种目标平台；
- 异步和 Suspense 支持：简化异步加载和懒加载，改善用户体验；
- 设计现代化：支持 TypeScript，编译优化，结合现代 JavaScript 特性；

9. vue3 响应式原理？

- 核心思想：通过拦截对象的访问和变更，自动追踪依赖（数据与界面之间的关系），并在数据变化时通知相关的视图进行更新；

- 代理创建：通过 Proxy 将对象变成响应式对象；
- 依赖收集：在 get 时，记录这个地方依赖了哪些响应式数据；
- 数据变更：在 set 时，通知依赖执行相应的更新操作；
- 自动更新：依赖的响应式效果（如 DOM 更新、computed 等）自动触发；

10. vue3 生命周期？

- onBeforeMount()：组件挂载之前；
- onMounted()：组件挂载完成（DOM 已渲染到页面）；
- onBeforeUpdate()：组件更新之前；
- onUpdated()：组件更新完成；
- onBeforeUnmount()：组件卸载之前；
- onUnmounted()：组件已卸载（销毁）；
- onActivated()：keep-alive 组件激活时（缓存组件）；
- onDeactivated()：keep-alive 组件失活时（缓存组件）；

11. 低代码平台，组件按需加载？

- 将组件的配置信息（如组件名称、路径）存储在后台，运行时根据配置动态加载对应的组件；
- 通过 import() 方法动态加载组件，并使用 Suspense 组件进行加载等待处理；
