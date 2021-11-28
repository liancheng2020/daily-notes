1. CSS3的新特性?
- 新增各种CSS选择器；
- 圆角border-radiuis；
- 多列布局：multi-column layout；
- 阴影和反射：multi-column layout；
- 文字特效：text-shadow；
- 线性渐变：gradient；
- 旋转：transform；
- 缩放、定位、倾斜、动画，多背景；

2. CSS如何实现水平垂直居中？
- div绝对定位水平垂直居中；
- 利用flex布局实现；
- 使用 tranfrom 做相对位移的调节；

3. position定位问题？
- absolute：生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位；
- fixed：生成绝对定位的元素，相对于浏览器窗口进行定位；
- relative：生成相对定位的元素，相对于其正常位置进行定位；
- static：默认值，没有定位，元素出现在正常的流中；

4. display: none和visibility: hidden的区别？
- display: none：隐藏对应的元素，在文档布局中不再给它分配空间，它各边的元素会合拢，就当它从来不存在；
- visibility: hidden：隐藏对应的元素，但是在文档布局中仍保留原来的空间。

5. 行内元素有哪些？块级元素有哪些？空元素有哪些？
- 行内元素：span img input select strong...；
- 块级元素：div ul ol dl dt dd h1 h2 h3 h4 p...；
- 空元素：br hr img input link meta  base area command embed keygen param source track wbr...；

6. 行内元素（内联元素）和块级元素的区别？
- 行内元素（inline）特性：
  - 行内元素和其它行内元素都会在一条线上排列，都是在同一行；
  - 宽度、高度、内边距、外边距都不可改变，宽度高度随文本内容的变化而变化；
- 块级元素（block）特性：
  - 块级元素总是在新的一行开始排列，各个块级元素独占一行；
  - 宽度、高度、内边距、外边距都可控制；
- 行内元素和块级元素可以相互转换，块级元素包括行内元素和块级元素；

7. 如何清除浮动？
- 浮动可以理解为让某个div元素脱离标准流，漂浮在标准流之上，和标准流不是一个层次；
- 父级div定义 overflow: hidden；
- 父级div定义 伪类: after；
- 浮动元素末尾添加额外标签 clear: both；
