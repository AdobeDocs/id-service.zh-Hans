---
description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
keywords: 操作顺序;ID 服务
title: CNAME 实施概述
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 100%

---


# CNAME 实施概述{#cname-implementation-overview}

通过 CNAME 实施，您可以自定义 Adobe 使用的收藏集域名，以便与您自己的域名匹配。这将允许 Adobe 在服务器端设置第一方 Cookie，而不是使用 JavaScript 在客户端进行设置。这些服务器端第一方 Cookie 过去不受 Apple 的智能反追踪 (ITP) 政策的约束。但是，2020 年 11 月，[!DNL Apple] 更新了政策，规定这些限制也适用于通过 CNAME 设置的 Cookie。目前，通过 CNAME 在服务器端设置的 Cookie 和通过 JavaScript 在客户端设置的 Cookie 均须根据 ITP 遵守 7 日或 24 小时过期限制。有关 ITP 政策的更多信息，请参阅关于反追踪的此[!DNL Apple]文档[](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)。

尽管 CNAME 实施在 Cookie 生命周期方面没有任何益处，但是它可能提供其他益处，比如，广告拦截、可防止将数据发送到归类为追踪器的域的不太常见的浏览器。在这些情况下，使用 CNAME 可以在对使用这些工具的用户进行数据收集时防止中断。