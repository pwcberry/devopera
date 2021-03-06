---
title: Opera电视商店应用程序的设计考虑
authors:
- yenny-otero
- patrick-lauke
tags:
- opera-tv-store
- tv
language: zh-cn
license: cc-by-3.0
---

- [简介](#introduction)
- [快捷检验清单](#checklist)
- [电视情境](#context)
- [用户距离](#distance)
- [分辨率和过扫描](#resolution_overscan)
- [布局](#layout)
	- [举例](#layout_examples)
- [导航](#navigation)
	- [快捷键](#shortcuts)
- [文本输入](#input)
- [响应性能](#responsiveness)
- [隐私](#privacy)

## 简介

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/tvstore.png" alt="" class="figure__media">
	<figcaption class="figure__caption" markdown="span">Opera电视商店界面</figcaption>
</figure>

Opera电视商店向用户提供了一个基于HTML5应用程序的发布平台。

尽管电视商店的应用程序本质上也是网页，但开发者有必要了解在电视情境中，特别是Opera电视商店的模式上，设计上需要做的考虑。

## 快捷检验清单

以下是我们对一个优化的电视商店应用程序的总结建议：

- 少就是多 — 电视屏幕或许很大，可我们通常是从更远的距离观看。
- 为保证可读性和实用性，请使用至少22px大小的非衬线字体，可聚焦选择的元素高度至少34px。
- 确保您的应用程序在屏幕大小1216×684px上可用。（Opera电视商店的分辨率为1280×720，留下5％的空白防止 [过扫描 ][14]）。
- 使一切内容用标准的遥控器方向键可访问： 上, 下, 左, 右 和 返回 ， 其他键（如大多数摇控器的颜色键）只应被用来作为快捷键。
- 确保表明当前元素选定状态的聚焦框任何时候都清晰可见。
- 避免用户输入文字。
- 保证应用程序对用户操作的快响应性。

[14]: index.html#resolution_overscan

## 电视情境

当您创建应用时，您需要考虑——用户对电视的使用习惯和桌面电脑及手机是完全不同的:

- 电视主要用来娱乐休闲的，用户不希望有太多的交互及决策。
- 电视和用户距离较远，之间交互工具只有遥控器。
- 电视像移动手机一样界面简洁，但电视交互是用远程遥控器控制（4键导航）。
- 不同于其他设备，电视是公共设备，控制隐私的能力有限。
- 电视的优势在于对大图像，视频及音频的展示，您的程序应该利用这些优势。

## 用户距离

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/10feetUx2.png" alt="10-feet UX" class="figure__media">
	<figcaption class="figure__caption" markdown="span">10-英尺的用户体验: 用户坐在距离电视10英尺的沙发上.</figcaption>
</figure>

电视界面也被称为10英尺的用户界面，因为10英尺(3米)是用户离电视的大概距离。对于设计师来说，这意味着“大屏幕”不能真正的被认为是“大”,你要保持和开发移动应用程序一样的考虑。

- 所有程序的界面元素和文本都需要比桌面电脑的大。我们建议文本大小至少22像素，尽管你的设计若不看重文本，也可以使用最低18像素。再考虑到你对按钮等文字装载元素的留白，我们建议其他元素使用至少34像素的高度。
- 字体最好大而简洁。我们建议使用简单的非衬线字体。
- 尽量多的留白，以避免项目元素从远处看互相重叠覆盖。
- 背景和程序界面元素对比明显，尤其当你用整一张图片作为背景时。
- 当界面元素被选择时，聚焦框应该是清晰可见的，用户不会不知道什么地方聚焦。
- 在电视上，深色背景上的浅色内容通常更易读。
- 不要试图认为大屏幕意味着你可以包含更多的内容。少就是多。只包括相关内容,保持在每个界面的内容降到最低。

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/comparisonTvMobile.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">一个远距离观看的电视和一个近距离使用的手机没什么不同。</figcaption>
</figure>

虽然电视的察觉类似于移动设备尺寸,但设计一个移动应用并期望它在电视上也能用是不实际的：

- 手机屏幕可以垂直和水平旋转；而电视只是水平显示，在某些情况下则是宽屏。
- 因为是被远距离4键导航控制，所有为触摸屏设计的互动都需要重新设计。

## 分辨率和过扫描

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/overscan.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">如果您忽视了过扫瞄，您的应用程序可能部分在电视屏幕之外不可见。</figcaption>
</figure>

Opera电视商店运行在1280×720像素的分辨率上。但是，因为过扫描的关系，你必须保证您的应用程序在1216×684像素下也显示良好。

今天所有的电视机都有一定的过扫描，这意味着你的应用程序边缘可能在电视的可见区域之外。虽然用户可能关掉过扫描，不过最好设计程序时注意这种留白，因为大多数用户很可能意识不到“关闭过扫描”这一选择。不过电视的过扫描量是不同的,可以假设5%的边框用户可能不可见。

我们建议您在过扫描打开和关闭的情况下都测试您的程序。

## 布局

电视应用程序的布局必须简单:

- 菜单元素的最好位置是在顶部或左列。
- 保持布局尽可能简单：菜单和元素容器(列表、网格、单元素等)。
- 保持所有相关的功能和信息在一起。例如，如果有游戏得分,保持所有那些相似信息在同一边列/角落，而不是分散在屏幕上或者与其他非相关元素组合一起。
- 记住基本的图形设计理念，并让您的应用程序遵循它们：对齐、接近、平衡、一致性、对比和空白。

### 举例

在设计应用程序的布局时，我们建议您对屏幕上元素最多分为2组：菜单和内容。你也可以将菜单单独放在一个屏幕上，在另一个屏幕上对内容进行全屏设计。

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/layout-justContent.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">例子：内容和菜单分布在不同屏幕上。</figcaption>
</figure>

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/layout-horizontal.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">例子：横向布局的电视应用程序。</figcaption>
</figure>

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/layout-vertical.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">例子：纵向布局的电视应用程序。</figcaption>
</figure>

## 导航

电视用户普遍受遥控器上 只有四个方向的导航键限制： (上, 下, 左, 右) 。

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/remote.jpg" class="figure__media">
	<figcaption class="figure__caption" markdown="span">保证所有内容用方向键，确认键 和 退出键 (在某些遥控器上也可能是 返回键) 可访问。</figcaption>
</figure>

尽管一个全面的电视浏览器可能支持方向导航和虚拟鼠标的使用，但在Opera电视商店上只支持方向导航。

努力使导航简单化。在长方形或列表的设计中，元素间相对的上下左右位置很清晰，导航也更为容易。尽量避免用户突然跳跃到对角线间的另一元素上。.

避免同时混合横向和纵向导航。最好单独依赖横向列或纵向列，而不是组合使用它们。避免将重要的元素放在列表顶层或者底部，否则，用户将不得不浏览所有列表去选择它。

因为电视的横向性及比例尺，横向导航更受欢迎。也可以根据应用程序进行设计。

尽量避免使用需要激活或点击才能交互的元素。例如，避免点击列表单后才能在在列表中导航的设计。如果你有一个元素有子元素（如列表），尽量让这种点击父元素后选择子元素的操作变得明显。

### 快捷键

我们建议所有程序功能都能够用普通的导航键可访问。颜色键仅作为可选的快捷键。大多数用户并不想去学习快捷键，而且不同的摇控器上，颜色键的位置可能也并不方便使用。

在某个你经常用到，却需要很多次点击的操作上，你可以去使用颜色快捷键。但注意，并不是要用上所有的颜色键，因为用户只可能记住1,2个而不是所有的4个快捷键的用途。用4个用户可能一个都记不住，再根据您的应用程序来判断用几个快捷键。

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/shortcuts.png" class="figure__media">
	<figcaption class="figure__caption" markdown="span">例子：颜色快捷键提示信息的位置。</figcaption>
</figure>

## 文本输入

基本来说，电视和用户的互动很少，除了必要的音量调整和更换频道。尽管现在的摇控器拥有更多功能，但对于文本输入还是很原始，基本没有优化。

<figure class="figure">
	<img src="/articles/design-considerations-for-opera-tv-store-applications/remote2.jpg" class="figure__media">
	<figcaption class="figure__caption" markdown="span">电视摇控器</figcaption>
</figure>

某些电视会附带外加键盘，但用户基本还是只使用摇控器。我们建议您设计应用程序时候，尽量避免文本输入。以下是一些建议：

- 用户内容提示而不是让用户去搜索
- 通过逻辑合理的目录访问内容
- 尽可能在搜索／输入框里包含智能自动补全功能
- 当需要登录时，尽量让用户选择记住登录状态。这需要默认选上“记住我的登录状态”这个可选框。

## 响应度

电视依旧在低配置的硬件上运行。电视摇控器响应度也不高。因此需要尽量让您的应用程序拥有高响应性，避免另一瓶颈。您需要注意的是：

- 让聚焦框高光可见，让用户不用花时间寻找。
- 若操作需要一段时间，则显示进度提示。
- 不要为了动态效果而牺牲性能。如果动态效果不是很平滑或者增加负担，则禁用它。
- 当元素状态因为用户操作而发生改变，请提供加载框或者声音反馈。

我们极力推荐您在电视上测试您的应用程序。

## 隐私

移动手机是不公用的个人用品；桌面电脑可公用，但操作系统会提供多用户界面，当前活跃用户只有一个；而电视是公用设备，它被放置在房子的公共空间，它的屏幕很大并不方便隐藏信息。对此，在设计电视应用程序时需考虑:

- 大多数情况下，用户并不想在电视上输入自己的私人数据，特别是密码或者信用卡卡号等敏感信息。 对于这些服务，提供桌面网页应用让用户能够输入此类信息，然后将帐户很方便地链接到电视上。
- 方便用户清除历史纪录。
- 设计一个让当前用户能和多人交互的应用程序（如多人游戏，在共享单里加入添加元素）。
