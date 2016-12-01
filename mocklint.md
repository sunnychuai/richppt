title: mocklint
speaker: jingjing.chuai
url: https://github.com/sunnychuai/mocklint
transition: slide3
files: /style/richppt.css
theme: moon

[slide]
# mocklint实现及使用
## 检查JSON文件和JS文件
## [<i class="fa fa-github"></i>mocklint](https://github.com/sunnychuai/mocklint)

[slide data-transition="vertical3d"]
# 怎么检查JSON文件？

[slide]
## JSON基本结构: 
----
* 名称/值”对的集合，即对象 {:&.rollIn}
* 值的有序列表，即数组

[slide]
## JavaScript针对JSON有两个全局方法:
----
* JSON.parse(text[, reviver]) {:&.rollIn}
* JSON.stringify(value[, replacer[, space]]) 
<br/>
<br/>
` 
可以利用JSON.parse()方法来检查JSON文件的格式 
`

[slide]
# 怎么检查JS文件？
----
abort.js{:&.flexbox.vleft}
<pre><code class="markdown">
module.exports = {
    "companyName":"廊坊市美林进出口贸易有限公司",
    "loanLimit":500000.00,
    "loanEndtime":1462069941843,
    "functionCode" : "103",//
    "userName":"李帅",
    "roleId":2, //角色id
    "relationId":1,
    tools: {
        dateFormat: function (format, datetime) {
            return '2016-05-05';
        },
        moneyFormat: function(money){
            return '1230000.00';
        }
    }
};
</code>
</pre>

[slide]
## module.exports
----
* 是nodejs中[Modules](https://nodejs.org/api/modules.html)里的语法 {:&.rollIn}
* 对于module.exports的解释是：
> If you want the root of your module's export to be a function (such as a constructor) or if you want to export a complete object in one assignment instead of building it one property at a time, assign it to module.exports instead of exports.

* 大概意思是：
> 如果你希望你的模块导出的根是一个函数（如构造函数）或者你希望在一个赋值中导出一个完整的对象，而不是一次一个地构建一个属性，那么就用module.exports代替exports。

* 可以利用nodejs模块加载的方法require()来检查JS文件

[slide]
<br/>
<pre><code class="javascript">var colors = require('colors');
var JSON5 = require('json5');
var glob = require('glob');
var path = require('path');
var fs = require('fs');

var isError; 
function start() {
    var cwd = path.resolve(__dirname, '../../');
    process.argv.slice(2).forEach(function(pattern) {
        glob.sync(pattern, {
            cwd: cwd,
            ignore: ['node_modules/**/*', 'build/**/*', 'build.js']
        }).forEach(function (filename) {
            var content = fs.readFileSync(path.join(cwd, filename), 'utf-8');
            try {
                filename.endsWith('.json') ? JSON5.parse(content) : require(path.join(cwd, filename));
            } catch (err) {
                handleError(filename, err);
            }
        });
    });
    isError && process.exit(1);
}
function handleError(filename, err) {
    console.error(colors.yellow.underline(filename) + '\n' + colors.red(err.message) + '\n');
    isError = true;
}
start();
</code>
</pre>

[slide]
- 安装 `npm install`
- 使用 <br/>
`node node_modules/mocklint/index.js <file ...>`
- 栗子 <br/>
`node node_modules/mocklint/index.js '*.js' '**/*.json'`
    
[slide]
## NPM介绍
----
* NPM (node package manager)，通常称为 node 包管理器。 {:&.rollIn}
* 主要功能：管理node包<br/>
    包括：安装、卸载、更新、查看、搜索、发布

[slide]
## 包文件
- package.json {:&.rollIn}
- README (and its variants)
- CHANGELOG (and its variants)
- LICENSE / LICENCE

[slide]
## package.json

- name：package的名字 {:&.rollIn}
- version：package的版本<br/>
    当package发生变化时，version也应该跟着一起变化
- description：package的描述
- keywords：package的关键字,方便别人搜索到本模块
- homepage：项目主页url
- bugs：bug提交地址或者邮箱
- license：模块协议
- main：指定了程序的主入口文件
- repository：仓库,代码存放地址
- scripts：指定了项目的生命周期个各个环节需要执行的命令。<br/>
    键是事件名，值是在该点上运行的命令
- config：用来设置项目中不怎么变化的项目配置

[slide]
## package.json
- dependencies：应用依赖模块<br/> {:&.rollIn}
    要使用这个package，至少需要安装哪些，应用依赖模块会安装到当前模块的node_modules目录下
- devDependencies：开发依赖模块<br/>
    如果有人想要下载并使用你的模块，并不希望或需要下载一些你在开发过程中使用的额外的测试或者文档框架
- peerDependencies：同伴依赖 <br/>
    如果要使用此插件模块，请确保安装了兼容版本的宿主模块。<br/>
    为了说明此模块只能作为插件跑在宿主的某个版本范围下

[slide]
# NPM包安装
- 本地安装：<br/> {:&.rollIn}
    package会被下载到当前所在目录，也只能在当前目录下使用。
- 全局安装：<br/>
    package会被下载到到特定的系统目录下，安装的package能够在所有目录下使用。

[slide]
## 安装命令

- 本地安装 `npm install grunt-cli` {:&.rollIn}
- 全局安装 `npm install -g gulp-cli`
- 按版本安装 `npm install grunt-cli@"0.1.9"`
- 通过 package.json 安装<br/>
如果我们的项目依赖了很多package，一个一个地安装那将是个体力活。我们可以将项目依赖的包都在package.json这个文件里声明，然后一行命令搞定 npm install
- 其他命令<br/>
运行 `npm install --help`会列出所有 npm install 可能的参数形式

[slide]
## 卸载

- 本地卸载 `npm uninstall grunt-cli` {:&.rollIn}
- 全局卸载 `npm uninstall -g grunt-cli`
- 按版本卸载 `npm uninstall grunt-cli@"0.1.9"`

[slide]
## 查看

- 查看当前目录安装了哪些package `npm ls` {:&.rollIn}
- 查看package的全局安装信息，加上 `-g` 就可以
- 查看特定package的信息 `npm ls pkg`
- 查看更详细信息，可以通过 `npm info pkg `，输出的信息非常详尽，包括作者、版本、依赖等。

[slide]

- 更新 `npm update grunt-cli` {:&.rollIn}

- 搜索 `npm search grunt-cli`

- 发布 <br/>
    `npm publish <tarball>`<br/>
    `npm publish <folder>`

[slide]
# 配置
----
npm的配置工作主要是通过 `npm config` 命令，主要包含增、删、改、查几个步骤，下面就以最为常用的proxy配置为例。

[slide]
## 配置命令
----

- 设置 `npm config set proxy url`<br/> {:&.rollIn}
    可简写：`npm set proxy url`

- 查看 `npm config get proxy`<br/>
    可简写：`npm get proxy`

- 删除 `npm delete proxy`

- 查看所有配置 `npm config list`

- 修改配置文件 `npm config edit`





