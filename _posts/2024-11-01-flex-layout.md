---
#layout: post
layout: post-custom
title: "使用Flexbox进行网页布局"
---

网页布局（layout）是 CSS (Casscading Style Sheets，层叠样式表) 的一个重点应用。

网页布局一般有三种方式：
- CSS Float 浮动布局
- CSS Flexbox 弹性盒子布局
- CSS Grid-View 网格布局
  
**float布局**在各浏览器兼容性差。依赖`display` + `position` + `float`属性。它对于特殊布局非常不方便，比如：垂直居中。

**Flex 布局**，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全地使用这项功能。在各浏览器兼容性好，可以适应不同的屏幕尺寸和显示设备。

**Grid-View布局**将整个页面划分了12个格子以方便布局，但这同样也会有个别浏览器不支持。

本文介绍如何使用Flex进行网页布局。

## Flex容器

HTML中使用 flexbox 的区域就叫做 **flex 容器**（flex container）。

当我们把一个HTML元素的 `display` 属性值改为 `flex` 或者 `inline-flex`，就创建了 flex 容器。容器中的所有子元素自动成为容器成员，叫做 **flex 项目**（flex item）。

为了方便说明，下面给出css和html的代码模板：

```css
.box {
  display: flex;
}
```

```html
<div class="box">
  <span class="item"></span>
  <span class="item"></span>
  <span class="item"></span>
</div>
```

上面代码中，div元素代表是Flex容器，span元素表示Flex的项目，这里有3个项目。

假设我们每个子项目中还有元素，排列方式也想使用flex布局，那么也可以让子项目成为flex容器。

```css
.box{
  display: flex;
}

.sub-section{
  display:flex;
}
```

```html
<div class="box">
  <span>logo</span>
  <div class="sub-section">
    <span>logo-title</span>
    <span>logo-descrption</span>
  </div>
</div>
```

此时，`<div class="box">`容器中有两个项目：
- 一个是`span`。
- 第二个是`<div class="sub-section">`。

它们按照flex进行布局。同时`<div class="sub-section">`也是容器，其中有两个`span`项目，它们按照flex进行布局。

*注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。*

Flex 容器有两根轴线：
- 水平的主轴（main axis）
- 垂直的交叉轴（cross axis）

主轴的起始位置叫**起始线**，结束位置叫**终止线**。

主轴由 `flex-direction` 定义，表示main axis的延伸方向，cross axis一直垂直于main axis，故它的延伸方向因 `flex-direction` 的取值不同而不同。我们接下来在说容器的属性时会再次涉及。

## 容器的属性
容器（`display: flex`）有以下6个属性：

|属性|用途|
|---|---|
|`flex-direction`|主轴延伸方向，即项目的排列方向|
|`flex-wrap`|换行方式|
|`flex-flow`|`flex-direction` 和 `flex-wrap` 的简写形式|
|`justify-content`|主轴上项目之间的对齐方式|
|`align-items`| 定义项目在交叉轴上的如何对齐|
|`align-content`| 当项目有多根轴线时定义对齐方式，只有一根轴线时不起作用|

### 1.flex-direction 
当你设定：

```css
.box{
    flex-direction: row;
}
```

你的主轴将沿着**水平方向**延伸，此时交叉轴的方向是沿着**上下方向**延伸的。若设定 `flex-direction: column` 时，主轴会沿着页面的上下方向延伸，而交叉轴就变成了水平方向延伸。

`flex-direction` 有4个值：  

|取值|说明|
|---|---|
|`row`|默认值。主轴为水平方向，起点在左端|
|`row-reverse`|主轴为水平方向，起点在右端|
|`column`|主轴为垂直方向，起点在上沿|
|`column-reverse`|主轴为垂直方向，起点在下沿|


### 2.flex-wrap
默认情况下，项目都排在一条线上。如果一条线排布下，就由 `flex-wrap` 决定如何换行。

```css
.box{
    flex-wrap: wrap | nowrap | wrap-reverse;
}
```

`flex-wrap`的枚举如下：

|取值|说明|
|---|---|
|`wrap`|换行，第一行在上方|
|`nowrap`|不换行|
|`wrap-reverse`|换行，第一行在下方|


### 3.flex-flow
将两个属性 `flex-direction` 和 `flex-wrap` 组合为简写属性 `flex-flow`。 第一个值指定 `flex-direction`，第二个值指定 `flex-wrap`。

```css
.box{
    flex-flow: row wrap;
}
```

### 4.justify-content
`justify-content` 属性定义了项目在主轴上的对齐方式。具体对齐方式与**主轴的方向**有关。

```css
.box {
  flex-direction: row;
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```

它有5个取值。假设 `flex-direction: row` ，主轴为从左往右：

|取值|说明|
|---|---|
|`flex-start`|默认值，左对齐|
|`flex-end`|右对齐|
|`center`|居中|
|`space-between`|两端对齐，项目之间的间隔都相等|
|`space-around`|每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍|


### 5.align-items
`align-items` 属性定义了项目在交叉轴上如何对齐。具体对齐方式与**交叉轴的方**向有关。

```css
.box {
  flex-direction: row;
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```

它有5个取值。假设 `flex-direction: row` ，主轴为从左往右，此时交叉轴便是从上往下：

|取值|说明|
|---|---|
|`stretch`|默认值，若项目未设置高度或设置auto，将占满整个容器的高度|
|`flex-start`|与交叉轴的起点对齐|
|`flex-end`|与交叉轴的终点对齐|
|`center`|与交叉轴的中点对齐|
|`baseline`|与项目的第一行文字的基线对齐|


### 6.align-content
`align-content` 属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

```css
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

它有6个取值：

|取值|说明|
|---|---|
|`flex-start`|与交叉轴的起点对齐|
|`flex-end`|与交叉轴的终点对齐|
|`center`|与交叉轴的中点对齐|
|`space-between`|与交叉轴两端对齐，轴线之间的间隔平均分布|
|`space-around`|每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框之间的间隔大一倍|
|`stretch`|默认值，轴线占满整个交叉轴|



## 项目的属性
容器中的Flex项目 也有6个属性：

```css
.item{
    /* order定义项目的排列顺序 默认为0，数值越小，排列越靠前*/
    order: <integer>;
    /* flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大 */
    flex-grow: <number>;
    /* flex-shrink定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小 */
    flex-shrink: <number>;
    /* 默认值为auto，即项目的本来大小。 */
    flex-basis: <length> | auto;;
    /* flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。 */
    flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ];
    /* 该属性可能取6个值，除了auto，其他都与align-items属性完全一致。 */
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

### order
定义项目的排列顺序 默认为0，数值越小，排列越靠前。

### flex-grow
定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

如果所有项目的`flex-grow`属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

### flex-shrink
`flex-shrink`定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。

### flex-basis
`flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。

它可以设为跟`width`或`height`属性一样的值（比如350px），则项目将占据固定空间。

### flex

`flex`属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。

该属性有两个快捷值：`auto` (1 1 auto) 和 `none` (0 0 auto)。

建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

### align-self
`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。

该属性可能取6个值，除了`auto`，其他都与`align-items`属性完全一致。


## 资料引用

<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox">flex 布局的基本概念</a>

<a href="http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html">阮一峰的网络日志 - Flex 布局教程：语法篇</a>

