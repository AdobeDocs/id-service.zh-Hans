---
description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
keywords: 操作顺序;ID 服务
title: CNAME 实施概述
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# CNAME 实施概述{#cname-implementation-overview}

通过 CNAME 实施，您可以自定义 Adobe 使用的收藏集域名，以便与您自己的域名匹配。这些域也称为第一方集合域。 这些实施允许Adobe使用JavaScript在服务器端而不是客户端设置第一方Cookie。 这些服务器端第一方 Cookie 过去不受 Apple 的智能反追踪 (ITP) 政策的约束。但是，2020 年 11 月，[!DNL Apple] 更新了政策，规定这些限制也适用于通过 CNAME 设置的 Cookie。目前，根据ITP，通过CNAME在服务器端设置的Cookie和通过Javascript在客户端设置的Cookie均受七天或24小时的到期限制。 有关 ITP 政策的更多信息，请参阅关于反追踪的此[!DNL Apple]文档[](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)。

虽然CNAME实施在Cookie生命周期方面不提供任何好处，但可能还有其他一些好处。 这些好处包括广告拦截器和不太常见的浏览器，它们会阻止数据发送到它们分类为跟踪器的域。 在这些情况下，使用CNAME可以防止使用这些工具的用户中断数据收集。

此外，CNAME实施允许您指定 **[!UICONTROL 选择自定义RDC类型]** 可控制最初将用户点击路由到的位置。 大多数客户不使用自定义RDC类型。
