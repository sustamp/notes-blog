---
layout: post-custom
title: vscode使用技巧
---

本文记录在使用vscode的方式，技巧，插件等一些技巧。

## 丰富的插件

打开vscode，最左侧找到拓展`Extensions`即可寻找和安装插件。

### 通义灵码（TONGYI Lingma）
阿里推出的大数据研发工具，可以方便我们的代码开发工作，它有很多功能，比如：
1. AI代码生成
2. AI代码补全
3. AI代码提示
4. AI代码重构
5. AI问答功能

在`Extensions`搜索框输入通义灵码或拼音均可搜索到。

安装后可能需要登录阿里账号，这里我用的是阿里邮箱的账号。

配置好账号后，就可以使用通义灵码了，其中**AI问答**的图标会出现在vscode左侧栏。

### Markdown Preview Enhanced
这个插件可以让我们使用markdown语法来编写文档，并且可以预览效果。

### Markdown All in One
这个插件可以让我们使用markdown语法来编写文档，并且可以预览效果，并且可以生成目录`Table of Contents`。

在md文档中需要插入目录的位置，使用vscode快捷键`Ctrl+Shift+P`，输入`create table of contents`，选择`Markdown All in One: Create Table of Contents`即可生成目录。

### Live Server
Live Server 是一个非常方便的插件，可以让我们直接在浏览器中预览我们的网页。

安装后，在我们的工作区右键`.html`结尾的文件，选择`Open with Live Server`即可在浏览器中预览。

### Document This
这个插件可以让我们快速生成函数注释，特别是js文件的方法注释。

使用 Document This 插件生成注释的步骤如下：
1. 安装 `Document This`插件：
   - 打开VS Code。
   - 点击左侧活动栏的拓展图标。
   - 搜索 `Document This`并安装。
2. 生成注释：
   - 打开你的JavaScript文件。
   - 选中你的函数名，比如buttonClick函数。
   - 按 `Alt + Shift + D`（Windows/Linux）或 `Option + Shift + D`（macOS）。

生成的注释可能如下所示：

```javascript
/**
 * 当汉堡按钮被点击时显示或隐藏导航菜单。
 *
 * @param {string} burgerSelector - 汉堡按钮的选择器
 * @param {string} menuSelector - 导航菜单的ID
 * @param {string} cssClass - 用于显示或隐藏导航菜单的CSS类名
 */
export function burgerClick(burgerSelector, menuSelector, cssClass) {
    // 获取汉堡按钮和导航菜单的DOM元素
    const burger = document.querySelector(burgerSelector);
    const navMenu = document.getElementById(menuSelector);

    // 为汉堡按钮添加点击事件监听器
    burger.addEventListener('click', () => {
        // 检查导航菜单是否已经包含指定的CSS类
        if (navMenu.classList.contains(cssClass)) {
            // 如果包含，则移除该类
            navMenu.classList.remove(cssClass);
        } else {
            // 如果不包含，则切换该类
            navMenu.classList.toggle(cssClass);
        }
    });

    // 为文档添加点击事件监听器
    document.addEventListener('click', function(event) {
        // 检查点击的目标是否在导航菜单内或汉堡按钮
        if (!navMenu.contains(event.target) && !event.target.closest(burgerSelector)) {
            // 如果不在，则移除导航菜单的 'show' 类
            navMenu.classList.remove('show');
        }
    });
}
```

## VS Code 快捷键的添加或修改

以 `Document This` 插件为例，生成函数注释的快捷键是 `Alt + Shift + D`。

若我们经常使用IntelliJ IDEA / Eclipse 的快捷键，比如 `Alt + Shift + J`来生成注释，则可以为 `Document This`插件添加这个快捷键。步骤如下：
1. 打开VS Code的命令面板:
   - 使用快捷键 `Ctrl + Shift + P`（Windows/Linux）或 `Command + Shift + P`（macOS）打开命令面板。
2. 搜索 `Document This`的命令：
   - 输入 `Document This`，在预选项的右侧有个齿轮按钮可点击。
3. 配置快捷键：
   - 点击齿轮图标`Configure Keybinding`，在快捷键命令列表中**鼠标右键点击**你想调整的命令，选择 `Add Keybinding`，然后键入你的快捷键指令，比如 `Alt + Shift + J`，回车确认即可。

 现在，当你使用 `Alt + Shift + J` 键来生成注释时，`Document This`插件就会生效。

## 快速生成HTML5基本代码结构

打开你的html文件，在空白处键入 `html` 或 `html:5` 在出现的代码提示框中选择`html:5`，然后回车即可。

## 工作区可以添加不同的文件夹
vscode支持添加`多个文件夹`到工作区`WorkSpace`，这样我们就可以在一个工作区中同时管理多个项目。




