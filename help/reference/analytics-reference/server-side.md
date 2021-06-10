---
description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
keywords: ID 服务
title: 结合了 JavaScript 技术的服务器端实施
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# 结合了 JavaScript 技术的服务器端实施 {#server-side-implementation-mixed-with-javascript}

在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。

ID 服务 API 提供了 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) 和 [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) 方法，以便检索可随后传递到服务器的 ID 值。

请务必检查 Experience Cloud 访客 ID 和 Analytics 访客 ID，并发送这两个 ID（如果存在）以确保发送的任何数据都与现有的 Analytics 访客配置文件相关联。

>[!IMPORTANT]
>
>AppMeasurement for Java 当前不支持 Experience Cloud Identity 服务。

## 数据插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中包括 Analytics 访客 ID（如果已设置）。

在 `<marketingCloudVisitorID>` 元素中包括 Experience Cloud 访客 ID。

请参阅[支持的 XML 标记](https://www.adobe.io)。

## Java AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

AppMeasurement for Java 当前不支持 Experience Cloud Identity 服务。
