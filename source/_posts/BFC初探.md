---
title: BFC初探
date: 2017-12-14 22:49:52
tags: CSS
---

中文名: 块级可视化上下文

布局规则:

1. 内部的 Box 会在垂直方向, 一个接一个地放置.
1. Box 垂直方向的距离由`margin`决定, 属于同一个 BFC 的两个相邻 Box 的`margin`会发生重叠.
1. 每个元素的`margin box`的左边, 与包含块`border box`的左边想接触(对于从左往右的格式化, 否则相反), 即使存在浮动也是如此.
1. BFC 的区域不会与`float box`重叠.
1. BFC 就是页面上的一个隔离的独立容器, 容器里面的子元素不会影响到外面的元素.反之也是如此.
1. 计算 BFC 的高度时, 浮动元素也参与计算.

哪些元素会生成 BFC:

1. 根元素
1. float 元素不为 none
1. `position`为`absolute`或`fixed`
1. `display`为`inline-block, table-cell, table-caption, flex, inline-flex`
1. overflow 不为`visible`
