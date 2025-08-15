1. 微信小程序生命周期

- 应用生命周期：全局初始化、错误监控、后台状态管理（onLaunch、onShow、onHide）；
- 页面生命周期：页面数据加载、DOM 操作、资源清理（onLoad、onShow、onReady、onUnload）；
- 页面附加函数：交互逻辑，如下拉刷新、分享、滚动监听等（onPullDownRefresh、onShareAppMessage）；

2. webpack 打包原理

- 初始化：读取配置，初始化编译器和插件；
- 构建依赖图：从入口文件开始，递归解析依赖，生成模块依赖图；
- 分块：根据规则将模块分组为 Chunk（如入口文件、动态导入、公共依赖）；
- 生成资源：调用 Loader 和插件处理模块，生成优化后的资源（如 JS、CSS）；
- 输出文件：将资源写入磁盘，触发插件钩子（如 emit）；

3. Promise 方法

- Promise.all()：全部成功时返回结果数组，任意一个失败则立即失败；
- Promise.race()：返回第一个完成（成功或失败）的 Promise 的结果；

4. watch 和 watchEffect 区别

- watch：
  - 需要精确控制监听的数据源；
  - 需要对比旧值和新值；
  - 监听深层对象或数组（配合 deep: true）；
- watchEffect：
  - 依赖自动追踪，适合执行副作用逻辑；
  - 不需要旧值，只需响应数据变化；

5. v-model 自定义组件实现

- vue2：
  - <CustomInput v-model="message" />
  - <CustomInput :value="message" @input="message = $event" />
- vue3：
  - <CustomInput v-model="message" />
  - <CustomInput :modelValue="message" @update:modelValue="message = $event"/>

6. ref 和 reactive 区别

- ref：
  - 支持基本类型和对象，返回 { value: ... } 对象；
  - 可以直接替换整个对象；
  - 适用于简单数据、需要明确控制响应式的情况；
- reactive：
  - 仅支持对象或数组，返回响应式代理对象；
  - 不能直接替换整个对象（需用 Object.assign 或解构）；
  - 适用于复杂对象、嵌套数据；

7. vue3 为什么要有 hooks

- 逻辑聚合：相关代码集中，提高可读性；
- 逻辑复用：通过自定义 Hooks 实现高效复用；
- 更好的 TS 支持：函数式编程风格更贴合 TypeScript；
- 更灵活的架构：适合大型项目，便于团队协作和维护；
