---
# layout: post
layout: post-custom
title: vue框架学习笔记
---

想帮同学做个赛季数据的分析网页，所以学习下vue。但是断断续续的也没怎么学全，官方文档的版本可能随时会变，这里就边学边记了。

本文目录：
- [vue的两个核心功能](#vue的两个核心功能)
- [渐进式框架](#渐进式框架)
- [单文件组件](#单文件组件)
- [API风格](#api风格)
	- [该选哪一个](#该选哪一个)
- [快速上手](#快速上手)
	- [win7系统安装nodejs](#win7系统安装nodejs)
	- [创建一个vue项目](#创建一个vue项目)
		- [推荐的IDE配置](#推荐的ide配置)
	- [通过CDN使用vue](#通过cdn使用vue)
- [语法基础](#语法基础)
	- [创建一个应用](#创建一个应用)
		- [应用实例](#应用实例)
		- [根组件](#根组件)
		- [挂载(mount)应用](#挂载mount应用)
		- [DOM中的根组件模板](#dom中的根组件模板)
		- [应用配置](#应用配置)
		- [多个应用实例](#多个应用实例)
	- [模板语法](#模板语法)
		- [文本插值](#文本插值)
		- [原始HTML](#原始html)
		- [Attribute绑定](#attribute绑定)
		- [布尔型Attribute](#布尔型attribute)
		- [动态绑定多个值](#动态绑定多个值)
		- [指令Directives](#指令directives)
			- [参数Arguments](#参数arguments)
		- [动态参数](#动态参数)
			- [动态参数值的限制](#动态参数值的限制)
			- [动态参数语法的限制](#动态参数语法的限制)
		- [修饰符](#修饰符)
	- [响应式基础](#响应式基础)
		- [声明响应式状态](#声明响应式状态)
			- [Script setup](#script-setup)
			- [为什么要使用ref？](#为什么要使用ref)
			- [深层响应性](#深层响应性)
			- [DOM更新时机](#dom更新时机)
			- [reactive()](#reactive)
				- [Reactive Proxy vs. Original](#reactive-proxy-vs-original)
				- [reactive()的局限性](#reactive的局限性)
		- [额外的ref解包细节](#额外的ref解包细节)
			- [作为reactive对象的属性](#作为reactive对象的属性)
			- [数组和集合的注意事项](#数组和集合的注意事项)
			- [在模板中解包的注意事项](#在模板中解包的注意事项)
	- [计算属性](#计算属性)
		- [计算属性缓存 vs 方法](#计算属性缓存-vs-方法)
		- [避免直接修改计算属性值](#避免直接修改计算属性值)
	- [类与样式的绑定](#类与样式的绑定)
		- [绑定 HTML class](#绑定-html-class)
			- [绑定对象](#绑定对象)
			- [绑定数组](#绑定数组)
			- [在组件上使用](#在组件上使用)
			- [绑定内联样式](#绑定内联样式)
				- [绑定对象](#绑定对象-1)
				- [绑定数组](#绑定数组-1)
				- [自动前缀](#自动前缀)
				- [样式多值](#样式多值)
	- [条件渲染](#条件渲染)
		- [v-if](#v-if)
		- [v-else](#v-else)
		- [v-else-if](#v-else-if)
		- [template上的v-if](#template上的v-if)
		- [v-show](#v-show)
		- [v-show vs. v-if](#v-show-vs-v-if)
	- [列表渲染](#列表渲染)
		- [v-for](#v-for)
		- [v-for 与对象](#v-for-与对象)
		- [在v-for里使用范围值](#在v-for里使用范围值)
		- [template中的v-for](#template中的v-for)
		- [v-for 与 v-if](#v-for-与-v-if)
		- [通过Key管理状态](#通过key管理状态)
		- [在组件中使用v-for](#在组件中使用v-for)
		- [数组变化侦测](#数组变化侦测)
			- [替换一个数组](#替换一个数组)
			- [展示过滤或排序后的结果](#展示过滤或排序后的结果)
	- [事件处理](#事件处理)
		- [监听事件](#监听事件)
			- [内联事件处理器](#内联事件处理器)
			- [方法事件处理器](#方法事件处理器)
				- [方法与内联事件判断](#方法与内联事件判断)
			- [在内联处理器中调用方法](#在内联处理器中调用方法)
		- [在内联事件处理器中访问事件参数](#在内联事件处理器中访问事件参数)
		- [事件修饰符](#事件修饰符)
		- [按键修饰符](#按键修饰符)
			- [按键别名](#按键别名)
			- [系统按键修饰符](#系统按键修饰符)
			- [.exact修饰符](#exact修饰符)
			- [鼠标按键修饰符](#鼠标按键修饰符)
	- [表单输入绑定](#表单输入绑定)
		- [基本用法](#基本用法)
			- [文本](#文本)
			- [多行文本](#多行文本)
			- [复选框](#复选框)
			- [单选按钮](#单选按钮)
			- [选择器](#选择器)
			- [值绑定](#值绑定)
			- [修饰符](#修饰符-1)
	- [生命周期](#生命周期)
		- [注册周期钩子](#注册周期钩子)
	- [侦听器](#侦听器)
		- [基本示例](#基本示例)
		- [侦听数据源类型](#侦听数据源类型)
		- [深层侦听器](#深层侦听器)
		- [即时回调的侦听器](#即时回调的侦听器)
		- [一次性侦听器](#一次性侦听器)
		- [watchEffect()](#watcheffect)
		- [watch vs. watchEffect](#watch-vs-watcheffect)
		- [回调触发的时机](#回调触发的时机)
			- [Post Watchers](#post-watchers)
			- [同步侦听器](#同步侦听器)
			- [停止侦听器](#停止侦听器)
	- [模板引用](#模板引用)
		- [访问模板引用](#访问模板引用)
		- [v-for中的模板引用](#v-for中的模板引用)
		- [函数模板的引用](#函数模板的引用)
		- [组件上的ref](#组件上的ref)
	- [组件基础](#组件基础)
		- [定义一个组件](#定义一个组件)
		- [使用组件](#使用组件)
		- [传递 props](#传递-props)
		- [监听事件](#监听事件-1)
		- [通过插槽来分配内容](#通过插槽来分配内容)
		- [动态组件](#动态组件)
		- [DOM 内模板解析注意事项](#dom-内模板解析注意事项)
			- [大小写区分](#大小写区分)
			- [闭合标签](#闭合标签)
			- [元素位置限制](#元素位置限制)
- [术语汇总](#术语汇总)
	- [SFC](#sfc)
	- [kebab-case](#kebab-case)
	- [PascalCase](#pascalcase)
	- [DOM](#dom)


<div id="vue的两个核心功能"></div>

## vue的两个核心功能

- 声明式渲染
  
vue基于html拓展了一套模板语法，可以使用声明式语言描述最终输出的html和js（JavaScript）状态之间的关系。

- 响应性

vue会自动跟踪js状态并在其发生变化时响应式地更新DOM。

<div id="渐进式框架"></div>

## 渐进式框架

vue能够根据需求场景提供不同的处理方式：

- 无需构建步骤，渐进式增强静态的 HTML。
- 在任何页面中作为 Web Components 嵌入
- 单页应用 (SPA) （Single Page Application?）
- 全栈 / 服务端渲染 (SSR)
- Jamstack / 静态站点生成 (SSG)
- 开发桌面端、移动端、WebGL，甚至是命令行终端中的界面

**渐进式框架**的含义：它是一个可以与你共同成长、适应你不同需求的框架。

<div id="单文件组件"></div>

## 单文件组件

Single-File Components，即SFC。我们可以使用一个类似HTML格式的文件来书写vue组件，他被称为单文件组件，也叫*.vue文件。

单文件组件会将一个组件的逻辑（JavaScript），模板（HTML）和样式（CSS）封装在同一个文件里，是VUE的标志性功能。

<div id="API风格"></div>

## API风格

vue的组件有两种不同的书写风格：

- 选项式API（Options API）。
- 组合式API（Composition API）。

<div id="该选哪一个"></div>

### 该选哪一个

选项式 API 以“组件实例”的概念为中心 (即上述例子中的 this)，对于有面向对象语言背景的用户来说，这通常与基于类的心智模型更为一致。同时，它将响应性相关的细节抽象出来，并强制按照选项来组织代码，从而对初学者而言更为友好。

组合式 API 的核心思想是直接在函数作用域内定义响应式状态变量，并将从多个函数中得到的状态组合起来处理复杂问题。这种形式更加自由，也需要你对 Vue 的响应式系统有更深的理解才能高效使用。相应的，它的灵活性也使得组织和重用逻辑的模式变得更加强大。

- 在学习的过程中，推荐采用更易于自己理解的风格。再强调一下，大部分的核心概念在这两种风格之间都是通用的。熟悉了一种风格以后，你也能够很快地理解另一种风格。
- 在生产项目中：
  - 当你不需要使用构建工具，或者打算主要在低复杂度的场景中使用 Vue，例如渐进增强的应用场景，推荐采用选项式 API。
  - 当你打算用 Vue 构建完整的单页应用，推荐采用组合式 API + 单文件组件。


<div id="快速上手"></div>

## 快速上手

<div id="win7系统安装nodejs"></div>

### win7系统安装nodejs

win7系统对nodejs版本的支持最高是v13.14.0。这里我选择nodejs官网previous version中的node-v18.19.1-win-x64.zip压缩包下载，直接解压使用。

将node-v18.19.1-win-x64.zip解压到工作磁盘目录中，如`D:\Soft\nodejs`。之后需要进行环境配置。

打开计算机的高级系统设置，设置环境变量。

1.对系统变量的Path编辑，添加nodejs的安装目录。

	变量名：Path
	变量值：****;****;D:\Soft\nodejs

  
2.在系统变量中新建一个`NODE_HOME`，值为`D:\Soft\nodejs\node_modules`,同样添加到系统变量Path中。

	变量名：Path
	变量值：****;****;D:\Soft\nodejs;%NODE_HOME%
	

3.在用户变量中新建一个变量`NODE_SKIP_PLATFORM_CHECK`，值为1。

以上步骤完整后点击确定完成修改，然后打开cmd，输入命令行查看node版本和npm版本，若能看到版本号输出，说明node安装正常。

	E:\WebWorkSpace\vue>npm -v
	10.2.4
	
	E:\WebWorkSpace\vue>node -v
	v18.19.1

4.全局模块和缓存路径的设置

在nodejs安装目录下新建两个文件夹`【node_global】`及`【node_cache】`，然后打开cmd命令，输入

	npm config set prefix "D:\Soft\nodejs\node_global"
	npm config set cache "D:\Soft\nodejs\node_cache"

然后还需要在计算机的高级系统设置中调整环境变量，将**用户变量**下的【Path】从默认的C盘下的APPData\Roaming\npm 修改为`D:\Soft\nodejs\node_global`，点击确定。

配置完成后，安装个module测试下，咱们就安装最经常使用的express模块，打开cmd窗口，输入以下命令进行模块的全局安装：

	npm install express -g   // -g是全局安装的意思

我们可在`D:\Soft\nodejs\node_global`中看到安装下来的express模块。

<div id="创建一个vue项目"></div>

### 创建一个vue项目

**前提条件**

- 熟悉命令行
- 已安装18.0或更高版本的Node.js

确保你安装了最新版本的 Node.js，并且你的当前工作目录正是打算创建项目的目录。在命令行中运行以下命令 ：

	npm create vue@latest

这一指令将会安装并执行 create-vue，它是 Vue 官方的项目脚手架工具。你将会看到一些诸如 TypeScript 和测试支持之类的可选功能提示：

	✔ Project name: … <your-project-name>
	✔ Add TypeScript? … No / Yes
	✔ Add JSX Support? … No / Yes
	✔ Add Vue Router for Single Page Application development? … No / Yes
	✔ Add Pinia for state management? … No / Yes
	✔ Add Vitest for Unit testing? … No / Yes
	✔ Add an End-to-End Testing Solution? … No / Cypress / Playwright
	✔ Add ESLint for code quality? … No / Yes
	✔ Add Prettier for code formatting? … No / Yes

	Scaffolding project in ./<your-project-name>...
	Done.

如果不确定是否要开启某个功能，你可以直接按下回车键选择 No。在项目被创建后，通过以下步骤安装依赖并启动开发服务器：

	cd <your-project-name>
	npm install
	npm run dev

你现在应该已经运行起来了你的第一个 Vue 项目！请注意，生成的项目中的示例组件使用的是组合式 API 和 script setup，而非选项式 API。

当你准备将应用发布到生产环境时，请运行：

	npm run build

此命令会在 ./dist 文件夹中为你的应用创建一个生产环境的构建版本。关于将应用上线生产环境的更多内容，请阅读生产环境部署指南。

<div id="推荐的IDE配置"></div>

#### 推荐的IDE配置

- 推荐使用的 IDE 是 VSCode，配合 Vue 语言特性 (Volar) 插件。该插件提供了语法高亮、TypeScript 支持，以及模板内表达式与组件 props 的智能提示。
- WebStorm 同样也为 Vue 的单文件组件提供了很好的内置支持。
- 其他支持语言服务协议 (LSP) 的 IDE 也可以通过 LSP 享受到 Volar 所提供的核心功能：
  - Sublime Text 通过 LSP-Volar 支持。
  - vim / Neovim 通过 coc-volar 支持。
  - emacs 通过 lsp-mode 支持。 

<div id="通过CDN使用vue"></div>

### 通过CDN使用vue

CDN，全称Content Delivery Network，是内容分发网络。通过 CDN 使用 Vue 时，不涉及“构建步骤”。这使得设置更加简单，并且可以用于增强静态的 HTML 或与后端框架集成。但是，你将无法使用单文件组件 (SFC) 语法。

借助 script 标签直接通过 CDN 来使用 Vue：

	<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

这里我们使用了 unpkg，但你也可以使用任何提供 npm 包服务的 CDN，例如 jsdelivr 或 cdnjs。当然，你也可以下载此文件并自行提供服务。

<div id="语法基础"></div>

## 语法基础

<div id="创建一个应用"></div>

### 创建一个应用
----
#### 应用实例

每个应用都是通过`createApp`函数创建一个新的**应用实例**：

	import {createApp} from 'vue'
	const app = createApp({
		/*根组件选项*/
	})

`createApp`的API定义：

	function createApp(rootComponent: Component, rootProps?: object): App

第一个参数是根组件。第二个参数可选，它是要传递给根组件的 props。

#### 根组件

我们传入`createApp`的对象实际是一个组件，每个应用都需要一个**根组件**，其他组件作为其子组件。

如果使用的是SFC，则可以从另外一个文件中导入根组件。

	import {createApp} from 'vue'
	//从一个单文件组件中导入根组件
	import App from './App.vue' //项目src目录下的App.vue文件
	
	const app = createApp(App)

虽然本指南中的许多示例只需要一个组件，但大多数真实的应用都是由一棵嵌套的、可重用的组件树组成的。例如，一个待办事项 (Todos) 应用的组件树可能是这样的：

	App (root component)
	├─ TodoList
	│  └─ TodoItem
	│     ├─ TodoDeleteButton
	│     └─ TodoEditButton
	└─ TodoFooter
	├─ TodoClearButton
	└─ TodoStatistics

后续章节中会讨论如何定义和组合多个组件。在那之前，我们得先关注一个组件内到底发生了什么。

#### 挂载(mount)应用

**应用实例**必须在调用了`.mount()`方法之后才会渲染出来。该方法接受一个“容器”参数，可以是一个实际的DOM元素或一个CSS选择器字符串：

	<div id="app"></div>
	app.mount('#app')

应用根组件的内容将会被渲染在容器元素里面。容器元素自己将不会被视为应用的一部分。
`.mount()`方法应该始终在整个应用配置和资源注册完成后被调用。同时请注意，不同于其他资源注册方法，它的返回值是**根组件实例**而非**应用实例**。

`.mount()`的API具体定义如下：

	interface App {
		mount(rootContainer: Element | string): ComponentPublicInstance
	}

对于每个应用实例，mount() 仅能调用一次。

#### DOM中的根组件模板

#### 应用配置

应用实例会暴露一个.config对象允许我们配置一些应用级的选项，例如定义一个应用级的错误处理器，用来捕获所有子组件上的错误：

	app.config.errorHandler = (err) => {
  		/* 处理错误 */
	}

应用实例还提供了一些方法来注册应用范围内可用的资源，例如注册一个组件：

	app.component('TodoDeleteButton', TodoDeleteButton)

这使得 TodoDeleteButton 在应用的任何地方都是可用的。

确保在挂载应用实例之前完成所有应用配置！

#### 多个应用实例

应用实例并不仅限一个。`createApp` API允许你在同一个页面创建多个共存的Vue应用，而且每个应用都有自己的用于配置和全局资源的作用域。

	const app1 = createApp({
		/* ... */
	})
	app1.mount('#container-1')
	
	const app2 = createApp({
		/* ... */
	})
	app2.mount('#container-2')

如果你正在使用 Vue 来增强服务端渲染 HTML，并且只想要 Vue 去控制一个大型页面中特殊的一小部分，应避免将一个单独的 Vue 应用实例挂载到整个页面上，而是应该创建多个小的应用实例，将它们分别挂载到所需的元素上去。


<div id="模板语法"></div>

### 模板语法

vue使用一种基于HTML的模板语法，是我们能够声明式地将其组件实例的数据绑定到呈现的DOM上。所有的vue模板都是语法层面合法的HTML，可以被符合规范的浏览器和HTML解析器解析。

在底层机制中，vue会将模板编译成高度优化的js代码。结合响应式系统，当应用状态变更时，vue能够智能地推导出需要重新渲染的组件的最少数量，并应用最少的DOM操作。

----

#### 文本插值

最基本的数据绑定形式，它使用的是“Mustache”语法（即双大括号）：

	<span>Message:{{msg}}</span>

双大括号标签会被替换为相应组件实例中的`msg`属性的值。同时每次`msg`属性更改时它也会同步更新。

#### 原始HTML

双大括号会将数据解释为纯文本，而不是 HTML。若想插入HTML，需要使用`v-html`指令：

	<p>Using text interpolation: {{rawHtml}}</p>
	<p>Using v-html directive: <span v-html="rawHtml"></span></p>

#### Attribute绑定

双大括号不能在HTML attributes中使用。想要响应式地绑定一个attribute，请使用`v-bind`指令：
	
	<div v-bind:id="dynamicId"></div>
	//简写
	<div :id="dynamicId"></div>
	//同名简写。与:id="id"相同
	<div :id></div>

`v-bind`指令指示vue将元素的`id` attribute与组件的`dynamicId` 属性保持一致。如果绑定的值为null或者undefined，那么该绑定将会从渲染的元素中移除。

#### 布尔型Attribute

布尔型Attribute依据true / false 值来决定是否应该存在于该元素上。`disabled`就是常见的例子。

	<button :disabled="isButtonShow">Button</button>

当`isButtonShow`为true或一个空字符串（即`<button disabled="">`）时，元素会包含这个`disabled` attribute。而当其为其他假值时attribute将会被忽略。

#### 动态绑定多个值

如果你有像这样的一个包含多个attribute的JavaScript对象：

	const objectOfAttrs = {
		id:'container',
		class:'wrapper'
	}

通过不带参数的`v-bind`，可以将它们绑定到单个元素上：

	<div v-bind="objectOfAttrs"></div>
	//其效果等同于
	<div id="container" class="wrapper"></div>

#### 指令Directives

指令是带有`v-`前缀的特殊attribute。vue提供了许多内置指令，包括`v-bind`和`v-html`。

指令attribute的期望值为一个JavaScript表达式（除了少数几个例外，即之后要说的`v-for`、`v-on`、`v-slot`）。

一个指令的任务是在其表达式的值变化时响应式地更新DOM。以`v-if`为例：

	<p v-if="seen">Now you see me</p>

这里，`v-if`指令会基于表达式`seen`的值的真假来移除/插入该`<p>`元素。

##### 参数Arguments

某些指令需要一个参数，在指令名后通过一个冒号隔开做标识。例如用`v-bind`指令来响应式地更新一个HTML attribute：

	<a v-bind:href="url"></a>
	//简写
	<a :href="url"></a>

这里的`href`就是一个参数，它告诉`v-bind`指令将`url`表达式的值绑定到元素的`href`属性中。

#### 动态参数

同样在指令参数上也可以使用一个JavaScript表达式需要包含在一对方括号内：

	<!--  注意，参数表达式有一些约束，参见下面“动态参数值的限制”与“动态参数语法的限制”章节的解释 -->
	<a v-bind:[attributeName]="url">...</a>
	//简写
	<a :[attributeName]="url">...</a>

这里的`attributeName`作为一个JavaScript表达式被动态执行，计算得到的值会被用作最终的参数。举例来说，如果你的组件实例中有一个数据属性`attributeName`，值为“href”，那么这个绑定就等价于`v-bind:href`。

##### 动态参数值的限制

动态参数中表达式的值应当是一个字符串，或者是 null。特殊值 null 意为显式移除该绑定。其他非字符串的值会触发警告。

##### 动态参数语法的限制

动态参数表达式因为某些字符的缘故有一些语法限制，比如空格和引号，在 HTML attribute 名称中都是不合法的。例如下面的示例：

	<!-- 这会触发一个编译器警告 -->
	<a :['foo' + bar]="value"> ... </a>

如果你需要传入一个复杂的动态参数，我们推荐使用**计算属性**替换复杂的表达式，也是 Vue 最基础的概念之一，我们很快就会讲到。

当使用 DOM 内嵌模板 (直接写在 HTML 文件里的模板) 时，我们需要避免在名称中使用大写字母，因为浏览器会强制将其转换为小写：

	<a :[someAttr]="value"> ... </a>

上面的例子将会在 DOM 内嵌模板中被转换为 `:[someattr]`。如果你的组件拥有 “someAttr” 属性而非 “someattr”，这段代码将不会工作。单文件组件内的模板不受此限制。

#### 修饰符

修饰符是以点开头的特殊后缀，表明指令需要以一些特殊的方式被绑定。例如 `.prevent` 修饰符会告知 `v-on` 指令对触发的事件调用 `event.preventDefault()`：

	<form @submit.prevent="onSubmit">...</form>

之后在讲到 v-on 和 v-model 的功能时，你将会看到其他修饰符的例子。

<div id="响应式基础"></div>

### 响应式基础
----
#### 声明响应式状态

**`ref()`** 的API定义为：

	function ref<T>(value: T): Ref<UnwrapRef<T>>

	interface Ref<T> {
		value: T
	}


在组合式API中，推荐使用`ref()`函数来声明响应式状态：

	import {ref} from 'vue'
	
	const count = ref(0)

`ref()`接受参数，将其包裹在一个带有`.value`属性的ref对象中返回：

	console.log(count) //{value:0}
	console.log(count.value) //0
	
	count.value++
	console.log(count.value) //1

要在组件模板中访问ref，请从组件`setup()`函数中声明并返回它们：

	import {ref} from 'vue'
	
	export default{
		//setup 是一个特殊的钩子，专门用于组合式API
		setup(){
			const count = ref(0)

			//将ref暴露给模板
			return {
				count
			}
		}
	}
	
	<div>{{count}}</div>

注意，在模板中使用 ref 时，我们不需要附加 `.value`。为了方便起见，当在模板中使用时，ref 会自动解包 (有一些注意事项)。

你也可以直接在事件监听器中改变一个 ref：

	 <button @click="count++">{{count}}</button>

对于更复杂的逻辑，我们可以在同一个作用域内声明更改ref的函数，并将它们作为方法与状态一起公开：

	import {ref} from 'vue'
	export default{
		setup(){
			const count = ref(0)
			
			function increment(){
				//在JavaScript中需要.value
				count.value++
			}
		}

		//不要忘记同时暴露 increment() 函数
		return{
			count,
			increment
		}
	}

然后，暴露的方法可以被用作事件监听器：

	<button @click="increment">{{count}}</button>

##### Script setup

在 `setup()` 函数中手动暴露大量的状态和方法非常繁琐。幸运的是，我们可以通过使用**单文件组件 (SFC)** 来避免这种情况。我们可以使用 `<script setup>` 来大幅度地简化代码：

	<script setup>
	import {ref} from 'vue'
	
	const count = ref(0)
	
	function increment(){
		count.value++
	}
	</script>

	<template>
		<button @click="increment">{{count}}</button>
	</template>

*tip*

*在指南的后续章节中，我们基本上都会在组合式 API 示例中使用单文件组件 + `<script setup>` 的语法，因为大多数 Vue 开发者都会这样使用。*

*如果你没有使用单文件组件，你仍然可以在 `setup()` 选项中使用组合式 API。*

##### 为什么要使用ref？

##### 深层响应性

Ref可以持有任何类型的值，包括深层嵌套的对象、数组或JavaScript内置的数据结构，比如`Map`。

Ref会使它的值具有深层响应性。这意味着即使改变嵌套对象或数组时，变化也会被检测到：

	import {ref} from 'vue'

	const obj = ref({
		nested:{count:0},
		arr:['foo','bar']
	})

	function mutateDeeply(){
		//以下都会按照期望工作
		obj.value.nested.count++
		obj.value.arr.push('bar')
	}

非原始值将通过`reactive()`转换为响应式代理。

也可以通过**shallow ref**来放弃深层响应。对于浅层ref，只有`.value`的访问会被追踪。浅层 ref 可以用于避免对大型数据的响应性开销来优化性能、或者有外部库管理其内部状态的情况。

##### DOM更新时机

当你修改了响应式状态时，DOM 会被自动更新。但是需要注意的是，DOM 更新不是同步的。Vue 会在“next tick”更新周期中缓冲所有状态的修改，以确保不管你进行了多少次状态修改，每个组件都只会被更新一次。

要等待 DOM 更新完成后再执行额外的代码，可以使用 nextTick() 全局 API：

	import {nextTick()} from 'vue'
	
	aysnc function increment(){
		count.value++
		await nextTick()
		//现在DOM已经更新了，以下是要执行的额外代码
		//....
	}

##### reactive()

还有另一种声明响应式状态的方式，即使用 `reactive()` API。与将内部值包装在特殊对象中的 ref 不同，`reactive()` 将使对象本身具有响应性：

	import {reactive} from 'vue'
	
	const state = reactive({count:0})

	<!-- 在模板中使用 -->
	<template>
		<<button @click="state.count++">
			{{ state.count }}
		</button>>
	</template>
	
响应式对象是 JavaScript 代理，其行为就和普通对象一样。不同的是，Vue 能够拦截对响应式对象所有属性的访问和修改，以便进行依赖追踪和触发更新。

`reactive()` 将深层地转换对象：当访问嵌套对象时，它们也会被 `reactive()` 包装。当 ref 的值是一个对象时，`ref()` 也会在内部调用它。与浅层 ref 类似，这里也有一个 `shallowReactive()` API 可以选择退出深层响应性。

###### Reactive Proxy vs. Original

值得注意的是，reactive() 返回的是一个原始对象的 Proxy，它和原始对象是不相等的：

	const raw = {}
	const proxy = reactive(raw)

	// 代理对象和原始对象不是全等的
	console.log(proxy === raw) // false

只有代理对象是响应式的，更改原始对象不会触发更新。因此，使用 Vue 的响应式系统的最佳实践是 **仅使用你声明对象的代理版本**。

为保证访问代理的一致性，对同一个原始对象调用 `reactive()` 会总是返回同样的代理对象，而对一个已存在的代理对象调用 `reactive()` 会返回其本身：

	// 在同一个对象上调用 reactive() 会返回相同的代理
	console.log(reactive(raw) === proxy) // true

	// 在一个代理上调用 reactive() 会返回它自己
	console.log(reactive(proxy) === proxy) // true

这个规则对嵌套对象也适用。依靠深层响应性，响应式对象内的嵌套对象依然是代理：

	const proxy = reactive({})

	const raw = {}
	proxy.nested = raw //代理对象内的嵌套对象依然是代理

	console.log(proxy.nested === raw) // false

###### reactive()的局限性

1.有限的值类型。

它只能用于对象类型（对象、数组和如Map、Set这样的集合类型），不能持有如string、number或boolean这样的原始类型。

2.不能替换整个对象。

由于vue的响应式跟踪是通过属性访问实现的，因此我们必须始终保持对响应式对象的相同引用。这意味着我们不能轻易地替换响应式对象，因为这样会导致与第一个引用的响应性连接丢失：

	let state = reactive({count:0})

	//上面的 ({ count: 0 }) 引用将不再被追踪 (响应性连接已丢失！)
	state = reactive({count:1})

3.对解构操作不友好。

当我们将响应式对象的原始类型属性解构为本地变量时，或者将该属性传递给函数时，我们将丢失响应性连接：

	const state = reactive({count:0})
	// 当解构时，count 已经与 state.count 断开连接
	let {count} = state
	// 不会影响原始的 state
	count++

	// 该函数接收到的是一个普通的数字
	// 并且无法追踪 state.count 的变化
	// 我们必须传入整个对象以保持响应性
	callSomeFunction(state.count)

由于这些限制，我们建议使用 `ref()` 作为声明响应式状态的主要 API。

#### 额外的ref解包细节

##### 作为reactive对象的属性

一个 ref 会在作为响应式对象的属性被访问或修改时自动解包。换句话说，它的行为就像一个普通的属性：

	const count = ref(0)
	const state = reactive({
		count
	})

	console.log(state.count) //0
	
	state.count = 1
	console.log(count.value) //1

如果将一个新的ref复制给一个关联了已有ref的属性，那么它会替换旧的ref：

	const otherCount = ref(2)
	
	state.count = otherCount
	console.log(state.count) //2
	// 原始 ref 现在已经和 state.count 失去联系
	console.log(count.value) //1

只有当嵌套在一个深层响应式对象内时，才会发生 ref 解包。当其作为浅层响应式对象的属性被访问时不会解包。

##### 数组和集合的注意事项

与reactive对象不同的是，当ref作为响应式数组或源生集合类型（如`Map`）中的元素被访问时，它不会被解包：

	const books = reactive([ref('Vue 3 Guide')])
	//这里需要.value
	console.log(books[0].value)

	const map = reacitve(new Map([['count',ref(0)]]))
	//这里需要.value
	console.log(map.get('count').value)

##### 在模板中解包的注意事项

在模板渲染上下文中，只有顶级的ref属性才会被解包。

	//count和obj都是顶级属性，但obj.id不是
	const count = ref(0)
	const obj = {id:ref(1)}


<div id="计算属性"></div>

### 计算属性
----
模板中的表达式虽然方便，但也只能用来做简单的操作。如果在模板中写太多的逻辑，会让模板变得臃肿，难以维护。比如这样一个包含嵌套数组的对象：

	const author = reactive({
		name:'John Doe',
		books:[
			'Vue2 - Advanced Guide',
			'Vue3 - Basic Guide',
			'Vue4 - The Mystery'
		]
	})
	
我们想根据`author`是否已有一些书籍来展示不同的信息：

	<p>Has published books:</p>
	<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>

如果在模板中需要不止一次这样的计算，我们可不想将这样的代码在模板里重复好多遍。因此我们推荐使用**计算属性**来描述依赖响应式状态的复杂逻辑。这是重构后的示例：

	<script setup>
	import {reactive, computed} from 'vue'

	const author = reactive({
		name:'John Doe',
		books:[
			'Vue2 - Advanced Guide',
			'Vue3 - Basic Guide',
			'Vue4 - The Mystery'
		]
	})

	//一个计算属性ref
	const pulishedBooksMessage = computed(() => {
		return author.books.length > 0 ? 'Yes' : 'No'
	})

	</script>

	<template>
		<p>Has published books:</p>
		<span>{{ pulishedBooksMessage }}</span>
	</teamplte>

#### 计算属性缓存 vs 方法

你可能注意到我们在表达式中像这样调用一个函数也会获得和计算属性相同的结果：

	// 组件中
	function calculateBooksMessage() {
		return author.books.length > 0 ? 'Yes' : 'No'
	}

	// 模板中
	<p>{{ calculateBooksMessage() }}</p>

若我们将同样的函数定义为一个方法而不是计算属性，两种方式在结果上确实是完全相同的，然而，不同之处在于**计算属性值会基于其响应式依赖被缓存**。一个计算属性仅会在其响应式依赖更新时才重新计算。这意味着只要 `author.books` 不改变，无论多少次访问 publishedBooksMessage 都会立即返回先前的计算结果，而不用重复执行 getter 函数。

这也解释了为什么下面的计算属性永远不会更新，因为 Date.now() 并不是一个响应式依赖：

	const now = computed(() => Date.now())

相比之下，方法调用总是会在重渲染发生时再次执行函数。

为什么需要缓存呢？想象一下我们有一个非常耗性能的计算属性 list，需要循环一个巨大的数组并做许多计算逻辑，并且可能也有其他计算属性依赖于 list。没有缓存的话，我们会重复执行非常多次 list 的 getter，然而这实际上没有必要！如果你确定不需要缓存，那么也可以使用方法调用。


#### 避免直接修改计算属性值

从计算属性返回的值是派生状态。可以把它看作是一个“临时快照”，每当源状态发生变化时，就会创建一个新的快照。更改快照是没有意义的，因此计算属性的返回值应该被视为只读的，并且永远不应该被更改——应该更新它所依赖的源状态以触发新的计算。

<div id="类与样式的绑定"></div>

### 类与样式的绑定

数据绑定的常见需求场景是操纵元素的CSS class列表和内联样式因为`class`和`style`都是attribute，我们可以和其他attribute一样使用`v-bind`将它们和动态的字符串绑定。但是，处理复杂绑定时，通过拼接生成字符串是麻烦且容易出错的。因此，Vue专门为`class`和`style`的`v-bind`用法提供了特殊的功能增强。除了字符串外表达式的值也可以是对象或数组。

----

#### 绑定 HTML class

##### 绑定对象

我们可以给 `v-bind:class` 传递一个对象来动态切换class：
	
	<!-- active 是否存在取决于数据属性 isActive 的真假值 -->
	<div :class="{ active : isActive }"></div>

你可以在对象中写多个字段来操作多个 class。此外，:class 指令也可以和一般的 class attribute 共存。举例来说，下面这样的状态：

	//组件中
	const isActive = ref(true)
	const hasError = ref(false)
	
	//模板中
	<!-- 渲染结果将是<div class="static active"></div> -->
	<div class="static" :class="{ active: isActive, 'text-danger': hasError }"></div>

绑定的对象并不一定需要写成内联字面量的形式，也可以直接绑定一个对象：

	const classObject = reactive({
		active: true,
		'text-danger': false
	})

	...
	...
	<div :class="classObject"></div> <!-- 渲染结果：<div class="active"></div> -->

我们也可以绑定一个返回对象的计算属性。这是一个常见且很有用的技巧：

	const isActive = ref(true)
	const error = ref(null)
	
	const classObject = computed(() => {
		active : isActive.value && !error.value,
		'text-danger' : error.value && error.value.type === 'fatal'
	})
	
	//在template中
	<div :class="classObject"></div>

##### 绑定数组

我们可以给`:class`绑定一个数组来渲染多个CSS class：

	const activeClass = ref('active')
	const errorClass = ref('text-danger')

	<div :class="[activeClass, errorClass]"></div><!-- 渲染结果：<div class="active text-danger"></div> -->

##### 在组件上使用

对于只有一个根元素的组件，当使用了class attribute时，这些class会被添加到根元素上并与该元素上已有的class合并。

举例来说，如果你声明了一个组件名叫 MyComponent，模板如下：

	<!-- 子组件模板 -->
	<p class="foo bar">Hi!</p>

在使用时添加一些 class：

	<!-- 在使用组件时 -->
	<MyComponent class="baz boo" />

渲染出的HTML为：

	<p class="foo bar baz boo">Hi!</p>

Class 的绑定也是同样：

	<MyComponent :class="{ active: isActive }" />

当 isActive 为真时，被渲染的 HTML 会是：

	<p class="foo bar active">Hi!</p>

如果你的组件有多个根元素，你将需要指定哪个根元素来接收这个 class。你可以通过组件的 `$attrs` 属性来实现指定：

	<!-- MyComponent 模板使用 $attrs 时 -->
	<p :class="$attrs.class">Hi!</p>
	<span>This is a child component</span>

	<MyComponent class="baz" />

这将被渲染为：

	<p class="baz">Hi!</p>
	<span>This is a child component</span>

你可以在透传 Attribute 一章中了解更多组件的 attribute 继承的细节。

##### 绑定内联样式

###### 绑定对象

`:style`支持绑定JavaScript的对象值，对应的是HTML元素的`style`属性。

直接绑定一个样式对象可以使模板更加简洁：

	const styleObject = reactive({
		color:'red',
		fontSize:'13px'
	})

	<div :style="styleObject">

###### 绑定数组

我们还可以给 `:style` 绑定一个包含多个样式对象的数组。这些对象会被合并后渲染到同一元素上：

	<div :style="[baseStyles, overridingStyles]"></div>

###### 自动前缀

当你在 `:style` 中使用了需要浏览器特殊前缀的 CSS 属性时，Vue 会自动为他们加上相应的前缀。Vue 是在运行时检查该属性是否支持在当前浏览器中使用。如果浏览器不支持某个属性，那么将尝试加上各个浏览器特殊前缀，以找到哪一个是被支持的。

###### 样式多值

你可以对一个样式属性提供多个 (不同前缀的) 值，举例来说：

	<div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>

数组仅会渲染浏览器支持的最后一个值。在这个示例中，在支持不需要特别前缀的浏览器中都会渲染为 `display: flex`。

<div id="条件渲染"></div>

### 条件渲染
----

#### v-if

`v-if`指令用于条件性的渲染一块内容这块内容只会在指令的表达式返回真值时才被渲染。

	<h1 v-if="awesome">Vue is awesome</h1>

#### v-else

`v-else`为`v-if`添加一个else区块：

	<button @click="awesome = !awesome">Toggle</button>

	<h1 v-if="awesome">Vue is awesome</h1>
	<h1 v-else>Oh no</h1>

一个 v-else 元素必须跟在一个 v-if 或者 v-else-if 元素后面，否则它将不会被识别。

#### v-else-if

顾名思义，v-else-if 提供的是相应于 v-if 的“else if 区块”。它可以连续多次重复使用，和 v-else 类似，一个使用 v-else-if 的元素必须紧跟在一个 v-if 或一个 v-else-if 元素后面。

	<div v-if="type === 'A'">
	A
	</div>
	<div v-else-if="type === 'B'">
	B
	</div>
	<div v-else-if="type === 'C'">
	C
	</div>
	<div v-else>
	Not A/B/C
	</div>

#### template上的v-if

因为 v-if 是一个指令，他必须依附于某个元素。但如果我们想要切换不止一个元素呢？在这种情况下我们可以在一个 `<template>` 元素上使用 v-if，这只是一个不可见的包装器元素，最后渲染的结果并不会包含这个 `<template>` 元素。

	<template v-if="ok">
		<h1>Title</h1>
		<p>Paragraph 1</p>
		<p>Paragraph 2</p>
	</template>

v-else 和 v-else-if 也可以在 `<template>` 上使用。

#### v-show

另一个可以用来按条件显示一个元素的指令是 v-show。其用法基本一样：

	<h1 v-show="ok">Hello!</h1>

不同之处在于 v-show 会在 DOM 渲染中保留该元素；v-show 仅切换了该元素上名为 display 的 CSS 属性。

v-show 不支持在 `<template>` 元素上使用，也不能和 v-else 搭配使用。

#### v-show vs. v-if

v-if 是“真实的”按条件渲染，因为它确保了在切换时，条件区块内的事件监听器和子组件都会被销毁与重建。v-if 也是惰性的：如果在初次渲染时条件值为 false，则不会做任何事。条件区块只有当条件首次变为 true 时才被渲染。

相比之下，v-show 简单许多，元素无论初始条件如何，始终会被渲染，只有 CSS display 属性会被切换。

总的来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要频繁切换，则使用 v-show 较好；如果在运行时绑定条件很少改变，则 v-if 会更合适。

<div id="列表渲染"></div>

### 列表渲染

#### v-for

**警告**：

同时使用 v-if 和 v-for 是不推荐的，因为这样二者的优先级不明显。请查看风格指南获得更多信息。当 v-if 和 v-for 同时存在于一个元素上的时候，v-if 会首先被执行。请查看列表渲染指南获取更多细节。

我们可以使用 v-for 指令基于一个数组来渲染一个列表。

	//在js中
	const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
	
	//在template中
	<li v-for="item in items">
		{{ item.message }}
	</li>

在 v-for 块中可以完整地访问父作用域内的属性和变量。v-for 也支持使用可选的第二个参数表示当前项的位置索引。

	const parentMessage = ref('Parent')
	const items = ref([{ message: 'Foo' }, { message: 'Bar' }])

	<li v-for="(item, index) in items">
		{{parentMessage}} - {{index}} - {{item.message}}
	</li>

#### v-for 与对象

你也可以使用 v-for 来遍历一个对象的所有属性。遍历的顺序会基于对该对象调用 Object.keys() 的返回值来决定。

	const myObject = reactive({
		title: 'How to do lists in Vue',
		author: 'Jane Doe',
		publishedAt: '2016-04-10'
	})

	<ul>
		<li v-for="value in myObject">
			{{value}}
		</li>
	</ul>

可以通过提供第二个参数表示属性名 (例如 key),第三个参数表示位置索引。

	<li v-for="(value, key, index) in myObject">
		{{ index }}. {{ key }}: {{ value }}
	</li>

#### 在v-for里使用范围值

v-for 可以直接接受一个整数值。会将该模板基于 1...n 的取值范围重复多次。注意此处 n 的初值是从 1 开始而非 0。

	<span v-for="n in 10">{{ n }}</span>

#### template中的v-for

与模板上的 v-if 类似，你也可以在 `<template>` 标签上使用 v-for 来渲染一个包含多个元素的块。例如：

	<ul>
		<template v-for="item in items">
			<li>{{ item.msg }}</li>
			<li class="divider" role="presentation"></li>
		</template>
	</ul>

#### v-for 与 v-if

当它们同时存在于一个节点上时，v-if 比 v-for 的优先级更高。这意味着 v-if 的条件将无法访问到 v-for 作用域内定义的变量别名：

	<!--这会抛出一个错误，因为属性 todo 此时没有在该实例上定义 -->
	<li v-for="todo in todos" v-if="!todo.isComplete">
		{{ todo.name }}
	</li>

在外新包装一层 `<template>` 再在其上使用 v-for 可以解决这个问题 (这也更加明显易读)：

	<template v-for="todo in todos">
		<li v-if="!todo.isComplete">
			{{ todo.name }}
		</li>
	</template>

#### 通过Key管理状态

Vue 默认按照“就地更新”的策略来更新通过 v-for 渲染的元素列表。当数据项的顺序改变时，Vue 不会随之移动 DOM 元素的顺序，而是就地更新每个元素，确保它们在原本指定的索引位置上渲染。

默认模式是高效的，但**只适用于列表渲染输出的结果不依赖子组件状态或者临时 DOM 状态 (例如表单输入值) 的情况**。

为了给 Vue 一个提示，以便它可以跟踪每个节点的标识，从而重用和重新排序现有的元素，你需要为每个元素对应的块提供一个唯一的 key attribute：

	<div v-for="item in items" :key="item.id"></div>

当你使用 `<template v-for>` 时，key 应该被放置在这个 `<template>` 容器上：

	<template v-for="todo in todos" :key="todo.name">
		<li>{{ todo.name }}</li>
	</template>


#### 在组件中使用v-for

我们可以直接在组件上使用 v-for，和在一般的元素上使用没有区别 (别忘记提供一个 key)：

	<MyComponent v-for="item in items" :key="item.id" />

但是，这不会自动将任何数据传递给组件，因为组件有自己独立的作用域。为了将迭代后的数据传递到组件中，我们还需要传递 props：

	<MyComponent
		v-for="(item, index) in items" :key="item.id"
		:item="item"
		:index="index"
	/>

不自动将 item 注入组件的原因是，这会使组件与 v-for 的工作方式紧密耦合。明确其数据的来源可以使组件在其他情况下重用。



#### 数组变化侦测

Vue 能够侦听响应式数组的变更方法，并在它们被调用时触发相关的更新。这些变更方法包括：

- push()
- pop()
- shift()
- unshift()
- splice()
- sort()
- reverse()

##### 替换一个数组

##### 展示过滤或排序后的结果

<div id="事件处理"></div>

### 事件处理
----

#### 监听事件

我们可以使用 v-on 指令 (简写为 @) 来监听 DOM 事件，并在事件触发时执行对应的 JavaScript。用法：

`v-on:click="handler" 或 @click="handler"`

事件处理器（handler）的值可以是：

1.内联事件处理器：事件被触发时执行的内联JavaScript语句（与onclick类似）。

2.方法事件处理器：一个指向组件上定义的方法的属性名或是路径。

##### 内联事件处理器

内联事件处理器应用于简单场景，如：

	const count = ref(0)

	<button @click="count++">Add 1</button>
	<p>Count is:{{ count }}</p>


##### 方法事件处理器

随着事件逻辑变得愈发复杂，内联代码的方式不够灵活。因此v-on可以接受一个方法名或对某个方法的调用。

	<script setup>
		import { ref } from 'vue'

		const name = ref('Vue.js')

		function greet(event){
			alert('Hello' ${name.value})
			//event 是DOM原生事件
			if(event){
				alert(event.target.tagName)
			}
		}
	</script>

	<template>
		<button @click="greet">Greet</button>
	</template>

方法事件处理器会自动接收原生 DOM 事件并触发执行。在上面的例子中，我们能够通过被触发事件的 event.target.tagName 访问到该 DOM 元素。

###### 方法与内联事件判断

模板编译器会通过检查 v-on 的值是否是合法的 JavaScript 标识符或属性访问路径来断定是何种形式的事件处理器。举例来说，foo、foo.bar 和 foo['bar'] 会被视为方法事件处理器，而 foo() 和 count++ 会被视为内联事件处理器。

##### 在内联处理器中调用方法

我们可以向方法传入自定义参数以代替原生事件：

	function say(message){
		alert(message)
	}

	<button @click="say('hello')">Alert hello</button>
	<button @click="say('bye')">Alert bye</button>

#### 在内联事件处理器中访问事件参数

有时我们需要在内联事件处理器中访问原生DOM事件。这时可以向该处理器方法传入一个特殊的$event变量，或者使用内联箭头函数：

	function warn(message, event){
		//这里可以访问原生事件
		if(event){
			event.preventDefault()
		}
		alert(message)
	}

	<!-- 使用特殊的$event变量 -->
	<button @click="warn('Form cannot be submitted yet.', $event)">Submit</button>

	<!-- 使用内联箭头函数 -->
	<button @click="(event) => warn('Form cannot be submitted yet.', event)">Submit</button>


#### 事件修饰符

在处理事件时调用 event.preventDefault() 或 event.stopPropagation() 是很常见的。尽管我们可以直接在方法内调用，但如果方法能更专注于数据逻辑而不用去处理 DOM 事件的细节会更好。

为解决这一问题，Vue 为 v-on 提供了事件修饰符。修饰符是用 . 表示的指令后缀，包含以下这些：

- .stop
- .prevent
- .self
- .capture
- .once
- .passive

示例代码如下：

	<!-- 单击事件将停止传递 -->
	<a @click.stop="doThis"></a>
	
	<!-- 提交事件将不再重新加载页面 -->
	<form @submit.prevent="onSubmit"></form>
	
	<!-- 修饰语可以使用链式书写 -->
	<a @click.stop.prevent="doThat"></a>
	
	<!-- 也可以只有修饰符 -->
	<form @submit.prevent></form>
	
	<!-- 仅当 event.target 是元素本身时才会触发事件处理器 -->
	<!-- 例如：事件处理器不来自子元素 -->
	<div @click.self="doThat">...</div>

.capture、.once 和 .passive 修饰符与原生 addEventListener 事件相对应：

	<!-- 添加事件监听器时，使用 `capture` 捕获模式 -->
	<!-- 例如：指向内部元素的事件，在被内部元素处理前，先被外部处理 -->
	<div @click.capture="doThis">...</div>
	
	<!-- 点击事件最多被触发一次 -->
	<a @click.once="doThis"></a>
	
	<!-- 滚动事件的默认行为 (scrolling) 将立即发生而非等待 `onScroll` 完成 -->
	<!-- 以防其中包含 `event.preventDefault()` -->
	<div @scroll.passive="onScroll">...</div>

.passive 修饰符一般用于触摸事件的监听器，可以用来改善移动端设备的滚屏性能。

*TIP:请勿同时使用 .passive 和 .prevent，因为 .passive 已经向浏览器表明了你不想阻止事件的默认行为。如果你这么做了，则 .prevent 会被忽略，并且浏览器会抛出警告。*

#### 按键修饰符

在监听键盘事件时，我们经常需要检查特定的按键。Vue 允许在 v-on 或 @ 监听按键事件时添加按键修饰符。

	<!-- 仅在 `key` 为 `Enter` 时调用 `submit` -->
	<input @keyup.enter="submit" />

你可以直接使用 KeyboardEvent.key 暴露的按键名称作为修饰符，但需要转为 kebab-case 形式。

##### 按键别名

Vue 为一些常用的按键提供了别名：

- .enter
- .tab
- .delete (捕获Delete和Backspace两个按键)
- .esc
- .space
- .up
- .down
- .left
- .right

##### 系统按键修饰符

你可以使用以下系统按键修饰符来触发鼠标或键盘事件监听器，只有当按键被按下时才会触发。

- .alt
- .ctrl
- .shift
- .meta

注意：在windows键盘上，.meta是Windows键。

	<!-- Alt + Enter -->
	<input @keyup.alt.enter="clear" />
	
	<!-- Ctrl + 点击 -->
	<div @click.ctrl="doSomething">Do something</div>

*TIP:请注意，系统按键修饰符和常规按键不同。与 keyup 事件一起使用时，该按键必须在事件发出时处于按下状态。换句话说，keyup.ctrl 只会在你仍然按住 ctrl 但松开了另一个键时被触发。若你单独松开 ctrl 键将不会触发。*

##### .exact修饰符

.exact 修饰符允许控制触发一个事件所需的确定组合的系统按键修饰符。

	<!-- 当按下 Ctrl 时，即使同时按下 Alt 或 Shift 也会触发 -->
	<button @click.ctrl="onClick">A</button>
	
	<!-- 仅当按下 Ctrl 且未按任何其他键时才会触发 -->
	<button @click.ctrl.exact="onCtrlClick">A</button>
	
	<!-- 仅当没有按下任何系统按键时触发 -->
	<button @click.exact="onClick">A</button>

##### 鼠标按键修饰符

- .left
- .middle
- .right

这些修饰符将处理程序限定为由特定鼠标按键触发的事件。

<div id="表单输入绑定"></div>

### 表单输入绑定
----

在前端处理表单时，将表单输入框的内容同步给JavaScript中相应的变量。手动连接值绑定和更改事件监听器可能会很麻烦：

	<input :value="text" @input="event => text = event.target.value" />

v-model 指令帮我们简化了这一步骤:

	<input v-model="text" />

另外，v-model 还可以用于各种不同类型的输入， `<textarea>`、`<select>`元素。它会根据所使用的元素自动使用对应的DOM属性和事件组合：

- 文本类型的`<input>`和`<textarea>`会绑定value property并侦听input事件；
- `<input type="checkbox">` 和 `<input type="radio">`会绑定 checked property并侦听change事件；
- `<select>` 会绑定value property 并侦听change事件。

注意：v-model 会忽略任何表单元素上初始的 value、checked 或 selected attribute。它将始终将当前绑定的 JavaScript 状态视为数据的正确来源。你应该在 JavaScript 中使用响应式系统的 API来声明该初始值。

#### 基本用法

##### 文本

	<p>Message is: {{ message }}</p>
	<input v-model="message" placeholder="edit me" />

##### 多行文本

	<span>Multiline message is:</span>
	<p style="white-space: pre-line;">{{ message }}</p>
	<textarea v-model="message" placeholder="add multiple lines"></textarea>


##### 复选框

单一复选框，绑定布尔值类型：

	<input type="checkbox" id="ckbx-demo" v-model="checked" />
	<lable for="ckbx-demo">{{ checked }}</lable>

将多个复选框绑定到同一个数组或集合的值：

	const checkedNames = ref([])
	
	<div>Checked names: {{ checkedNames }}</div>

	<input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
	<label for="jack">Jack</label>
	
	<input type="checkbox" id="john" value="John" v-model="checkedNames">
	<label for="john">John</label>
	
	<input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
	<label for="mike">Mike</label>

##### 单选按钮

	<div>Picked: {{ picked }}</div>
	
	<input type="radio" id="one" value="One" v-model="picked" />
	<label for="one">One</label>
	
	<input type="radio" id="two" value="Two" v-model="picked" />
	<label for="two">Two</label>

##### 选择器

	<div>Selected: {{ selected }}</div>
	
	<select v-model="selected">
	  <option disabled value="">Please select one</option>
	  <option>A</option>
	  <option>B</option>
	  <option>C</option>
	</select>

单个选择器：

	<script setup>
	import { ref } from 'vue'
	
	const selected = ref('')
	</script>
	
	<template>
	  <div>Selected: {{ selected }}</div>
	  <select v-model="selected">
	    <option disabled value="">请选一个选项</option>
	    <option>集团</option>
	    <option>丽枫</option>
	    <option>凯里亚德</option>
	    <option>康铂</option>
	  </select>
	</template>

多选（值绑定到一个数组）：

	<script setup>
	import { ref } from 'vue'
	
	const selected = ref([])
	</script>
	
	<template>
	  <div>Selected: {{ selected }}</div>
	  <select v-model="selected" multiple>
	    <option>集团</option>
	    <option>丽枫</option>
	    <option>凯里亚德</option>
	    <option>康铂</option>
	  </select>
	</template>

选择器的选项可以用v-for动态渲染：

	const selected = ref('')

	const options = ref([
		{text: 'One', value: 'A'},
		{text: 'Two', value: 'B'},
		{text: 'Three', value: 'C'},
	])

	<select v-model="selected">
		<option v-for=" option in options" :value="option.value">{{ option.text }}</option>
	</select>

##### 值绑定

对于单选按钮，复选框和选择器选项，v-model 绑定的值通常是静态的字符串 (或者对复选框是布尔值)。

	<!-- `picked` 在被选择时是字符串 "a" -->
	<input type="radio" v-model="picked" value="a" />
	
	<!-- `toggle` 只会为 true 或 false -->
	<input type="checkbox" v-model="toggle" />
	
	<!-- `selected` 在第一项被选中时为字符串 "abc" -->
	<select v-model="selected">
	  <option value="abc">ABC</option>
	</select>

但有时我们可能希望将该值绑定到当前组件实例上的动态数据。这可以通过使用 v-bind 来实现。此外，使用 v-bind 还使我们可以将选项值绑定为非字符串的数据类型。

	<input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />

true-value 和 false-value 是 Vue 特有的 attributes，仅支持和 v-model 配套使用。这里 toggle 属性的值会在选中时被设为 'yes'，取消选择时设为 'no'。你同样可以通过 v-bind 将其绑定为其他动态值：

	<input type="checkbox" v-model="toggle" :true-value="dynamicTrueValue" :false-value="dynamicFalseValue" />

下列代码是使用事件+动态值绑定来达到单选框动态变化的示例：

	<script setup>
	import { ref } from 'vue'
	
	//用于单选渲染的输入框内容
	const radioInput = ref('')
	//单选数组
	const radios = ref([])
	//选择结果的值
	const pick = ref('')
	
	//单选框处理器
	function radioHandler(input){
		//将输入以，号进行分组
		radios.value = input.split(",")
	}
	</script>
	
	<template>
	  <p>
	  	<lable>输入一个选项值：</lable>
		<!-- 利用v-model完成值绑定和数据监听，利用@input来完成onChange事件触发函数调用 -->
		<input type="text" placeholder="多个选项以,分隔" v-model="radioInput" @input="radioHandler(radioInput)" />
		<!-- 或使用button.click事件来触发函数调用 -->
		<button @click="radioHandler(radioInput)">确认</button>
	  </p>
	  <!-- 依赖div来使用v-for进行动态单选框渲染 -->
	  <div v-for="radio in radios">
		<!-- 利用v-bind:value来绑定value动态值 -->
	    <input type="radio" v-model="pick" :value="radio"/><lable>{{ radio }}</lable>
	  </div>
	  <div>Picked: {{ pick }}</div>
	</template>

##### 修饰符

.lazy

默认情况下，v-model 会在每次 input 事件后更新数据 (IME 拼字阶段的状态例外)。你可以添加 lazy 修饰符来改为在每次 change 事件后更新数据：

	<!-- 在 "change" 事件后同步更新而不是 "input" -->
	<input v-model.lazy="msg" />

.number

如果你想让用户输入自动转换为数字，你可以在 v-model 后添加 .number 修饰符来管理输入：

	<input v-model.number="age" />

如果该值无法被 parseFloat() 处理，那么将返回原始值。number 修饰符会在输入框有 type="number" 时自动启用。

.trim

如果你想要默认自动去除用户输入内容中两端的空格，你可以在 v-model 后添加 .trim 修饰符：

	<input v-model.trim="msg" />

<div id="生命周期"></div>

### 生命周期

每个 Vue 组件实例在创建时都需要经历一系列的初始化步骤，比如设置好数据侦听，编译模板，挂载实例到 DOM，以及在数据改变时更新 DOM。在此过程中，它也会运行被称为生命周期钩子的函数，让开发者有机会在特定阶段运行自己的代码。

----

#### 注册周期钩子

比如`onMounted`钩子可以用来在组件完成初始渲染并创建DOM节点后运行代码：

	<script setup>
	import { onMounted } from 'vue'
	
	onMounted(() => {
	  console.log(`the component is now mounted.`)
	})
	</script>

还有其他一些钩子，会在实例生命周期的不同阶段被调用，最常用的是 `onMounted`、`onUpdated` 和 `onUnmounted`。所有生命周期钩子的完整参考及其用法请参考 API 索引。

当调用 `onMounted` 时，Vue 会自动将回调函数注册到当前正被初始化的组件实例上。这意味着这些钩子应当在组件初始化时被同步注册。

<div id="侦听器"></div>

### 侦听器
----

#### 基本示例
计算属性允许我们声明性地计算衍生值。然而在有些情况下，我们需要在状态变化时执行一些“副作用”：例如更改 DOM，或是根据异步操作的结果去修改另一处的状态。

在组合式 API 中，我们可以使用 `watch` 函数在每次响应式状态发生变化时触发回调函数：

	<script setup>
	import { ref, watch } from 'vue'
	
	const question = ref('')
	const answer = ref('Questions usually contain a question mark. ;-)')
	const loading = ref(false)
	
	// 可以直接侦听一个 ref
	watch(question, async (newQuestion, oldQuestion) => {
	  if (newQuestion.includes('?')) {
	    loading.value = true
	    answer.value = 'Thinking...'
	    try {
	      const res = await fetch('https://yesno.wtf/api')
	      answer.value = (await res.json()).answer
	    } catch (error) {
	      answer.value = 'Error! Could not reach the API. ' + error
	    } finally {
	      loading.value = false
	    }
	  }
	})
	</script>
	
	<template>
	  <p>
	    Ask a yes/no question:
	    <input v-model="question" :disabled="loading" />
	  </p>
	  <p>{{ answer }}</p>
	</template>

#### 侦听数据源类型

watch 的第一个参数可以是不同形式的“数据源”：它可以是一个 ref (包括计算属性)、一个响应式对象、一个 getter 函数、或多个数据源组成的数组。

	const x = ref(0)
	const y = ref(0)
	
	// 单个 ref
	watch(x, (newX) => {
	  console.log(`x is ${newX}`)
	})
	
	// getter 函数
	watch(
	  () => x.value + y.value,
	  (sum) => {
	    console.log(`sum of x + y is: ${sum}`)
	  }
	)
	
	// 多个来源组成的数组
	watch([x, () => y.value], ([newX, newY]) => {
	  console.log(`x is ${newX} and y is ${newY}`)
	})

#### 深层侦听器

直接给 watch() 传入一个响应式对象，会隐式地创建一个深层侦听器——该回调函数在所有嵌套的变更时都会被触发：

	const obj = reactive({ count: 0 })
	
	watch(obj, (newValue, oldValue) => {
	  // 在嵌套的属性变更时触发
	  // 注意：`newValue` 此处和 `oldValue` 是相等的
	  // 因为它们是同一个对象！
	})
	
	obj.count++

**谨慎使用**

深度侦听需要遍历被侦听对象中的所有嵌套的属性，当用于大型数据结构时，开销很大。因此请只在必要时才使用它，并且要留意性能。

#### 即时回调的侦听器

watch 默认是懒执行的：仅当数据源变化时，才会执行回调。但在某些场景中，我们希望在创建侦听器时，立即执行一遍回调。举例来说，我们想请求一些初始数据，然后在相关状态更改时重新请求数据。

我们可以通过传入 immediate: true 选项来强制侦听器的回调立即执行：

	watch(
	  source,
	  (newValue, oldValue) => {
	    // 立即执行，且当 `source` 改变时再次执行
	  },
	  { immediate: true }
	)

#### 一次性侦听器

需要vue版本3.4+，每当被侦听源发生变化时，侦听器的回调就会执行。如果希望回调只在源变化时触发一次，请使用 once: true 选项。

	watch(
	  source,
	  (newValue, oldValue) => {
	    // 当 `source` 变化时，仅触发一次
	  },
	  { once: true }
	)

#### watchEffect()

侦听器的回调使用与源完全相同的响应式状态是很常见的。例如下面的代码，在每当 todoId 的引用发生变化时使用侦听器来加载一个远程资源：
	
	const todoId = ref(1)
	const data = ref(null)
	
	watch(
	  todoId,
	  async () => {
	    const response = await fetch(
	      `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
	    )
	    data.value = await response.json()
	  },
	  { immediate: true }
	)

我们可以用 `watchEffect` 函数 来简化上面的代码。watchEffect() 允许我们自动跟踪回调的响应式依赖。上面的侦听器可以重写为：

	watchEffect(async () => {
	  const response = await fetch(
	    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
	  )
	  data.value = await response.json()
	})

这个例子中，回调会立即执行，不需要指定 immediate: true。在执行期间，它会自动追踪 todoId.value 作为依赖（和计算属性类似）。每当 todoId.value 变化时，回调会再次执行。有了 watchEffect()，我们不再需要明确传递 todoId 作为源值。

对于这种只有一个依赖项的例子来说，watchEffect() 的好处相对较小。但是对于有多个依赖项的侦听器来说，使用 watchEffect() 可以消除手动维护依赖列表的负担。

此外，如果你需要侦听一个嵌套数据结构中的几个属性，watchEffect() 可能会比深度侦听器更有效，因为它将只跟踪回调中被使用到的属性，而不是递归地跟踪所有的属性。

*TIP: watchEffect 仅会在其同步执行期间，才追踪依赖。在使用异步回调时，只有在第一个 await 正常工作前访问到的属性才会被追踪。*

#### watch vs. watchEffect

watch 和 watchEffect 都能响应式地执行有副作用的回调。它们之间的主要区别是追踪响应式依赖的方式：

- watch 只追踪明确侦听的数据源。它不会追踪任何在回调中访问到的东西。另外，仅在数据源确实改变时才会触发回调。watch 会避免在发生副作用时追踪依赖，因此，我们能更加精确地控制回调函数的触发时机。
- watchEffect，则会在副作用发生期间追踪依赖。它会在同步执行过程中，自动追踪所有能访问到的响应式属性。这更方便，而且代码往往更简洁，但有时其响应性依赖关系会不那么明确。

#### 回调触发的时机

当你更改了响应式状态，它可能会同时触发 Vue 组件更新和侦听器回调。

类似于组件更新，用户创建的侦听器回调函数也会被批量处理以避免重复调用。例如，如果我们同步将一千个项目推入被侦听的数组中，我们可能不希望侦听器触发一千次。

默认情况下，侦听器回调会在父组件更新 (如有) 之后、所属组件的 DOM 更新之前被调用。这意味着如果你尝试在侦听器回调中访问所属组件的 DOM，那么 DOM 将处于更新前的状态。

##### Post Watchers

如果想在侦听器回调中能访问被 Vue 更新之后的所属组件的 DOM，你需要指明 flush: 'post' 选项：

	watch(source, callback, {
	  flush: 'post'
	})
	
	watchEffect(callback, {
	  flush: 'post'
	})


后置刷新的 watchEffect() 有个更方便的别名 watchPostEffect()：

	import { watchPostEffect } from 'vue'

	watchPostEffect(() => {
		//在 Vue 更新后执行
	})

##### 同步侦听器

你还可以创建一个同步触发的侦听器，它会在 Vue 进行任何更新之前触发：

	watch(source, callback, {
	  flush: 'sync'
	})
	
	watchEffect(callback, {
	  flush: 'sync'
	})

同步触发的 watchEffect() 有个更方便的别名 watchSyncEffect()：

	import { watchSyncEffect } from 'vue'
	
	watchSyncEffect(() => {
	  /* 在响应式数据变化时同步执行 */
	})

*谨慎使用：同步侦听器不会进行批处理，每当检测到响应式数据发生变化时就会触发。可以使用它来监视简单的布尔值，但应避免在可能多次同步修改的数据源 (如数组) 上使用。*

##### 停止侦听器

在 setup() 或 `<script setup>` 中用同步语句创建的侦听器，会自动绑定到宿主组件实例上，并且会在宿主组件卸载时自动停止。因此，在大多数情况下，你无需关心怎么停止一个侦听器。

一个关键点是，侦听器必须用同步语句创建：如果用异步回调创建一个侦听器，那么它不会绑定到当前组件上，你必须手动停止它，以防内存泄漏。如下方这个例子：

	<script setup>
	import { watchEffect } from 'vue'
	
	// 它会自动停止
	watchEffect(() => {})
	
	// ...这个则不会！
	setTimeout(() => {
	  watchEffect(() => {})
	}, 100)
	</script>

要手动停止一个侦听器，请调用 watch 或 watchEffect 返回的函数：

	const unwatch = watchEffect(() => {})

	// ...当该侦听器不再需要时
	unwatch()

注意，需要异步创建侦听器的情况很少，请尽可能选择同步创建。如果需要等待一些异步数据，你可以使用条件式的侦听逻辑：

	// 需要异步请求得到的数据
	const data = ref(null)
	
	watchEffect(() => {
	  if (data.value) {
	    // 数据加载后执行某些操作...
	  }
	})

<div id="模板引用"></div>

### 模板引用

虽然 Vue 的声明性渲染模型为你抽象了大部分对 DOM 的直接操作，但在某些情况下，我们仍然需要直接访问底层 DOM 元素。要实现这一点，我们可以使用特殊的 ref attribute：

	<input ref="input">

ref 是一个特殊的 attribute，和 v-for 章节中提到的 key 类似。它允许我们在一个特定的 DOM 元素或子组件实例被挂载后，获得对它的直接引用。这可能很有用，比如说在组件挂载时将焦点设置到一个 input 元素上，或在一个元素上初始化一个第三方库。

----

#### 访问模板引用

为了通过组合式API获得模板引用，需要声明一个匹配模板 ref attribute值的ref：

	<script setup>
	import { ref, onMounted } from 'vue'

	//声明一个ref来存放该元素的应用。必须和模板里的ref同名
	const input = ref(null)

	onMounted(() => {
		input.value.focus()
	})

	</script>

	<template>
		<input ref="input" />
	</template>

如果不使用`<script setup>`，需确保从`setup()`返回ref：

	export default{
		setup(){
			const input = ref(null)
			//...

			return {
				input
			}
		}
	}

注意，你只可以在**组件挂载**后才能访问模板引用。如果你想在模板中的表达式上访问 input，在初次渲染时会是 null。这是因为在初次渲染前这个元素还不存在呢！

如果你需要侦听一个模板引用ref的变化，确保考虑其值为null的情况：

	watchEffect(() => {
	if (input.value) {
		input.value.focus()
	} else {
		// 此时还未挂载，或此元素已经被卸载（例如通过 v-if 控制）
	}
	})

#### v-for中的模板引用

*需要v3.2.25及以上版本*

当在`v-for`中使用模板引用时，对应的 ref 中包含的值是一个数组，它将在元素被挂载后包含对应整个列表的所有元素：

	<script setup>
	import { ref, onMounted } from 'vue'

	const list = ref([1, 2, 3, 4])

	const itemRefs = ref([])

	onMounted(() => {
		alert(itemRefs.value.map(i => i.textContent))
	})
	</script>

	<template>
	<ul>
		<li v-for="item in list" ref="itemRefs">
		{{ item }}
		</li>
	</ul>
	</template>

应该注意的是，ref 数组并不保证与源数组相同的顺序。

#### 函数模板的引用

除了使用字符串值作名字，ref attribute 还可以绑定为一个函数，会在每次组件更新时都被调用。该函数会收到元素引用作为其第一个参数：

	<input :ref="(el) => { /* 将 el 赋值给一个数据属性或 ref 变量 */ }">

注意我们这里需要使用动态的 `:ref` 绑定才能够传入一个函数。当绑定的元素被卸载时，函数也会被调用一次，此时的 el 参数会是 null。你当然也可以绑定一个组件方法而不是内联函数。

#### 组件上的ref

模板引用也可以被用在一个子组件上。这种情况下引用中获得的值是组件实例：

	<script setup>
	import { ref, onMounted } from 'vue'
	import Child from './Child.vue'

	const child = ref(null)

	onMounted(() => {
		// child.value 是 <Child /> 组件的实例
	})
	</script>

	<template>
		<Child ref="child" />
	</template>

如果一个子组件使用的是选项式 API 或没有使用 `<script setup>`，被引用的组件实例和该子组件的 this 完全一致，这意味着父组件对子组件的每一个属性和方法都有完全的访问权。这使得在父组件和子组件之间创建紧密耦合的实现细节变得很容易，当然也因此，应该只在绝对需要时才使用组件引用。大多数情况下，你应该首先使用标准的 props 和 emit 接口来实现父子组件交互。

有一个例外的情况，使用了 `<script setup>` 的组件是默认私有的：一个父组件无法访问到一个使用了 `<script setup>` 的子组件中的任何东西，除非子组件在其中通过 defineExpose 宏显式暴露：

	<script setup>
	import { ref } from 'vue'

	const a = 1
	const b = ref(2)

	// 像 defineExpose 这样的编译器宏不需要导入
	defineExpose({
		a,
		b
	})
	</script>

当父组件通过模板引用获取到了该组件的实例时，得到的实例类型为 `{ a: number, b: number }` (ref 都会自动解包，和一般的实例一样)。



### 组件基础

组件允许我们将 UI 划分为独立的、可重用的部分，并且可以对每个部分进行单独的思考。在实际应用中，组件常常被组织成层层嵌套的树状结构。

这和我们嵌套 HTML 元素的方式类似，Vue 实现了自己的组件模型，使我们可以在每个组件内封装自定义内容与逻辑。Vue 同样也能很好地配合原生 Web Component。如果你想知道 Vue 组件与原生 Web Components 之间的关系，可以阅读此章节。

----

#### 定义一个组件

当使用构建步骤时，我们一般会将 Vue 组件定义在一个单独的 `.vue` 文件中，这被叫做单文件组件 (简称 SFC)：

	<script setup>
	import { ref } from 'vue'

	const count = ref(0)
	</script>

	<template>
	<button @click="count++">You clicked me {{ count }} times.</button>
	</template>

当不使用构建步骤时，一个 Vue 组件以一个包含 Vue 特定选项的 JavaScript 对象来定义：

	import { ref } from 'vue'

	export default {
	setup() {
		const count = ref(0)
		return { count }
	},
	template: `
		<button @click="count++">
		You clicked me {{ count }} times.
		</button>`
	// 也可以针对一个 DOM 内联模板：
	// template: '#my-template-element'
	}

这里的模板是一个内联的 JavaScript 字符串，Vue 将会在运行时编译它。你也可以使用 ID 选择器来指向一个元素 (通常是原生的 `<template>` 元素)，Vue 将会使用其内容作为模板来源。

上面的例子中定义了一个组件，并在一个 `.js` 文件里默认导出了它自己，但你也可以通过具名导出在一个文件中导出多个组件。

#### 使用组件

要使用一个子组件，我们需要在父组件中导入它。假设我们把计数器组件放在了一个叫做 `ButtonCounter.vue`的文件中，这个组件将会以默认导出的形式被暴露给外部。

	<script setup>
	import ButtonCounter from './ButtonCounter.vue'
	</script>

	<template>
	<h1>Here is a child component!</h1>
	<ButtonCounter />
	//组件可以被重用任意多次：
	<ButtonCounter />
	<ButtonCounter />
	</template>

通过 `<script setup>`，导入的组件都在模板中直接可用。

当然，你也可以全局地注册一个组件，使得它在当前应用中的任何组件上都可以使用，而不需要额外再导入。关于组件的全局注册和局部注册两种方式的利弊，我们放在了组件注册这一章节中专门讨论。

你会注意到，每当点击这些按钮时，每一个组件都维护着自己的状态，是不同的 count。这是因为每当你使用一个组件，就创建了一个新的**实例**。

在单文件组件中，推荐为子组件使用`PascalCase`（帕斯卡签名法，将多个单词连接在一起，首字母大写，不使用分隔符）的签名，以此来和原生的HTML元素作区分。虽然原生 HTML 标签名是不区分大小写的，但 Vue 单文件组件是可以在编译中区分大小写的。我们也可以使用 /> 来关闭一个标签。

如果你是直接在 DOM 中书写模板 (例如原生 `<template>` 元素的内容)，模板的编译需要遵从浏览器中 HTML 的解析行为。在这种情况下，你应该需要使用 kebab-case （短横线命名法，将多个单词用短横线连接，常用语CSS类名、文件名和URL） 形式并显式地关闭这些组件的标签。

	<!-- 如果是在 DOM 中书写该模板 -->
	<button-counter></button-counter>
	<button-counter></button-counter>
	<button-counter></button-counter>

#### 传递 props

如果我们正在构建一个博客，我们可能需要一个表示博客文章的组件。我们希望所有的博客文章分享相同的视觉布局，但有不同的内容。

这样的实现效果自然必须向组件中传递数据，例如文章标题，内容等。这就使用到了props。

props是一个特殊的attributes，可以在组件上声明注册。要传递给博客文章组件一个标题，必须在组件的props列表上声明它。这里要用到defineProps宏：

	<!-- BlogPost.vue -->
	<script>
	defineProps(['title'])
	</script>

	<template>
		<h4>{{ title }}</h4>
	</template>

`defineProps` 是一个仅 `<script setup>` 中可用的编译宏命令，并不需要显式地导入。声明的 props 会自动暴露给模板。defineProps 会返回一个对象，其中包含了可以传递给组件的所有 props：

	const props = defineProps(['title'])
	console.log(props.title)

如果没有使用 `<script setup>`，props 必须以 props 选项的方式声明，props 对象会作为 `setup()` 函数的第一个参数被传入：

	export default {
		props: ['title'],
		setup(props) {
    		console.log(props.title)
  		}
	}

一个组件可以有任意多的props，默认情况下，所有props都接受任意类型的值。

当一个 prop 被注册后，可以像这样以自定义 attribute 的形式传递数据给它：

	<BlogPost title="My journey with Vue" />
	<BlogPost title="Blogging with Vue" />
	<BlogPost title="Why Vue is so fun" />

在实际应用中，我们可能在父组件中会有如下的一个博客文章数组：

	const posts = ref([
		{ id: 1, title: 'My journey with Vue' },
		{ id: 2, title: 'Blogging with Vue' },
		{ id: 3, title: 'Why Vue is so fun' }
	])

这种情况下就可以用v-for来进行渲染：

	<BlogPost v-for="post in posts" :key="post.id" :title="post.title" />

留意是如何使用 v-bind 来传递动态 prop 值的。当事先不知道要渲染的确切内容时，这一点特别有用。

#### 监听事件

继续关注 `<BlogPost>` 组件。我们会发现有时候它需要与父组件进行交互。例如，要在此处实现无障碍访问的需求，将博客文章的文字能够放大，而页面的其余部分仍使用默认字号。

在父组件中，我们可以添加一个 postFontSize ref 来实现这个效果：

	<script setup>
	import { ref } from 'vue'
	
	const posts = ref([
	/* ... */
	])

	const postFontSize = ref(1)
	</script>

	//在模板中用它来控制所有博客文章的字体大小
	<template>
		<div :style="{ fontSize: postFontSize + 'em' }">
			<BlogPost v-for="post in posts" :key="post.id" :title="post.title" />
		</div>
	</template>

之后，给`<BlogPost>`组件添加一个按钮：

	<!-- BlogPost.vue，省略了script -->
	<template>
		<div class="blog-post">
			<h4>{{ title }}</h4>
			<button>Enlarge text</button>
		</div>
	</template>

这个按钮目前还没做任何事情，我们想要点击这个按钮来告诉父组件它应该放大所有博客文章的文字。要解决这个问题，组件实例提供了一个自定义事件。父组件可以通过`v-on`或`@`来选择性地监听子组件上抛的事件，就像监听DOM原生事件那样：

	//父组件
	<BlogPost @enlarge-text="postFontSize += 0.1"/>

子组件可以通过调用内置的 `$emit` 方法，通过传入事件名称来抛出一个事件：

	<!-- BlogPost.vue, 省略了 <script> -->
	<template>
		<div class="blog-post">
			<h4>{{ title }}</h4>
			<!-- emit一个事件，名字为：enlarge-text -->
			<button @click="$emit('enlarge-text')">Enlarge text</button>
		</div>
	</template>

因为有了 `@enlarge-text="postFontSize += 0.1"` 的监听，父组件会接收这一事件，从而更新 `postFontSize` 的值。

我们可以通过 defineEmits 宏来声明需要抛出的事件：

	<!-- BlogPost.vue -->
	<script setup>
	defineProps(['title'])
	defineEmits(['enlarge-text'])
	</script>

这声明了一个组件可能触发的所有事件，还可以对事件的参数进行验证。同时，这还可以让 Vue 避免将它们作为原生事件监听器隐式地应用于子组件的根元素。

和 defineProps 类似，defineEmits 仅可用于 `<script setup>` 之中，并且不需要导入，它返回一个等同于 `$emit` 方法的 emit 函数。它可以被用于在组件的 `<script setup>` 中抛出事件，因为此处无法直接访问 `$emit`：

	<script setup>
	const emit = defineEmits(['enlarge-text'])

	emit('enlarge-text')
	</script>

如果你没有在使用 `<script setup>`，你可以通过 emits 选项定义组件会抛出的事件。你可以从 `setup()` 函数的第二个参数，即 setup 上下文对象上访问到 emit 函数：

	export default {
		emits: ['enlarge-text'],
		setup(props, ctx) {
			ctx.emit('enlarge-text')
		}
	}

#### 通过插槽来分配内容

一些情况下我们会希望能和 HTML 元素一样向组件中传递内容：

	<AlertBox>
		Something bad happend.
	</AlertBox>

通过vue在子组件中用`<slot>`元素实现，`<slot>`作为一个占位符，父组件传递进来的内容就会渲染在这里：

	<template>
	<div class="alert-box">
		<strong>This is an Error for Demo Purposes</strong>
		<slot />
	</div>
	</template>

	<style scoped>
	.alert-box {
	/* ... */
	}
	</style>


#### 动态组件

有些场景需要在两个组件间来回切换，比如Tab界面：

	<script setup>
	import Home from './Home.vue'
	import Archive from './Archive.vue'
	import { ref } from 'vue'

	const currentTab = ref('Home')

	const tabs = {
		Home,
		Archive
	}
	</script>

	<template>
		<div class="demo">
			<button v-for="(i,tab) in tabs" :key="tab" 
			:class="['tab-button', {active: currentTab == tab}]"
			@click="currentTab = tab"
			>
				{{ tab }}
			</button>
			<!-- component元素和is attribute 绑定实现：currentTab 改变时组件也改变 -->
			<component :is="tabs[currentTab]" class="tab"></component>
		</div>
	</template>

	<style>
	.demo {
		font-family: sans-serif;
		border: 1px solid #eee;
		border-radius: 2px;
		padding: 20px 30px;
		margin-top: 1em;
		margin-bottom: 40px;
		user-select: none;
		overflow-x: auto;
	}

	.tab-button {
		padding: 6px 10px;
		border-top-left-radius: 3px;
		border-top-right-radius: 3px;
		border: 1px solid #ccc;
		cursor: pointer;
		background: #f0f0f0;
		margin-bottom: -1px;
		margin-right: -1px;
	}
	.tab-button:hover {
		background: #e0e0e0;
	}
	.tab-button.active {
		background: #e0e0e0;
	}
	.tab {
		border: 1px solid #ccc;
		padding: 10px;
	}
	</style>

上面的例子是通过 Vue 的 `<component>` 元素和特殊的 is attribute 实现的。被传给 :is 的值可以是以下几种：

- 被注册的组件名
- 导入的组件对象

你也可以使用 is attribute 来创建一般的 HTML 元素。

当使用 `<component :is="...">` 来在多个组件间作切换时，被切换掉的组件会被卸载。我们可以通过 `<KeepAlive>` 组件强制被切换掉的组件仍然保持“存活”的状态。

#### DOM 内模板解析注意事项

如果你想在 DOM 中直接书写 Vue 模板，Vue 则必须从 DOM 中获取模板字符串。由于浏览器的原生 HTML 解析行为限制，有一些需要注意的事项。

##### 大小写区分

HTML 标签和属性名称是不分大小写的，所以浏览器会把任何大写的字符解释为小写。这意味着当你使用 DOM 内的模板时，无论是 PascalCase 形式的组件名称、camelCase 形式的 prop 名称还是 v-on 的事件名称，都需要转换为相应等价的 kebab-case (短横线连字符) 形式：

	// JavaScript 中的 camelCase
	const BlogPost = {
	props: ['postTitle'],
	emits: ['updatePost'],
	template: `
		<h3>{{ postTitle }}</h3>
	`
	}

	<!-- HTML 中的 kebab-case -->
	<blog-post post-title="hello!" @update-post="onUpdatePost"></blog-post>

##### 闭合标签

我们在上面的例子中已经使用过了闭合标签 (self-closing tag)：

	<MyComponent />

这是因为 Vue 的模板解析器支持任意标签使用 /> 作为标签关闭的标志。

然而在 DOM 内模板中，我们必须显式地写出关闭标签：

	<my-component></my-component>

这是由于 HTML 只允许一小部分特殊的元素省略其关闭标签，最常见的就是 `<input>` 和 `<img>`。对于其他的元素来说，如果你省略了关闭标签，原生的 HTML 解析器会认为开启的标签永远没有结束。

##### 元素位置限制

某些HTML元素对于放在其中的元素类型有限制，例如`<ul>`、`<ol>`、`<table>`和`<select>`，相应的，某些元素仅在放于特定元素中时才会显示，例如：`<li>`,`<tr>`和`<option>`。

这将导致使用带有此类限制元素的组件时出现问题。例如：

	<table>
	<blog-post-row></blog-post-row>
	</table>

自定义的组件 <blog-post-row> 将作为无效的内容被忽略，因而在最终呈现的输出中造成错误。我们可以使用特殊的 is attribute 作为一种解决方案：

	<table>
	<tr is="vue:blog-post-row"></tr>
	</table>

*tip:当使用在原生 HTML 元素上时，is 的值必须加上前缀 vue: 才可以被解析为一个 Vue 组件。这一点是必要的，为了避免和原生的自定义内置元素相混淆。*



## 术语汇总

### SFC

单文件组件，Single-File Components。

### kebab-case

短横线命名法。将多个单词用短横线连接，常用语CSS类名、文件名和URL。

### PascalCase

帕斯卡签名法，将多个单词连接在一起，首字母大写，不使用分隔符

Vue推荐为子组件使用`PascalCase`的签名，以此来和原生的HTML元素作区分。

### DOM

HTML DOM 是HTML Document Object Model（文档对象模型）的缩写，是专门适用于HTML/XHTML的文档对象模型。

熟悉软件开发的人员可以将HTML DOM理解为网页的API。它将网页中的各个元素都看作一个个对象，从而使网页中的元素也可以被计算机语言获取或者编辑。 例如Javascript就可以利用HTML DOM动态的修改网页。

根据W3C DOM规范,DOM是一种与浏览器，平台，语言无关的接口，使得你可以访问页面其他的标准组件。简单理解，DOM解决了Netscape的JavaScript和 Microsoft的JavaScript之间的冲突，给予web设计师和开发者一个标准的方法，让他们来访问他们站点中的数据、脚本和表现层对象。

HTML DOM 定义了访问和操作HTML文档的标准方法。

HTML DOM 把 HTML 文档呈现为带有元素、属性和文本的树结构(节点树)。

下面列出一些常用的 DOM 对象方法:

|方法|描述|
|:------|:------|
|getElementById()|返回带有指定 ID 的元素。|
|getElementsByTagName()|返回包含带有指定标签名称的所有元素的节点列表(集合/节点数组)。|
|getElementsByClassName()|返回包含带有指定类名的所有元素的节点列表。|
|getAttribute()|返回指定的属性值。|
|setAttribute()|把指定属性设置或修改为指定的值。|
|createElement()|创建元素节点。|
|createTextNode()|创建文本节点。|

