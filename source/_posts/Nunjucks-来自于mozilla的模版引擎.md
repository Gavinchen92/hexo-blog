---
title: Nunjucks--来自于mozilla的模版引擎
date: 2017-12-18 17:22:55
tags: nodejs
---

最近打算搭建一个以 nodejs 做服务端的项目, 公司要求兼容到 ie8, 且要做 seo, 所以再找一个合适的模版引擎.
看了 jade, ejs, handlebars 都感觉不太合适: jade 太抽象, ejs 太繁琐, handlebars 不够强大

我认为理想的模版引擎必须要有以下的特点:

* 不能破坏原有的 html 结构
* 语法必须简洁
* 方便扩展

纠结了几天后我碰到了 nunjucks, 是 jinja2 的 javascript 实现, 基本符合我的需求且它的背后是 mozilla, 有完善的中文文档, 质量应该有保证.
但 nunjucks 也不是完美的, 它的语法以及逻辑继承自 python 而不是 javascript, 这会对前端开发人员造成一定的困扰
