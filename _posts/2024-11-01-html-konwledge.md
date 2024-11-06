# HTML知识

本文记录html的一些知识，作为备忘录，以免时间长了又不知道怎么理解了。

本文目录：
- [HTML知识](#html知识)
  - [html5基础结构](#html5基础结构)
  - [html5引入了新的元素替代div元素](#html5引入了新的元素替代div元素)
    - [header元素](#header元素)
    - [nav元素](#nav元素)
    - [main元素](#main元素)
    - [section元素](#section元素)
    - [Aside元素](#aside元素)
    - [Article元素](#article元素)
    - [Blockquote元素](#blockquote元素)
    - [Footer元素](#footer元素)


## html5基础结构

在vscode编辑器打开html文件，在空白处输入：
-  `!` 
-  `html: 5` 

均会出现代码提示，选择提示按回车均会一键生成html5基础结构的代码内容：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

`<!DOCTYPE html>` 表示该文档的类型为html。

`<meta charset="UTF-8">` 设置字符集为`UTF-8`，确保网页能正确显示各种语言字符。

`<title>` 设置网页的标题。

`lang`属性用于设置当前页面的语言类型。

常用语言代码：
- 英语: `lang="en"`
- 简体中文： `lang="zh-CN"`
- 繁体中文： `lang="zh-TW"`
- 法语： `lang="fr"`
- 德语 `lang="de"`

它的主要作用是：
1. ‌提高可访问性‌。  
   对于使用屏幕阅读器等辅助技术的用户，lang属性可以帮助这些工具正确地发音和理解网页内容，从而提高内容的可访问。
2. 搜索引擎优化（SEO, Search Engine Optimization）。  
   搜索引擎可以根据lang属性确定网页的主要语言，从而更好地索引和排名网页，有助于吸引更多的目标受众‌。
3. 翻译工具。  
   在线翻译工具和浏览器内置的翻译功能可以根据lang属性识别内容的语言，提供更准确的翻译‌

## html5引入了新的元素替代div元素

HTML 的早期阶段进行往往也构建，最终搞成 div 汤 并不奇怪。需要一个内容块在你的主页？ div 啊！构建一个侧边栏？ Div 啊！三栏布局？还是div啊。

根据 **W3C** 的说法：

>`div` 元素没有任何特殊意义。
>强烈建议使用者将 div 元素视为没有其他合适的元素的最后的选择。使用更合适的元素而不是 div 元素，可以为读者提供更好的可访问性，也为使用者增加可维护性。

当 2014 年 HTML5 发布时，它引入了一些新的部分和分组元素，web 开发人员可以使用这些元素来增强代码的语义性。

### header元素
`<header>` 元素用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。

`header`用在 HTML 文档的`body`标签中。这点与包含页面标题、元信息的`head`标签不同。

### nav元素

`nav` 元素表示文档的导航部分。`nav` 应该包含给定页面、应用等主要导航链接。

### main元素
`main` 元素向浏览器和屏幕阅读器展示页面的主要内容的区域。一个页面只可以使用一个 `main`。

### section元素
`section` 元素用于按主题对内容进行分组，并表示文档或应用程序的一部分。`section` 可以有自己的 `header`、`footer` 元素，并且一个也页面可以有多个 `section` 元素。

### Aside元素
`aside` 通常用作侧边栏。用于表示包含与给定部分相关内容的页面的一部分。

### Article元素
`article` 元素可用于内容的独立部分。博客文章、报纸文章和用户评论这些用例都可以使用 `article` 元素。

### Blockquote元素

在HTML中，可以使用 `<blockquote>` 标签来定义一个块引用。 元素内容引用自外部源 （譬如个人，文件，新闻，案例研究等），并将其显示为一个独立的块级元素。

```html
<main>
   <article></article>
   
   <blockquote>
      <p>好雨知时节</p>
   </blockquote>
</main>
```

### Footer元素
`footer` 元素表示文档或 section 的 「页脚」部分。大部分网站，footer 元素会用包含练习方式和公司信息，简短的「关于」介绍，社交媒体标志和链接等








