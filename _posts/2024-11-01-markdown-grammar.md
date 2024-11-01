---
layout: post
title: "Markdown语法"
---

## 标题语法

使用`# 标题`方式创建标题。#后面跟一个空格，然后是标题文本。
有几个'#'就表示是几级标题。

## 段落语法

使用空白行将一行或多行文本进行分隔。

<table>
    <thead>
        <tr>
            <td>Markdown语法</td>
            <td>HTML</td>
            <td>预览效果</td>
        </tr>
    </thead>
    <tbody>
        <td>
            <code>这是段落一。</code>
            <br><br>
            <code>这是段落二。</code>
        </td>
        <td>
            <pre>
                <code>&lt;p&gt;这是段落一。&lt;/p&gt;</code>
                <br>
                <code>&lt;p&gt;这是段落二。&lt;/p&gt;</code>
            </pre>
        </td>
        <td>
            这是段落一。
            <br><br>
            这是段落二。
        </td>
    </tbody>
</table>

## 强调语法

`*斜体*`，表示*斜体*。

`**粗体**`，表示粗体。

`***斜体+粗体***`，表示***斜体+粗体***。

`~~删除线~~`，表示~~删除线~~。

## 代码语法

### 代码
要将单词或短语表示为代码，请将其包裹在反引号 (`) 中。

``At the command prompt, type `nano`.``， At the command prompt, type `nano`.

### 围栏代码块

Markdown基本语法允许您通过将行缩进四个空格或一个制表符来创建代码块。如果发现不方便，请尝试使用受保护的代码块。在代码块之前和之后的行上使用三个反引号（```）。

<pre>
    <code>&#96;&#96;&#96;
    {
        &quot;firstName&quot;: &quot;John&quot;,
        &quot;lastName&quot;: &quot;Smith&quot;,
        &quot;age&quot;: 25
    }
    &#96;&#96;&#96;</code>
</pre>

显示效果如下：
```
{
    firstName: John&quot,
    lastName: &quot;Smith&quot;,
    &quot;age&quot;: 25   
}
```

#### 语法高亮
许多Markdown处理器都支持受围栏代码块的语法突出显示。使用此功能，您可以为编写代码的任何语言添加颜色突出显示。要添加语法突出显示，请在受防护的代码块之前的反引号旁边指定一种语言。

<pre>
    <code>&#96;&#96;&#96;json
    {
        &quot;firstName&quot;: &quot;John&quot;,
        &quot;lastName&quot;: &quot;Smith&quot;,
        &quot;age&quot;: 25
    }
    &#96;&#96;&#96;</code>
</pre>

显示效果如下：
```json
{
    firstName: John,
    lastName: Smith,
    age: 25   
}
```

## Markdown代码块支持的语言列表

|语言|关键字|调用的js|说明|
|----|----|----|----|
|C|cpp,c|shBrushCpp.js|C语言|
|C++|cpp|...|C++|
|C#|csharp, c-sharp, c#||C#语言|
|Java|java|shBrushJava.js|...|
|PHP|php|shBrushPython.js|...|
|python|py, python|shBrushPython.js|...|
|bash|bash|shBrushBash.js|...|
|shell|bash, shell, sh, zsh|shBrushBash.js|Shell scripting|
|sql|sql|shBrushSql.js|结构化查询语言|
|vue|vue|...|vue框架|
|javascript|js, jscript, javascript|shBrushJScript.js|...|
|json|json|...|...|
|css|css|...|Casscading Style Sheets，层叠样式表|
|scss&scss|sass, scss|shBrushSass.js|SCSS是一种CSS预处理器，它扩展了CSS的功能，为编写提供额外的便利|
|xml|xml|...|XML and also used for HTML with inline CSS and Javascript|
|yaml|...|...|YAML是一种数据交换格式，被用来描述各种配置文件，如_config.yml|
|http|...|...|...|
|markdown|...|...|我支持我自己|
|go|go, golang|shBrushGo.js|...|
|Ruby|rb, jruby, ruby|...|...|
|ActionScript 3.0|actionscript3 , as3|shBrushAS3.js|...|
|Vim|vim, viml|...|Vim Script|
|apache|apache|...|...|
|AppleScript|applescript|shBrushAppleScript.js||
|asp|...|...|...|
|brainfuck|...|...|...|
|cfm|...|...|...|
|clojure|...|...|...|
|cmake|...|...|...|
|CoffeeScript|coffee-script, coffeescript, coffee|...|...|
|cs|...|...|...|
|csv|...|...|...|
|diff|...|...|...|
|elixir|...|...|...|
|erb|...|...|HTML + Embedded Ruby|
|haml|...|...|...|
|jsx|...|...|...|
|less|...|...|...|
|lolcode|...|...|...|
|make|...|...|Makefile|
|matlab|...|...|...|
|nginx|...|...|...|
|objectivec|...|...|...|
|pascal|...|...|...|
|Perl|...|...|...|
|profile|...|...|python profiler output|
|rust|...|...|...|
|salt, saltstate - Salt|...|...|...|
|svg|...|...|...|
|swift|...|...|...|
|smalltalk|...|...|...|
|volt|...|...|...|
|vhdl|...|...|...|


## 参考资料
<a href="https://markdown.com.cn/basic-syntax/" target="_blank">Markdown基本语法</a>
<a href="https://markdown.com.cn/extended-syntax/" target="_blank">Markdown拓展语法</a>

