---
description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
keywords: ID Service
seo-description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
seo-title: 结合了 JavaScript 技术的服务器端实施
title: 结合了 JavaScript 技术的服务器端实施
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 结合了 JavaScript 技术的服务器端实施 {#server-side-implementation-mixed-with-javascript}

在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。

ID服务API提供getMarketingCloudVisitorID [和getAnalyticsVisitor](../../library/get-set/getmcvid.md) ID [等方法](../../library/get-set/getanalyticsvisitorid.md)，用于检索随后可传递到服务器的ID值。

请务必检查 Experience Cloud 访客 ID 和 Analytics 访客 ID，并发送这两个 ID（如果存在）以确保发送的任何数据都与现有的 Analytics 访客配置文件相关联。

>[!IMPORTANT]
>
>AppMeasurement for Java 当前不支持 Experience Cloud Identity 服务。

## 数据插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中包括 Analytics 访客 ID（如果已设置）。

在 `<marketingCloudVisitorID>` 元素中包括 Experience Cloud 访客 ID。

请参 [阅支持的XML标签](https://www.adobe.io)。

## Java AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

AppMeasurement for Java 当前不支持 Experience Cloud Identity 服务。
