---
description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
keywords: 操作顺序;ID 服务
title: CNAME 实施概述
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 100%

---

# CNAME 实施概述{#cname-implementation-overview}

通过 CNAME 实施，您可以自定义 Adobe 使用的收藏集域，以便与您自己的域匹配。这些域也称作第一方收藏集域。通过这些实施，Adobe 可使用 JavaScript 在服务器端而非客户端设置第一方 Cookie。这些服务器端第一方 Cookie 过去不受 Apple 的智能反追踪 (ITP) 政策的约束。但是，2020 年 11 月，[!DNL Apple] 更新了政策，规定这些限制也适用于通过 CNAME 设置的 Cookie。目前，通过 CNAME 在服务器端设置的 Cookie 和通过 JavaScript 在客户端设置的 Cookie 均须根据 ITP 遵守 7 日或 24 小时过期限制。有关 ITP 政策的更多信息，请参阅此有关跟踪预防的[!DNL Apple]文档[](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)。

虽然 CNAME 实施未提供 Cookie 生命周期方面的好处，但可能会带来其他一些好处。这些好处包括广告拦截器和不太常见的浏览器，可防止数据被发送到它们归类为跟踪器的域。在这些情况下，使用 CNAME 可以在对使用这些工具的用户进行数据收集时防止中断。

此外，利用 CNAME 实施，您可以[选择自定义 RDC 类型](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=zh-Hans)来控制最初路由用户点击的位置。大多数客户不使用自定义 RDC 类型。
