1. HTML 与 HTML5 之间的区别?

-   在文档类型声明上：html5 只有一句简简单单的声明`<!DOCTYPE html>`；
-   在结构语义上：html5 提供了一些新的标签，如`<header>、<nav>、<footer>`等；
-   强大的 html5 新功能：canvas 标签、SVG 图像，新增视频标签 video、audio 等；

2. 对 HTML 语义化的理解？

-   语义类标签对开发者更友好，使用语义类标签增强了可读性，即便是在没有 CSS 的时候，开发者也能够清晰的看出网页的结构，便于团队的开发和维护；
-   语义类标签页十分适宜机器阅读，它的文字表现力丰富，更适合搜索引擎（SEO），也可以让搜索引擎爬虫更好地获取到更多有效信息，有效提升网页的搜索量；

3. HTML5 有哪些更新?

-   语义化标签：例如 nav、header、aside、section、article、footer 等；
-   媒体标签：audio（音频）、video（视频）；
-   数据存储：localStorage、sessionStorage；
-   canvas（画布）、Geolocation（地理定位）、websocket（通信协议）；
-   input 标签新增属性：placeholder、autocomplete、autofocus、required；
-   history API：go、forward、back、pushstate；
-   移除的元素有：
    -   纯表现的元素：basefont，big，center，font, s，strike，tt，u；
    -   对可用性产生负面影响的元素：frame，frameset，noframes；

4. 行内元素有哪些？块级元素有哪些？空(void)元素有那些？

-   行内元素：a、b、span、img、input、select、strong 等；
-   块级元素：div、ul、ol、li、dl、dt、dd、h1、h2、h3、p 等；
-   空元素：即没有内容的 HTML 元素，空元素是在开始标签中关闭的，也就是空元素没有闭合标签：
    -   常见的有：br、hr、img、input、link、meta；
    -   鲜见的有：area、base、col、colgroup、param、source、track、wbr；

5. src 与 href 的区别？

-   src 是“引入”，在 img、script、iframe 等元素上使用；
-   href 是“超文本引用”，指向需要连接的地方，是与该页面有关联的，是引用，在 link 和 a 等元素上使用；

6. div 与 span 的区别？

-   div 是一个块级元素，它包含的元素会自动换行；
-   span 是行内元素，在它的前后不会换行，span 没有结构上的意义，只是单纯的应用样式；

7. `<em>`和`<strong>`的区别？

-   `<em>`：斜体标签，强调文本内容，有顺序的；
-   `<strong>`：粗体标签，更加强调文本内容，重要性强调，随意无顺序的；

8. iframe 有那些优点和缺点？

-   iframe 元素会创建包含另外一个文档的内联框架（即行内框架）；
-   优点：
    -   用来加载速度较慢的内容（如广告）；
    -   可以使脚本可以并行下载；
    -   可以实现跨子域通信；
-   缺点：
    -   iframe 会阻塞主页面的 onload 事件；
    -   无法被一些搜索引擎索识别；
    -   会产生很多页面，不容易管理；

9. 渐进增强和优雅降级的区别？

-   渐进增强：主要针对低版本的浏览器进行页面重构，再针对高级浏览器进行效果、交互等方面的改进和追加功能；
-   优雅降级：一开始就构建完整的功能，然后再针对低代码的浏览器进行兼容；
