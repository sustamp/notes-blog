---
#layout: post
layout: post-custom
title: 利用github pages构建个人网站
---

本文介绍如何使用GitHub创建个人的网站或博客。在此之前，请确保你已经拥有一个github账号，否则请访问&lt;a href="https://github.com/" target="_blank"&gt;GitHub&lt;/a&gt;注册一个账号。

**Tips**  
注册账号时请为你填写一个**好看**的用户名，因为它将是你在GitHub上使用众多功能时的链接凭证。请尽量不要胡乱输入一个用户名。

## 1.创建仓库

GitHub有**个人站点**[user]和**项目站点**[project]的之分。

GitHub个人站点将为你提供免费域名以供访问。域名格式为：`https://[username].github.io`。其中`username`就是你的用户名，域名格式在Github上是固定的，它将是你的个人主页地址。如果你自己购买了域名，也可以用自己购买的域名与这个地址映射。

接下来我们来创建仓库，这里建议尽量创建**公共**仓库(Public)，因为私有仓库(Private)在 GitHub Action有免费额度限制。

1. 登录GitHub后，点击右上角的"+"号按钮创建一个新的仓库"New repository"。  
   - 若将仓库名"Repository Name"命名为：`[username].github.io`，确认创建后你的**个人站点**就创建成功了。访问地址：https://[username].github.io。  
   - 若仓库名命名不是`[username].github.io`的格式，比如你命名成`HelloGit`，则在GitHub上创建一个名为"HelloGit"的**项目仓库**，同时它也将是你的**项目站点**。访问地址：https://[username].github.io/[repositoryname]  
   
观察上面的2个访问地址，可以发现项目站点的访问地址只是在个人站点链接后增加"/仓库名"拼接的。

那么接下来都将以个人站点的仓库作为后续内容的讲述标本。

2. 创建主页文件index.html  
   我们可以在仓库新建一个文件Create new file，命名为：index.html，这是主页文件。文件内容可以随便填写，比如"Hello world!"，然后点击提交。此时我们在浏览器访问个人站点或项目站点就可以看到这个页面上的内容了。
   站点地址默认会读index.html/index.md/README.md等文件的内容。

## 2.启用Github pages

- 点击仓库的**Settings**菜单进入配置页。
- 选择左侧栏中**Code and automation**下的Pages进入GitHub Pages设置页。
- 使用main分支部署。在**Build And Deplovment**中点击**Source**下拉框，选择"Deploy from a branch"，Branch 选择 main。
- 点击Save保存。
  
&lt;img src="/notes/assets/pictures/GitHub-Settings-1.png" /&gt;

你也可以选择**其它分支**进行部署，这要求你提前新建好分支。比如新建一个`gh-pages`分支。

**GitHub Actions** 是另外一个可选的部署方式。它可以进行代码的同步和部署，如果你使用GitHub Actions，可以配置触发条件和部署信息。当条件触发时，提交的代码会同步到分支上，然后在分支进行站点的部署和发布。

&gt;启用Github Pages会创建仓库的部署。在等待部署期间，GitHub Actions可能需要长达一分钟的时间才能响应，需要耐心等待。  
注意：在Pages设置的顶部，会出现你的网站链接，复制链接或者点击"Visit Site"按钮可以访问你的GitHub Pages站点。


## 2.定制主题

这里使用GitHub Pages推荐的jekyll主题来定制个人网站的风格。

### 2. 在仓库根目录下新建一个_config.yml文件。  
在仓库**Code**菜单中添加一个文件Add file -&gt; Create new file，上方填写文件名`_config.yml`，填写如下内容：

```yaml
remote_theme: pages-themes/cayman@v0.2.0 #这里选择你要使用的远程主题
plugins:
- jekyll-remote-theme # 使用远程主题需要引入这个插件
title: Sustamp学习笔记
description: #这里输入你的主页描述
#baseUrl是定义基础路径，个人站点默认是"/"，项目站点则需要在这里设置"/仓库名"。
#这会让基础地址定位成：https://username.github.io/[baseurl]，方便后续的资源访问。
baseurl: "/"  #项目站点设置为"/仓库名"
```

Commit提交后保存。

### 2. 编写index.md文件，编写主页内容。  
我们之前创建了一个index.html文件，具备前端编程能力的开发者们可以在这里自己定义html内容打造自己专属的主页内容。  

但这里我们用jekyll主题面向非开发者编写主页。将index.html改名为index.md。在原有内容的顶部增加如下代码:  
   
```markdown
---
layout: defalut
title: 你的主页标题 #输入你的页面标题
---
```

&gt;jekyll是量行3个分隔符号`---`作为虚线，是**YAML**头信息的识别区域。头信息必须在文件的开始部分，并且需要按照 YAML 的格式写在两行三虚线之间。任何只要包含 YAML 头信息的文件在 Jekyll 中都能被当做一个特殊的文件来处理

### 3. 定制布局。  
在上述第2点我们引用了`layout: defalut`的布局。这其实是使用的是`_layout`目录下的`default.html`文件。

现在我们创建_layout目录并新建default.html。在仓库新建文件，输入`/_layout/default.html`，这会同时创建目录`_layout`，并新增`default.html`文件，文件内容如下：

<pre><code>
  &lt;!DOCTYPE html&gt;
  &lt;html lang="&lcub;&lcub; site.lang | default: "en-US" &rcub;&rcub;"&gt;
    &lt;head&gt;
      &lt;meta charset="UTF-8"&gt;

&lcub;% seo %&rcub;

      &lt;link rel="preconnect" href="https://fonts.gstatic.com"&gt;
      &lt;link rel="preload" href="https://fonts.googleapis.com/css?family=Open+Sans:400,700&display=swap" as="style" type="text/css" crossorigin&gt;
      &lt;meta name="viewport" content="width=device-width, initial-scale=1"&gt;
      &lt;meta name="theme-color" content="#157878"&gt;
      &lt;meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"&gt;
      &lt;link rel="stylesheet" href="&lcub;&lcub; '/assets/css/style.css?v=' | append: site.github.build_revision | relative_url &rcub;&rcub;"&gt;
      &lcub;% include head-custom.html %&rcub;
    &lt;/head&gt;
    &lt;body&gt;
      &lt;a id="skip-to-content" href="#content"&gt;Skip to the content.&lt;/a&gt;

      &lt;header class="page-header" role="banner"&gt;
        &lt;h1 class="project-name"&gt;&lcub;&lcub; page.title | default: site.title | default: site.github.repository_name &rcub;&rcub;&lt;/h1&gt;
        &lt;h2 class="project-tagline"&gt;&lcub;&lcub; page.description | default: site.description | default: site.github.project_tagline &rcub;&rcub;&lt;/h2&gt;
        &lcub;% if site.github.is_project_page %&rcub;
          &lt;a href="&lcub;&lcub; site.github.repository_url &rcub;&rcub;" class="btn"&gt;View on GitHub&lt;/a&gt;
        &lcub;% endif %&rcub;
        &lcub;% if site.show_downloads %&rcub;
          &lt;a href="&lcub;&lcub; site.github.zip_url &rcub;&rcub;" class="btn"&gt;Download .zip&lt;/a&gt;
          &lt;a href="&lcub;&lcub; site.github.tar_url &rcub;&rcub;" class="btn"&gt;Download .tar.gz&lt;/a&gt;
        &lcub;% endif %&rcub;
      &lt;/header&gt;

      &lt;main id="content" class="main-content" role="main"&gt;
        &lcub;&lcub; content &rcub;&rcub;

        &lt;footer class="site-footer"&gt;
          &lcub;% if site.github.is_project_page %&rcub;
            &lt;span class="site-footer-owner"&gt;&lt;a href="&lcub;&lcub; site.github.repository_url &rcub;&rcub;"&gt;&lcub;&lcub; site.github.repository_name &rcub;&rcub;&lt;/a&gt; is maintained by &lt;a href="&lcub;&lcub; site.github.owner_url &rcub;&rcub;"&gt;&lcub;&lcub; site.github.owner_name &rcub;&rcub;&lt;/a&gt;.&lt;/span&gt;
          &lcub;% endif %&rcub;
          &lt;span class="site-footer-credits"&gt;This page was generated by &lt;a href="https://pages.github.com"&gt;GitHub Pages&lt;/a&gt;.&lt;/span&gt;
        &lt;/footer&gt;
      &lt;/main&gt;
    &lt;/body&gt;
  &lt;/html&gt;
</code></pre>

这是GitHub Pages **cayman**主题的html模板，直接复制填写即可。有关cayman主题的官方内容请访问：&lt;a href="https://github.com/pages-themes/cayman" target="_blank"&gt;https://github.com/pages-themes/cayman&lt;/a&gt;。

jeykll目录结构中的`_layouts`目录是存放布局文件的。**default.html**是布局模板中的一种，我们还可以定义page.html, post.html，home.html等页面模板。然后在md文件的头信息中选择使用哪种布局模板。

为了后续的博客文章编写，我们在定义一个post.html模板。在`_layout`目录下继续新增一个`post.html`文件。内容如下：

<pre><code>
---
layout: default
---
&lt;article itemscope itemtype="http://schema.org/BlogPosting"&gt;

  &lt;header class="post-header"&gt;
    &lt;h1 class="post-title" itemprop="name headline"&gt;&lcub;&lcub; page.title | escape &rcub;&rcub;&lt;/h1&gt;
    &lt;p class="post-meta"&gt;
      &lt;time datetime="&lcub;&lcub; page.date | date_to_xmlschema &rcub;&rcub;" itemprop="datePublished"&gt;
        &lcub;% assign date_format = site.cayman-blog.date_format | default: "%b %-d, %Y" %&rcub;
        &lcub;&lcub; page.date | date: date_format &rcub;&rcub;
      &lt;/time&gt;
      &lcub;% if page.author %&rcub;
        • &lt;span itemprop="author" itemscope itemtype="http://schema.org/Person"&gt;&lt;span itemprop="name"&gt;&lcub;&lcub; page.author &rcub;&rcub;&lt;/span&gt;&lt;/span&gt;
      &lcub;% endif %&rcub;&lt;/p&gt;
  &lt;/header&gt;

  &lt;div itemprop="articleBody"&gt;
    &lcub;&lcub; content &rcub;&rcub;
  &lt;/div&gt;

  &lcub;% if site.disqus.shortname %&rcub;
    &lcub;% include disqus_comments.html %&rcub;
  &lcub;% endif %&rcub;
&lt;/article&gt;
</code></pre>

这模板会在之后的博客文章中用到。
   

## 3.编写博客文章

### 1. 创建博客目录_posts。  

jeykll要求将博客文章放置在`_posts`目录下，目录下的文章文件默认要求`yyyy-MM-dd-title.md`格式命名。

在目标仓库继续新增文件，输入`/_posts/2024-10-31-my-first-post.md`，就可以创建_posts目录，同时创建了一个2024-10-31-my-first-post.md文件，它将是我们的第一篇博客文章。文章内容可随便填写，但主题区域需要一些基本设置：

```markdown
---
layout: post
title: 我的第一篇博客 
---

填写你的文章正文内容

```

这里，布局使用的是post.html页面模板，title是对你的文章标题。文件提交保存后，其实就可以进行访问了。为了让文章在我们的主页显示出来，需要修改index.md文件。

### 2. 主页显示文章

调整我们的index.md内容，填写一代代码：

<pre><code>
---
layout: default
title: 你的主页标题
---

文章列表:

&lt;ul&gt;
  &lcub;% for post in site.posts %&rcub;
    &lt;li&gt;
      &lt;a href="&lcub;&lcub; post.url &rcub;&rcub;"&gt;&lcub;&lcub; post.title &rcub;&rcub;&lt;/a&gt;&lt;span&gt;    (&lcub;&lcub; post.date | date_to_string &rcub;&rcub;)    &lt;/span&gt;
    &lt;/li&gt;
  &lcub;% endfor %&rcub;
&lt;/ul&gt;
</code></pre>


这样，jekyll就会遍历_posts目录，检索其下的文章内容，并显示在主页下，你就可以选择你的文章访问了。

访问前关注一下仓库中**Actions**内容，查看部署进度，部署成功后，新的内容才会生成。


