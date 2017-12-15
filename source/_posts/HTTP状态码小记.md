---
title: HTTP状态码小记
date: 2017-12-15 11:12:34
tags: http
---

前言: http 本质上只是一段纯文本, 它在前后端的交互主要靠规范约定

今天在阅读 Koa 文档正好看到了 http 状态码, 我们平常开发时只会用到其中几种, 以至于我对大部分不太熟悉

把所有的状态码都列一遍加深记忆:

* 100 "Continue" 继续
* 101 "Switching protocols" 转换协议
* 102 "processing" 正在处理
* 200 "ok" 一切正常
* 201 "created" 创建完成
* 202 "accepted" 被接受
* 203 "non-authoritative information" 非权限信息
* 204 "no content" 无内容
* 205 "reset content" 重置内容
* 206 "partial content" 部分信息
* 207 "multi-status" 多种状态
* 208 "already reported" 已经报告
* 226 "im used" 已经使用
* 300 "multiple choices" 多选择
* 301 "moved permanently" 永久移除
* 302 "found" 找到目标
* 303 "see other" 查看其他
* 304 "not modified" 未修改
* 305 "use proxy" 使用代理
* 307 "temporary redirect" 临时重定向
* 308 "permanent redirect" 永久重定向
* 400 "bad request" 无效的请求
* 401 "unauthorized" 未鉴权
* 402 "payment required" 需要付款
* 403 "forbidden" 静止请求
* 404 "not found" 未找到
* 405 "method not allowed" 请求方法不允许
* 406 "not acceptable" 不接受
* 407 "proxy authoritication required" 代理需要鉴权信息
* 408 "request timeout" 请求超时
* 409 "conflict" 冲突
* 410 "gone" 被移走
* 411 "length required" 长度要求
* 412 "precondition failed" 验证前提条件失败
* 413 "payload too large" 载体过大
* 414 "uri too long" uri 过长
* 415 "unsupported media type" 不支持的媒体类型
* 416 "range not satisfiable" 范围不满足
* 417 "expectation failed" 期望失败
* 418 "i'm a teapot" 我是个茶壶 ○rz ps. 哪个大神发明的啊
* 422 "unprocessable entity" 不能处理的实体
* 423 "locked" 被锁定
* 424 "failed dependency" 依赖失败
* 426 "upgreade requied" 需要更新
* 428 "precondiction required" 需要验证前提条件
* 429 "too many requests" 太多请求
* 431 "request header fields too large" 请求头字段过多
* 500 "internal server error" 内部服务错误
* 501 "not implemented" 未实现
* 502 "bad gateway" 网管错误
* 503 "service unavailable" 服务不可用
* 504 "gateway timeout" 网管超时
* 505 "http version not supported" http 版本不支持
* 506 "variant also negotiates" 变动正在交涉中
* 507 "insufficient storage" 内存不足
* 508 "loop detected" 发现循环
* 510 "not extended" 未扩展
* 511 "network authentication required" 要求网络鉴权
