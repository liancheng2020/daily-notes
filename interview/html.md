1. HTML与HTML5之间的区别?
- 在文档类型声明上：
  - 在文档声明上，html有很长的一段代码，并且很难记住这段代码，基本上很多都是靠工具直接生成的；
  - 而html5却是不同，只有简简单单的一个声明（<!DOCTYPE html>），方便我们记忆、使用；
- 在结构语义上：
  - 在html中并没有体现结构语义化的标签，我们通常都是以```<div class="header"></div>```来命名网站的头部；
  - 相反，html5在语义上却有很大的优势，提供了一些新的html标签，如```<header>、<nav>、<section>、<footer>、<article>、<aside>```；

2. HTML5的新功能？
- Canvas标签和SVG画图：
  - 在html5中，主要通过Canvas标签和SVG来画图，画出相应的图片和动画，但在html中却不行；
  - Canvas标签通过JavaScript来绘制2D图形，Canvas是逐像素进行渲染的；
  - 在Canvas中，一旦图形被绘制完成，它就不会继续得到浏览器的关注，如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象；
  - SVG是一种使用XML描述2D图形的语言，SVG基于XML，这意味着SVG DOM中的每个元素都是可用的，您可以为某个元素附加JavaScript事件处理器；
  - 在SVG中，每个被绘制的图形均被视为对象，如果SVG对象的属性发生变化，那么浏览器能够自动重现图形；
- Video和Audio标签支持：
  - 在html中，我们想要插入一段视频，可能还需要引用一小段的代码，
  - 但是在html5的情况下，我们只需要用于一个Video标签即可；
  - Audio标签和Video标签支持视频或音乐插入到网页中；

3. 对HTML语义化的理解？
- 语义类标签对开发者更友好，使用语义类标签增强了可读性，即便是在没有CSS的时候，开发者也能够清晰的看出网页的结构，便于团队的开发和维护；
- 语义类标签页十分适宜机器阅读，它的文字表现力丰富，更适合搜索引擎（SEO），也可以让搜索引擎爬虫更好地获取到更多有效信息，有效提升网页的搜索量；

4. cookies、sessionStorage和localStorage的区别？
- cookie：
  - cookie是网站为了标识用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）；
  - cookie数据始终在同源的http请求中携带（即使不需要），即会在浏览器和服务器间来回传递；
  - sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存；
- 存储大小：
  - cookie数据大小不能超过4k；
  - sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大；
- 有期时间：
  - cookie：设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭；
  - localStorage：存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
  - sessionStorage：数据在当前浏览器窗口关闭后自动删除。
- 作用域不同：
  - localStorage和cookie在所有同源窗口中都是共享的；
  - sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；
  - Web Storage支持事件通知机制，可以将数据更新的通知发送给监听者；
  - Web Storage的api接口使用更方便；

4. XHTML的介绍与特性?
- XHTML指扩展超文本标签语言，XHTML 的目标是取代 HTML，与HTML4.01版本几乎是相同的，是更严格更纯净的HTML版本，XHTML是作为一种 XML应用被重新定义的HTML；
- 主要特性如下：
  - XHTML元素必须被正确地嵌套；
  - XHTML 元素必须被关闭；
  - 标签名必须用小写字母；
  - XHTML 文档必须拥有根元素；

5. src与href的区别？
- src是“引入”，在img、script、iframe等元素上使用；
- href是“超文本引用”，指向需要连接的地方，是与该页面有关联的，是引用，在link和a等元素上使用；

6. div与span的区别？
- div是一个块级元素，它包含的元素会自动换行；
- span是行内元素，在它的前后不会换行，span没有结构上的意义，只是单纯的应用样式；

7. ```<em>```和```<strong>```的区别？
- ```<em>```：斜体标签，强调文本内容，有顺序的；
- ```<strong>```：粗体标签，更加强调文本内容，重要性强调，随意无顺序的；