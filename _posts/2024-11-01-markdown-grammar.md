---
#layout: post
layout: post-custom
title: "Markdown语法"
---

本文记录一些自己常用的markdown语法。

---
## 标题语法

使用`# 标题`方式创建标题。#后面跟一个空格，然后是标题文本。
有几个'#'就表示是几级标题。

---
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

---
## 分割线语法

要创建分隔线，请在单独一行上使用三个或多个星号 (***)、破折号 (---) 或下划线 (___) ，并且不能包含其他内容。

```
***

---

_________________
```

---
## 强调语法

`*斜体*`，表示*斜体*。

`**粗体**`，表示粗体。

`***斜体+粗体***`，表示***斜体+粗体***。

`~~删除线~~`，表示~~删除线~~。

---
## 换行语法

最一行的末尾添加两个或多个空格，然后按回车键，即可创建一个换行`<br>`。这种叫`结尾空格(trailing whitespace)`的换行手法是有争议的，因为很难在编辑器中直接看到空格。

Markdown同时支持html标签，可以直接使用html的`<br>`标签。

**总结**  
为了兼容性，请在行尾添加“结尾空格”或 HTML 的 <br> 标签来实现换行。

---
## 列表语法

### 无序列表

### 有序列表

---
## 链接语法

markdown超链接语法代码：  
`[超链接显示名](超链接地址 "超链接title")`。*注意空格位置*。

但我比较喜欢用html标签：  
`<a href="超链接地址" title="超链接title" target="_blank">超链接显示名</a>`。

### 网址或Email

使用尖括号`<内容>`可以很方便地把网址、Email等变成可点击的超链接。  

```
<https://github.com/>
```

渲染效果：
<https://github.com/>

---
## 图片语法

要添加图像，请使用感叹号 (!), 然后在方括号增加替代文本，图片链接放在圆括号里，括号里的链接后可以增加一个可选的图片标题文本。

markdown图片语法代码：  
`![图片alt](图片链接 "图片title")`

对应HTML代码：  
`<img src="图片链接" alt="图片alt" title="图片title">`  

### 链接图片

这是把图像作为链接使用，或者说给图片**增加链接**。

需要将图像的Markdown 代码括在方括号中，然后将链接添加在圆括号中。

```
[![图片alt](图片链接 "图片title")](链接地址)
```
渲染之后点击图片就会跳转到链接地址。

---
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
许多Markdown处理器都支持受围栏代码块的语法突出显示。使用此功能，您可以为编写代码的任何语言添加颜色突出显示。要添加语法突出显示，请在受防护的代码块之前的**反引号旁边指定一种语言**。

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

#### Markdown代码块支持的语言列表

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

---
## 引用语法

要创建块引用，请在段落前添加一个 `>` 符号。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
```

渲染效果:
> Dorothy followed her through many of the beautiful rooms in her castle.


### 多个段落的引用
块引用可以包含多个段落。为段落之间的空白行添加一个 > 符号。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

### 嵌套块引用
块引用可以嵌套。在要嵌套的段落前添加一个 `>>` 符号。从嵌套块出来，则在段落结束后空一行再添加 `>>` 符号。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
>> 
> something new
```

渲染效果：
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
>>
> somethingnew

### 带有其他元素的快引用
块引用可以包含其他 Markdown 格式的元素。并非所有元素都可以使用，你需要进行实验以查看哪些元素有效。


---
## 定义列表
一些Markdown处理器允许您创建术语及其对应定义的定义列表。要创建定义列表，请在第一行上键入术语。在下一行，键入一个冒号，后跟一个空格和定义。

markdown语法：

```
First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.
```


HTML代码像这样：

```html
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

显示效果：  
***First Tem***  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is the definition of the first term.

***Second Term***  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is one definition of the second term.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is another definition of the second term.




---
## 参考资料
<a href="https://markdown.com.cn/basic-syntax/" target="_blank">Markdown基本语法</a>  

<a href="https://markdown.com.cn/extended-syntax/" target="_blank">Markdown拓展语法</a>  


