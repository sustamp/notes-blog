---
layout: post
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

HTML中使用 flexbox 的区域就叫做 **flex 容器**。当我们把一个容器的 `display` 属性值改为 `flex` 或者 `inline-flex`就创建了 flex 容器。容器中的直系子元素就会变为 **flex 元素**。

```css
.box {
  display: flex;
}
```

```html
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>
    Three<br>
    has<br>
    extra<br>
    text
  </div>
</div>
```

*注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。*


## 参考资料

<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox">flex 布局的基本概念</a>
<a href="http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html">阮一峰的网络日志 - Flex 布局教程：语法篇</a>

