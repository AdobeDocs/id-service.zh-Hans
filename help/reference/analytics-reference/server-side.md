---
description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
keywords: ID 服务
seo-description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
seo-title: 结合了 JavaScript 技术的服务器端实施
title: 结合了 JavaScript 技术的服务器端实施
uuid: 256ea0e7-1eb4-4c92-9a7e-f61 cb1 ed13 c7
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 结合了 JavaScript 技术的服务器端实施 {#server-side-implementation-mixed-with-javascript}

在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。

ID 服务 API 提供了 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) 和 [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) 方法，以检索随后可传送至服务器的 ID 值。

请务必检查 Experience Cloud 访客 ID 和 Analytics 访客 ID，并发送这两个 ID（如果存在）以确保发送的任何数据都与现有的 Analytics 访客配置文件相关联。

>[!IMPORTANT]
>
>AppMeasurement for Java当前不支持Experience Cloud ID服务。

## 数据插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

Include the Analytics visitor ID (if set) in the `<visitorID>` element.

Include the Experience Cloud visitor ID in the `<marketingCloudVisitorID>` element.

请参阅[支持的 XML 标签](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)。

## Java AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

AppMeasurement for Java目前不支持Experience Cloud ID服务。
