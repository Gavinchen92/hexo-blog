---
title: 什么是ETag
date: 2017-12-15 14:59:44
tags: http
---

全称: entity tag

ETag 是一个 http 返回头中用来区分资源版本的字段, 被称为资源的指纹.

当客户端请求某个资源时, 请求头中会带上 If-None-Match, 当服务端对比 ETag 相同时返回 304, 它使浏览器的缓存更高效, 节省带宽.

Http/1.1 并没有规定 ETag 的值该如何生成.

它的功能与 Last-Modified 类似, Last-Modifed 的问题是只能精确到秒, 所以 ETag 更适合敏感资源.
