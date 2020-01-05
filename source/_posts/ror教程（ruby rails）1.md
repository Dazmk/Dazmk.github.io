title: ror教程（ruby on rails）1
tags:
  - Rails
categories:
  - Rails
author: Dashy
date: 2017-12-26 22:42:00
---
 git rm -r --cached .
 删除暂存区中的全部文件(未commit 已add)
 git checkout -f
 恢复未add 的文件

 scaffold 脚手架生成资源
 资源可以理解为model（数据模型）+view（web页面），可以通过http协议在网页中创建、读取、更新和删除。

 REST 架构由计算机科学家 Roy Fielding 提出，意思是“表现层状态转化”（Representational State Transfer）

 REST 是一种架构风格，用于开发分布式、基于网络的系统和软件应用，例如万维网和 Web 应用。REST 理论很抽象，在 Rails 应用中，REST 意味着大多数组件（例如用户和微博）都被模型化，变成资源（resource），可以创建（create）、读取（read）、更新（update）和删除（delete）。这些操作与关系型数据库中的 CRUD 操作和 HTTP 请求方法（POST、GET、PATCH 和 DELETE）对应。
