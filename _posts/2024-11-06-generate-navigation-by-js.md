---
layout: post-custom
title:  "利用outline.js生成文章导读目录"
---

本文介绍如何利用js脚本为文章页面生成导读目录（解析h1~h6标题）。

---
## 引入outline.js

这里我用到的是`outline.js`，自动生成文章导读（Table of Contents）导航的 JavaScript 工具。

GitHub有该项目仓库，地址：<a href="https://github.com/yaohaixiao/outline.js">https://github.com/yaohaixiao/outline.js</a>

首先要引入`outline.js`，可以使用CDN引入或者下载源码作本地引入。

### CDN

```html
<link href="https://cdn.jsdelivr.net/gh/yaohaixiao/outline.js/outline.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/gh/yaohaixiao/outline.js/outline.min.js"></script>
```

### 本地引入

在GitHub上访问`outline.js`项目的**Release**页面有下载选项，Release地址：
<a href="https://github.com/yaohaixiao/outline.js/releases">https://github.com/yaohaixiao/outline.js/releases</a>

可以选择不同的版本下载。我下载的是`outline.js-3.40.1`。解压缩后得到的源码文件里我用到了以下的几个文件：
- outline.min.css
- outline.min.js

---
##  使用方法

### 步骤1：代码引入outline.js和其样式
在你的文章页面比如demo.html中引入outline.js和其样式。

css样式可以直接在`<head>`标签引入，但js可能要在`<body>`标签内引入，因为js需要DOM元素。

若是本地引入，请注意将文件放到你的文章页面所在目录下。若是不同目录，请注意路径问题。

示例代码如下:

```html
<!-- demo.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- cdn引入outline.js的css样式 -->
    <link href="https://cdn.jsdelivr.net/gh/yaohaixiao/outline.js/outline.min.css" rel="stylesheet" />


    <title>练习使用outline.js</title>
</head>
<body>
    <!-- cdn引入outline.min.js -->
    <script src="https://cdn.jsdelivr.net/gh/yaohaixiao/outline.js/outline.min.js"></script>
    <script>
        (function(){
            const defaults = Outline.DEFAULTS
            let outline

            // position 的值为 sticky 或者 fixed 时需要指定parentElement
            defaults.position = 'relative'
            // parentElement 参数，即文章导航菜单插入的 DOM 位置
            // 可以时 dom 元素，也可以是 DOM 元素的选择器字符串
            // defaults.parentElement = '#aside'

            // 指定要解析的文章区域
            defaults.articleElement = '#article'
            // 要收集的标题
            defaults.selector = 'h1,h2,h3,h4,h5,h6'
            // 使导读栏布局在窗口右侧
            defaults.placement = 'rtl'
            defaults.stickyHeight = 86
            // 点击空白处（非独立导航菜单），收起导航菜单
            defaults.closeOnClickModal = false
            // 有独立导航菜单时，是否默认显示菜单 
            defaults.showNavModalFirst = true
            defaults.homepage = '#'
            outline = new Outline(defaults)
            outline.reload()
        })()
    </script>
</body>
</html>
```


上述代码的解释在后面在叙述。

我使用的是`position='relative'`，创建独立的侧滑菜单，这在手机端也能够很好的工作。其它布局模式我在使用时导致手机浏览效果不佳，而它的flex布局方式我没有实现出来，读者可以自己尝试和调整。

到这里，我们还没有完成任务，接下来还需要给出文章区域。

### 步骤2：创建文章区域
在上一步中，我们会发现`articleElement='#my-article'`，这其实是表示要让outline.js解析html文件中的id为"my-article"的区域，用来生成目录结构。

但demo.html目前还没有文章区域的内容。接下来我们在`<body>`标签中使用`<div>`标签，并设置id为"my-article"，或者使用html5的新特性，使用`<article>`标签代替`<div>`，并指定id属性为"my-article"。

完整代码如下：

```html
<!-- demo.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- cdn引入outline.js的css样式 -->
    <link href="https://cdn.jsdelivr.net/gh/yaohaixiao/outline.js/outline.min.css" rel="stylesheet" />


    <title>练习使用outline.js</title>
</head>
<body>
    <!-- 头部区域 -->
    <header>
        <h1>文章笔记</h1>
    </header>
    <!-- 页面主区域 -->
    <main>
        <!-- 文章区域，设置id作为唯一标识 -->
        <!-- 等同于<div id="my-article"></div> -->
        <article id="my-article">
            <h1>练习使用outline.js</h1>
            <p>
                outline.js是一个轻量级的js库，用于为页面中的元素添加outline样式。
            </p>
            <h2>引入方法</h2>
            <p>内容</p>
            <h2>使用方法</h2>
            <p>内容</p>
        </article>
    </main>

    <!-- cdn引入outline.min.js -->
    <script src="outline.min.js"></script>
    <!-- 初始化outline.js参数生成目录 -->
    <script>
        (function(){
            const defaults = Outline.DEFAULTS
            let outline

            // position 的值为 sticky 或者 fixed 时需要指定parentElement
            defaults.position = 'relative'
            // parentElement 参数，即文章导航菜单插入的 DOM 位置
            // 可以时 dom 元素，也可以是 DOM 元素的选择器字符串
            // defaults.parentElement = '#aside'

            // 指定文章区域用来解析
            defaults.articleElement = '#my-article'
            // 要收集的标题
            defaults.selector = 'h1,h2,h3,h4,h5,h6'
            // 使导读栏布局在窗口右侧
            defaults.placement = 'rtl'
            defaults.stickyHeight = 86
            // 点击空白处（非独立导航菜单），收起导航菜单
            defaults.closeOnClickModal = false
            // 有独立导航菜单时，是否默认显示菜单 
            defaults.showNavModalFirst = true
            defaults.homepage = '#'
            outline = new Outline(defaults)
            outline.reload()
        })()
    </script>
</body>
</html>
```

现在，使用浏览器打开demo.html文件即可看到效果。

<img src="/notes/assets/pictures/demo-outlinejs.png" alt="demo-outlinejs">

---
## API文档

完整API文档地址：<a href="https://yaohaixiao.github.io/outline.js/">https://yaohaixiao.github.io/outline.js/</a>

这里我介绍下上面代码用到的参数。

### Outline.DEFAULTS

DEFAULTS是outline的默认配置，如果无法正常引入outline.js，浏览器控制台会提示找不到对象。

Outline.DEFAULTS 默认配置如下：

```javascript
const outline = new Outline({
    // 文章显示区域的 DOM 元素或者选择器字符串
    articleElement: '#article',
    // 要收集的标题选择器
    selector: 'h2,h3,h4,h5,h6',
    // 指定文章导读导航菜单的标题文字。
    // 设置空字符串或者 false，则不显示标题
    // 在插入导航菜单的 DOM 元素已有标题时，可以设置 title: '' 或者 false
    title: '目录',
    // 负责文章区域滚动的元素
    // String 类型 - 选择器字符串，默认值：html,body（window窗口）
    // HTMLElement 类型 - DOM 元素
    scrollElement: 'html,body',
    // 文章导读菜单的位置
    // relative - （默认值）创建独立的侧滑菜单
    // sticky - 导航菜单将以 sticky 模式布局（需要确保菜单插入位置支持 sticky 模式布局）
    // fixed - 导航菜单将以 fixed 模式布局，会自动监听滚动位置，模拟 sticky 布局
    // sticky 和 fixed 布局时，需要设置 parentElement
    // 2.0.0 暂时不支持之前版本那种 inside 模式，不会自动在文章开始位置插入 navigator 导航菜单
    position: 'sticky',
    // 导航菜单将要插入的位置（DOM 元素）
    // String 类型 - 选择器字符串
    // HTMLElement 类型 - 插入的 DOM 元素
    // 仅在 position 设置为 sticky 和 fixed 布局时有效
    parentElement: '#aside',
    // 设置 position: relative 时，placment 定义侧滑菜单和 toolbar 导航位置：
    // rtl - 菜单位置在窗口右侧，滑动动画为：right to left
    // ltr - 菜单位置在窗口左侧，滑动动画为：left to right
    // ttb - 菜单位置在窗口上方，滑动动画为：top to bottom
    // btt - 菜单位置在窗口下方，滑动动画为：bottom to top
    placement: 'rtl',
    // 页面中其它 sticky 或者模拟 skicky 的 fiexed 定位的 DOM 元素的高度。例如 wordpress 系统中，
    // 就会有 sticky 定位的导航菜单。这些 sticky 元素脱离了正常的流布局后，原来 h1~h6 标题标签的 
    // offsetTop 计算会出现偏差。sticky 元素会遮挡标题，因此针对页面中有其它 sticky 元素会遮挡标题，
    // 因此针对 sticky 布局时，需要设置 stickyHeight 高度。outline.js 会根据 stickyHeight 和计
    // 算出的标题的 offsetTop 值重新计算滚动定位；
    // 说明：outline.js 主要用于文章详情页面，
    // 因此 stickyHeight 仅针对 top: 0，且 sticky 定位元素在文章内容区域上方的位置；
    stickyHeight: 0,
    // 是否显示标题编号
    showCode: true,
    // 指定是否采用动画定位高亮当前的章节标题，默认值：true
    // 当值为 false 时，则采用高亮当前章节标题的链接文字并加粗文字
    // 如果喜欢更简洁的高亮效果，可以选择设置为 false
    animationCurrent: true,
    // 是否显示侧边的按钮工具栏
    hasToolbar: true,
    // 点击空白处（非独立导航菜单），收起导航菜单
    closeOnClickModal: true,
    // 有独立导航菜单时，是否默认显示菜单 
    showNavModalFirst: false,
    // 标题图标链接的 URL 地址
    // （默认）没有设置定制，点击链接页面滚动到标题位置
    // 设置了链接地址，则不会滚动定位
    anchorURL: '',
    // 指定当前站点主页地址
    homepage: '',
    // 指定git仓库地址
    git: '',
    // 指定git仓库中的 tags 地址
    tags: '',
    // 指定git仓库中的 issues 地址
    issues: '',
    // 自定义按钮配置
    tools: [],
    // 为文章页添加基础的打印样式
    // 如果您的页面已经有打印样式，就无需设置了
    // 原名：print
    reader: {
      //（必须）要打印的文章区域，DOM 元素或者选择器字符串。
      target: '', // 原名：element
      // （可选）要打印的文章标题。如果 element 区域有 h1 标签则无需设置。
      // 可以直接设置标题文本，也可以是文章页的主标题 DOM 元素
      title: '',
      // 进入阅读模式的提示消息文本
      enterReadingTip: '进入阅读模式，按 ESC 键可退出阅读模式',
      // 是否允许启用 Web Speech API 阅读文章
      allowSpeak: false
    },
    // DIYer的福利
    // 独立侧滑菜单时，customClass 会追加到 drawer 侧滑窗口组件
    // 在文章中显示导航菜单时，customClass 会追加到 navigator 导航菜单
    customClass,
    // position: fixed，当导航菜单样式进入 fixed 定位后，触发的回调函数
    afterSticky: null,
    // 当导航菜单隐藏或者显示后，触发的回调函数
    afterToggle: null,
    // 当点击上下滚动按钮，导航菜单或者文章中的 # 图标，滚动结束后触发的回调函数
    afterScroll: null,
    // 文档的标题文本过滤回调函数
    // API 文档中，正文的方法会添加参数等信息，例如：getChapters(headings, showCode, chapterTextFilter)
    // 而在 navigator 导航菜单，我希望显示为 getChapters()，这时我们就可以借助 chapterTextFilter 回调函数
    // 对原始的文本进行过滤，返回我们期望的 getChapters() 文本
    chapterTextFilter: null,
    // 锚点链接的生成回调函数
    // anchorLinkFilter(tag, title, id)
    // tag - 当前标题的 tagName 小写：h1~6
    // title - 当前标题的文本内容
    // id - outline 为当前标题生成的 id 号，是个数值
    // 如果设置了 anchorURL，则会统一使用 anchorURL 参数的地址
    anchorLinkFilter: null
});
```

可以在创建导航后，重置配置信息，重新生成新的导航。

```javascript
Outline.reload({
  // 调整位直接在文章内生成导航
  position: 'sticky',
  articleElement: '#article'
})
```

### Options

#### articleElement
文章元素，指定要解析的文章区域。

*type*: `String|HtmlElement`  
*default*: `'#article'`

赋值说明：
- String: 假设赋值`'#article'`，即查找html文件所有标签中`id="article"`的标签区域作为解析区域。
- HtmlElement: 假设赋值`article`，即解析html文件的`<article>`元素包含的区域。

#### selector
标题选择器，指定要解析文章区域的哪几个h元素。

*type*: `String`  
*default*: `'h1,h2,h3,h4,h5,h6'`

#### position
用来指定文章导读导航菜单的显示位置。

*type*: `String`  
*default*: `'relative'`

`position`的有以下几个取值：
- `relative`：（默认值）创建独立的侧滑菜单。
- `sticky`: 导航菜单将以 sticky 模式布局，需要确保菜单插入位置(DOM 节点)支持 sticky 模式布局。
- `fixed`： 导航菜单将模拟 sticky 布局，起初是普通定位，会自动监听滚动位置，但滚动到导航菜单顶部时，以 fixed 模式布局，模拟 sticky 布局效果。

当`position`为`sticky`或`fixed`时， 需要设置 parentElement。

#### parentElement
导航菜单将要插入的位置（DOM 元素）。仅在`position`为`sticky`或`fixed`时有效。

*type*: `String|HTMLElement`  
*default*: `'#aside'`

#### placement
定义侧滑菜单和 toolbar 导航位置。

*type*: `String`  
*default*: `'rtl'`

它有如下几个取值：
- rtl - 菜单位置在窗口右侧，滑动动画为：right to left（默认值）。
- ltr - 菜单位置在窗口左侧，滑动动画为：left to right；
- ttb - 菜单位置在窗口上方，滑动动画为：top to bottom；
- btt - 菜单位置在窗口下方，滑动动画为：bottom to top；
  
#### showCode
是否显示段落章节编号。

*type*: `Boolean`
*default*: `true`

这个配置是将文章中的各标题按顺序赋值，下级标题再以`.`号命名，为`true`会将h1标题定位1级，然后按顺序划分h2的二级标题为1.2，1.3，...，在显示上会有点眼花缭乱。

而我实验后发现默认值好像是`false`，此时若标题中已经有`1.标题1`,`2.标题2`这样的内容时，生成的目录中还自动会将数字删掉。