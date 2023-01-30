1. CSS 选择器优先级？

-   内联样式 》id 选择器 》类选择器、伪类选择器 》标签选择器、伪元素选择器；
-   !important 声明的样式的优先级最高；

2. 伪类、伪元素？

-   伪类是通过在元素选择器上加入伪类改变元素状态；
-   伪元素是通过对元素的操作进行对元素的改变；
-   冒号（:）用于伪类，双冒号（::）用于伪元素；

```
  // 伪类
  a:hover { color: #ffffff }
  p:first-child { color: red }

  // 伪元素
  p::before { content: '一 ' }
  p::first-line { background: red }
```

3. CSS 如何实现水平垂直居中？

-   div 绝对定位水平垂直居中；
-   利用 flex 布局实现；
-   使用 transform 做相对位移的调节；

4. CSS3 的新特性?

-   新增各种 CSS 选择器；
-   圆角：border-radius；
-   多列布局：multi-column layout；
-   阴影和反射：shadow reflect；
-   文字特效：text-shadow；
-   线性渐变：gradient；
-   旋转：transform；
-   缩放、定位、倾斜、动画，多背景；

5. css 盒模型？

-   标准盒子模型：width 和 height 指的是 content 的宽度和高度；
-   IE 盒子模型：width 和 height 指的是 content + padding + border 的宽度和高度；
-   在不设置 box-sizing 的情况下，box-sizing 默认是标准盒子模型（content-box）；

```
  box-sizing: content-box; // 标准盒子
  box-sizing: border-box;  // IE盒子
```

6. link 和@import 的区别？

-   两者都是外部引用 CSS 的方式，它们的区别如下：
    -   link 是 XHTML 标签，除了加载 CSS 外，还可以定义 RSS 等其他事务，@import 则属于 CSS 范畴，只能加载 CSS；
    -   link 引用 CSS 时，在页面载入时同时加载，而@import 需要页面网页完全载入以后加载；
    -   link 是 XHTML 标签，无兼容问题，@import 是在 CSS2.1 提出的，低版本的浏览器不支持；
    -   link 支持使用 Javascript 控制 DOM 去改变样式，而@import 不支持；

7. position 定位问题？

-   absolute：生成绝对定位的元素，相对于值不为 static 的第一个父元素进行定位；
-   fixed：生成绝对定位的元素，相对于浏览器窗口进行定位；
-   relative：生成相对定位的元素，相对于其正常位置进行定位；
-   static：默认值，没有定位，元素出现在正常的流中；

8. display: none 和 visibility: hidden 的区别？

-   display: none：隐藏对应的元素，在文档布局中不再给它分配空间，就当它从来不存在；
-   visibility: hidden：隐藏对应的元素，但是在文档布局中仍保留原来的空间；

9. 行内元素有哪些？块级元素有哪些？空元素有哪些？

-   行内元素：span img input select strong...；
-   块级元素：div ul ol dl dt dd h1 h2 h3 h4 p...；
-   空元素：br hr img input link meta base area command embed keygen param source track wbr...；

10. 行内元素（内联元素）和块级元素的区别？

-   行内元素（inline）特性：
    -   行内元素和其它行内元素都会在一条线上排列，都是在同一行；
    -   宽度、高度、内边距、外边距都不可改变，宽度高度随文本内容的变化而变化；
-   块级元素（block）特性：
    -   块级元素总是在新的一行开始排列，各个块级元素独占一行；
    -   宽度、高度、内边距、外边距都可控制；
-   行内元素和块级元素可以相互转换，块级元素包括行内元素和块级元素；

11. CSS 预处理器 scss、less，为什么使用它们？

-   结构清晰，便于扩展；
-   可以很方便屏蔽浏览器私有语法之间的差异；
-   可以轻松实现多重继承；
-   完美的兼容了 CSS 代码，可以应用到老项目中；

12. em 和 rem 的区别？

-   em 是相对于其父元素来设置字体大小；
-   rem 是相对于根元素来设置字体大小；

13. BFC 块级格式上下文？

-   触发 BFC 的条件：
    -   浮动元素(float 除了 node 以外的值)；
    -   定位元素(position: absolute/fixed)；
    -   display(值为 inline-block/table-cell/table-caption/flex/inline-flex)；
    -   overflow(值为 hidden/auto/srcoll)设置有这些属性的 box，都会产生 BFC；
-   BFC 特性：
    -   内部的盒子在垂直方向上一个接一个地放置；
    -   垂直方向上地距离由 margin 决定，在同一个 BFC 的 box 中，相邻的两个 box 边距会重叠；
    -   BFC 的区域不会与 float box 重叠；
    -   计算 BFC 的高度时，浮动元素也参与计算；
    -   BFC 就是一个独立的容器，里面的子元素不受外面的元素影响；
-   BFC 的作用：
    -   解决 margin 重叠问题（添加独立 BFC）；
    -   解决浮动高度塌陷问题（在父元素添加 overflow：hidden）；

14. 单行、多行文本溢出隐藏？

-   单行文本溢出：

```
  white-space: nowrap;         // 规定段落中的文本不换行
  text-overflow: ellipsis;     // 溢出用省略号显示
  overflow: hidden;            // 溢出隐藏
```

-   多行文本溢出：

```
  overflow: hidden;             // 溢出隐藏
  text-overflow: ellipsis;      // 溢出用省略号显示
  display: -webkit-box;         // 作为弹性伸缩盒子模型显示。
  -webkit-box-orient: vertical; // 设置伸缩盒子的子元素排列方式：从上到下垂直排列
  -webkit-line-clamp: 3;        // 显示的行数
```

15. css 实现一个三角形？

```
  width: 0;
  height: 0;
  border-bottom: 50px solid red;
  border-right: 50px solid transparent;
  border-left: 50px solid transparent;
```
