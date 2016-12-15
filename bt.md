title: Bootstrap 预研
speaker: jingjing.chuai
transition: slide3
files: /style/bootstrap.css
theme: moon

[slide]
# Bootstrap 简介
- 描述：Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。
- 核心概念/原则: 响应式布局、移动设备优先
- 预处理器: Less 和 Sass
- 响应式: Yes
- 模块化: Yes
- 字体图标：200个来自 Glyphicon Halflings 的字体图标
- 浏览器支持：Firefox, Chrome, Safari, IE8+ (需要 Respond.js for IE8)

[slide data-transition="vertical3d"]
# 特点
- 一个框架、多种设备
    <pre>
    通过同一份代码快速、有效适配手机、平板、PC 设备
    </pre>
- 预处理脚本
    <pre>
    虽然可以直接使用 Bootstrap 提供的 CSS 样式表， 
    因为 Bootstrap 的源码是基于最流行的 CSS 预处理脚本 - Less 和 Sass 开发的。
    所以可以采用预编译的 CSS 文件快速开发，也可以从源码定制自己需要的样式.。
    </pre>
- 特性齐全
    <pre>
    Bootstrap 提供了全面、美观的文档。
    你能在这里找到关于 HTML 元素、HTML 和 CSS 组件、jQuery 插件方面的所有详细文档。
    </pre>

[slide]
# 框架的使用方法 
- 直接下载
    - 用于生产环境的 Bootstrap
        <pre>编译并压缩后的 CSS、JavaScript 和字体文件</pre>
        ```
        bootstrap/
        ├── css/
        │   ├── bootstrap.css
        │   ├── bootstrap.min.css
        │   ├── bootstrap-theme.css
        │   └── bootstrap-theme.min.css
        ├── js/
        │   ├── bootstrap.js
        │   └── bootstrap.min.js
        └── fonts/
            ├── glyphicons-halflings-regular.eot
            ├── glyphicons-halflings-regular.svg
            ├── glyphicons-halflings-regular.ttf
            └── glyphicons-halflings-regular.woff
        ```
[slide]
# 框架的使用方法
- 直接下载
    - Bootstrap 源码
    <pre>Less、JavaScript 和 字体文件的源码，并且带有文档。需要 Less 编译器和一些设置工作。</pre>
    ```
    bootstrap/
    ├── less/
    ├── js/
    ├── fonts/
    ├── dist/
    │   ├── css/
    │   ├── js/
    │   └── fonts/
    └── docs/
        └── examples/
    ```
[slide]
# 框架的使用方法
- 直接下载  
    - Sass项目
        <pre>
        这是 Bootstrap 从 Less 到 Sass 的源码移植项目
        用于快速地在 Rails、Compass 或 只针对 Sass 的项目中引入
        </pre>

[slide]
# 框架的使用方法
- 使用 Bootstrap 中文网提供的免费 CDN 加速服务
- 通过 Bower 进行安装

[slide]
# 框架优缺点
- 优点
    - 流媒体网格布局
    - 响应式设计
    - 自定义表单元素
    - 页面排版
    - JavaScript交互性
    - 跨浏览器兼容性

[slide]
# 框架优缺点
- 缺点


[slide]
# 技术壁垒
## 禁止响应式布局
    - 移除此 CSS 文档中提到的设置浏览器视口（viewport）的标签：<meta>。
    - 通过为 .container 类设置一个 width 值从而覆盖框架的默认 width 设置，例如 width: 970px !important; 。
      请确保这些设置全部放在默认的 Bootstrap CSS 文件的后面。注意，如果你把它放到媒体查询中，也可以略去 !important 。
    - 如果使用了导航条，需要移除所有导航条的折叠和展开行为。
    - 对于栅格布局，额外增加 .col-xs-* 类或替换掉 .col-md-* 和 .col-lg-*。 
      不要担心，针对超小屏幕设备的栅格系统能够在所有分辨率的环境下展开。

[slide]
# 技术壁垒
- 浏览器和设备的支持情况
    - Bootstrap的目标是在最新的桌面和移动浏览器上有最佳的表现
    - 也就是说，在较老旧的浏览器上可能会导致某些组件表现出的样式有些不同，但是功能是完整的。
- 被支持的浏览器
![被支持的浏览器](/images/bt/support.png)

[slide]
# 技术壁垒
## IE浏览器存在的问题及解决办法
- IE 8 和 9
<pre>
是被支持的，然而很多 CSS3 属性和 HTML5 元素 -- 例如，圆角矩形和投影，是肯定不被支持的。
另外， IE8 需要 Respond.js 配合才能实现对媒体查询（media query）的支持。
</pre>
- IE8 与 Respond.js需注意
<pre>
1.Respond.js 与 跨域CSS 的问题
    如果 Respond.js 和 CSS 文件被放在不同的域名或子域名下面（例如，使用CDN）时需要一些额外的设置
2.由于浏览器的安全机制，Respond.js不能在 通过 file:// 协议（打开本地HTML文件所用的协议）访问的页面上发挥正常的功能。
3.Respond.js 不支持通过 @import 指令所引入的 CSS 文件
</pre>
- IE8 与 box-sizing 属性
<pre>
当 box-sizing: border-box; 与 min-width、max-width、min-height 或 max-height 一同使用时
IE8 不能完全支持 box-sizing 属相。
</pre>
- IE 兼容模式
<pre>
为了让 IE 浏览器运行最新的渲染模式下，建议将此 <meta> 标签加入到你的页面中：
<meta http-equiv="X-UA-Compatible" content="IE=edge">
</pre>

[slide]
# 技术壁垒
## 国产浏览器高速模式
-------------------
1. 国内浏览器厂商一般都支持兼容模式（即 IE 内核）和高速模式（即 webkit 内核），
2. 不幸的是，所有国产浏览器都是默认使用兼容模式，这就造成由于低版本 IE （IE8 及以下）内核让基于 Bootstrap 构建的网站展现效果很糟糕的情况。
3. 幸运的是，国内浏览器厂商逐渐意识到了这一点，某些厂商已经开始有所作为了！

- 解决办法：
    将下面的 <meta> 标签加入到页面中，可以让部分国产浏览器默认采用高速模式渲染页面：
    <meta name="renderer" content="webkit">
- 目前只有360浏览器支持此 <meta> 标签。


[slide]
# 对第三方组件的支持
-------------
官方支持任何第三方插件


[slide]
# 从 v2.x 版本升级到 v3.x 版本

Bootstrap 3 版本并不向后兼容 v2.x 版本。
在 Bootstrap 3 中，我们重写了整个框架，使其一开始就是对移动设备友好的。
这次不是简单的增加一些可选的针对移动设备的样式，而是直接融合进了框架的内核中。

[slide]
# 从 v2.x 版本升级到 v3.x 版本
- 扁平化设计 配色清新明快
- 栅格系统层数变化 
    在Bootstrap3中的栅格层数已经达到了四层，分别为.col-xs（手机设备）、.col-sm（平板设备）、.col-md（桌面设备）、.col-lg（宽屏设备）
- 移动优先
    Bootstrap2从整体理念上来说，主要还是针对桌面浏览器
    Bootstrap3移动设备优先
- 浏览器兼容性<br/>
    ![浏览器兼容性](http://www.yeahzan.com/ui/img/article/bs3/5.png)

[slide]
# 从 v2.x 版本升级到 v3.x 版本
- 更小的文件体积
    
    在Bootstrap2中由于bootstrap.min.css与bootstrap-responsive.min文件是分开的，所以两个min文件大小为106kb+17kb=123kb。

    而Bootstrap3中将两者整合到了一起，单独一个bootstrap.min.css的文件是67KB，缩减了50%之多。
- 启用CDN
    在Bootstrap3中启用了CDN（内容分发网络），从而保证了即使在不同区域访问网站，也能够更为快速地加载Bootstrap3的CSS与JS文件。
- 添加新的组件
    在Bootstrap3中新增了List Group组件以及Panels组件，这两个组件的加入大大丰富了列表型布局的多样性。
- 对于旧组件的完善

