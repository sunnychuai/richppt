一、使用场景，主要功能，带来的收益
    - 使用场景
        描述: “Bootstrap是最流行的的 HTML, CSS和 JavaScript 响应式开发框架 ，web上开发的第一个移动项目.”
        核心概念/原则: 响应式布局、移动设备优先
        框架大小: 145 KB
        预处理器: Less 和 Sass
        响应式: Yes
        模块化: Yes
        字体图标：200个来自 Glyphicon Halflings 的字体图标
        浏览器支持： Firefox, Chrome, Safari, IE8+ (你需要 Respond.js for IE8)
二、框架优缺点，使用技术壁垒
三、框架的使用方法
四、主要的技术点调研
优点：
    - 流媒体网格布局
    - 响应式设计
    - 自定义表单元素
    - 页面排版
    - JavaScript交互性
    - 跨浏览器兼容性
缺点：
    - 

------------------------------------------------------------------
一、Bootstrap简介
Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。
特点：
1.一个框架、多种设备
    通过同一份代码快速、有效适配手机、平板、PC 设备
2.预处理脚本
    虽然可以直接使用 Bootstrap 提供的 CSS 样式表，不要忘记 Bootstrap 的源码是基于最流行的 CSS 预处理脚本 - Less 和 Sass 开发的。
    你可以采用预编译的 CSS 文件快速开发，也可以从源码定制自己需要的样式.。
3.特性齐全
    Bootstrap 提供了全面、美观的文档。
    你能在这里找到关于 HTML 元素、HTML 和 CSS 组件、jQuery 插件方面的所有详细文档。
二、下载与使用
1.直接下载
    1.用于生产环境的 Bootstrap（编译并压缩后的 CSS、JavaScript 和字体文件）
    2.Bootstrap 源码（Less、JavaScript 和 字体文件的源码，并且带有文档。需要 Less 编译器和一些设置工作。）
    3.Sass项目
3.使用 Bootstrap 中文网提供的免费 CDN 加速服务
4.通过 Bower 进行安装
三、编译 CSS 和 JavaScript 文件
使用 Grunt 作为编译系统
四、工具--Bootlint
是 Bootstrap 官方所支持的 HTML 检测工具。
在使用了 Bootstrap 的页面上（没有对 Bootstrap 做修改和扩展的情况下），它能自动检查某些常见的 HTML 错误。
纯粹的 Bootstrap 组件需要固定的 DOM 结构。Bootlint 就能检测你的页面上的这些“纯粹”的 Bootstrap 组件是否符合 Bootstrap 的 HTML 结构规则。
四、禁止响应式布局
1.移除 此 CSS 文档中提到的设置浏览器视口（viewport）的标签：<meta>。
2.通过为 .container 类设置一个 width 值从而覆盖框架的默认 width 设置，例如 width: 970px !important; 。
  请确保这些设置全部放在默认的 Bootstrap CSS 文件的后面。注意，如果你把它放到媒体查询中，也可以略去 !important 。
3.如果使用了导航条，需要移除所有导航条的折叠和展开行为。
4.对于栅格布局，额外增加 .col-xs-* 类或替换掉 .col-md-* 和 .col-lg-*。 
  不要担心，针对超小屏幕设备的栅格系统能够在所有分辨率的环境下展开。
五、浏览器和设备的支持情况
Bootstrap 的目标是在最新的桌面和移动浏览器上有最佳的表现，也就是说，在较老旧的浏览器上可能会导致某些组件表现出的样式有些不同，但是功能是完整的。
1.被支持的浏览器
//图片
2.IE 8 和 9
是被支持的，然而很多 CSS3 属性和 HTML5 元素 -- 例如，圆角矩形和投影 -- 是肯定不被支持的。
另外， IE8 需要 Respond.js 配合才能实现对媒体查询（media query）的支持。
3.IE8 与 Respond.js需注意
    1.Respond.js 与 跨域CSS 的问题
        如果 Respond.js 和 CSS 文件被放在不同的域名或子域名下面（例如，使用CDN）时需要一些额外的设置
    2.由于浏览器的安全机制，Respond.js 不能在通过 file:// 协议（打开本地HTML文件所用的协议）访问的页面上发挥正常的功能。
    3.Respond.js 不支持通过 @import 指令所引入的 CSS 文件
4.IE8 与 box-sizing 属性
    当 box-sizing: border-box; 与 min-width、max-width、min-height 或 max-height 一同使用时，IE8 不能完全支持 box-sizing 属相。
5.IE 兼容模式
    为了让 IE 浏览器运行最新的渲染模式下，建议将此 <meta> 标签加入到你的页面中：
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
6.国产浏览器高速模式
国内浏览器厂商一般都支持兼容模式（即 IE 内核）和高速模式（即 webkit 内核），
不幸的是，所有国产浏览器都是默认使用兼容模式，这就造成由于低版本 IE （IE8 及以下）内核让基于 Bootstrap 构建的网站展现效果很糟糕的情况。
幸运的是，国内浏览器厂商逐渐意识到了这一点，某些厂商已经开始有所作为了！

将下面的 <meta> 标签加入到页面中，可以让部分国产浏览器默认采用高速模式渲染页面：
<meta name="renderer" content="webkit">
目前只有360浏览器支持此 <meta> 标签。希望更多国内浏览器尽快采取行动、尽快进入高速时代！

7.Windows 8 中的 IE 10 和 Windows Phone 8
IE 10 并没有对 屏幕的宽度 和 视口（viewport）的宽度 进行区分，这就导致 Bootstrap 中的媒体查询并不能很好的发挥作用。
为了解决这个问题，你可以引入下面列出的这段 CSS 代码暂时修复此问题：@-ms-viewport{ width: device-width; }
Windows Phone 8 还需要加入以下 CSS 和 JavaScript 代码来化解此问题。
8.Safari 对百分比数字凑整的问题
OS X 上搭载的 v7.1 以前 Safari 和 iOS v8.0 上搭载的 Safari 浏览器的绘制引擎对于处理 .col-*-1 类所对应的很长的百分比小数存在 bug。
也就是说，如果你在一行（row）之中定义了12个单独的列（.col-*-1），你就会看到这一行比其他行要短一些。
除了升级 Safari/iOS 外，有以下几种方式来应对此问题：
    为最后一列添加 .pull-right 类，将其暴力向右对齐
    手动调整百分比数字，让其针对Safari表现更好（这比第一种方式更困难）
六、对第三方组件的支持
虽然我们并不官方支持任何第三方插件，我们还是提供一些建议，帮你避免可能在你的项目中会出现的问题。
1.box-sizing 属性
由于 * { box-sizing: border-box; } 的设置而产生冲突，这一设置使 padding 不影响页面元素最终宽度的计算。

七、从 v2.x 版本升级到 v3.x 版本
Bootstrap 3 版本并不向后兼容 v2.x 版本。

在 Bootstrap 2 中，我们对框架中的某些关键部分增加了对移动设备友好的样式。
而在 Bootstrap 3 中，我们重写了整个框架，使其一开始就是对移动设备友好的。
这次不是简单的增加一些可选的针对移动设备的样式，而是直接融合进了框架的内核中。
也就是说，Bootstrap 是移动设备优先的。针对移动设备的样式融合进了框架的每个角落，而不是增加一个额外的文件。

1.主要 class 的变更
2.新增的内容
3.删除的内容

八、栅格系统
1.工作原理
    1.“行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100% 宽度）中
    2.通过“行（row）”在水平方向创建一组“列（column）”
    3.你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素
    4.通过为“列（column）”设置 padding 属性，从而创建列与列之间的间隔（gutter）。
      通过为 .row 元素设置负值 margin 从而抵消掉为 .container 元素设置的 padding，
      也就间接为“行（row）”所包含的“列（column）”抵消掉了padding
    5.如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
2.媒体查询
    /* 超小屏幕（手机，小于 768px） */
    /* 没有任何媒体查询相关的代码，因为这在 Bootstrap 中是默认的（还记得 Bootstrap 是移动设备优先的吗？） */

    /* 小屏幕（平板，大于等于 768px） */
    @media (min-width: @screen-sm-min) { ... }

    /* 中等屏幕（桌面显示器，大于等于 992px） */
    @media (min-width: @screen-md-min) { ... }

    /* 大屏幕（大桌面显示器，大于等于 1200px） */
    @media (min-width: @screen-lg-min) { ... }
九、JS插件
1.建议使用压缩版的 JavaScript 文件
2.不要在同一个元素上同时使用多个插件的 data 属性
3.某些插件和 CSS 组件依赖于其它插件。如果你是单个引入每个插件的，请确保在文档中检查插件之间的依赖关系。
  注意，所有插件都依赖 jQuery （也就是说，jQuery必须在所有插件之前引入页面）。 

第三方工具库
Bootstrap 官方不提供对第三方 JavaScript 工具库的支持，例如 Prototype 或 jQuery UI。
除了 .noConflict 和为事件名称添加命名空间，还可能会有兼容性方面的问题，这就需要你自己来处理了。

1.过渡效果 transition.js
    Transition.js 是针对 transitionEnd 事件的一个基本辅助工具，也是对 CSS 过渡效果的模拟。
    它被其它插件用来检测当前浏览器对是否支持 CSS 的过渡效果。
2.模态框 modal.js
    - 不支持模态框重叠
    - 务必将模态框的 HTML 代码放在文档的最高层级内（也就是说，尽量作为 body 标签的直接子元素），以避免其他组件影响模态框的展现和/或功能。
    - 增强模态框的可访问性 务必为 .modal 添加 role="dialog" 属性，aria-labelledby="myModalLabel" 属性用于只想模态框的标题栏，aria-hidden="true" 用于通知辅助性工具略过模态框的 DOM元素。
3.下拉菜单
4.滚动监听
5.标签页 
6.工具提示 












