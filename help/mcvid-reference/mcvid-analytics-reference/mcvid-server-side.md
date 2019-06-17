---
description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
keywords: ID 服务
seo-description: 在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。
seo-title: 结合了 JavaScript 技术的服务器端实施
title: 结合了 JavaScript 技术的服务器端实施
uuid: 256ea0e7-1eb4-4c92-9a7e-f61 cb1 ed13 c7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 结合了 JavaScript 技术的服务器端实施 {#server-side-implementation-mixed-with-javascript}

在一些实施过程中，访客 ID 是经由 JavaScript 传送至服务器，这样一来服务器就可以发送其他的 Analytics 事件（例如购买事件）。

ID 服务 API 提供了 [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) 和 [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) 方法，以检索随后可传送至服务器的 ID 值。

请务必检查 Experience Cloud 访客 ID 和 Analytics 访客 ID，并发送这两个 ID（如果存在）以确保发送的任何数据都与现有的 Analytics 访客配置文件相关联。

>[!IMPORTANT]
>
>AppMeasurement for Java当前不支持Experience Cloud ID服务。

## 数据插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中包括Analytics访客ID(如果设置)。

在元素中包含Experience `<marketingCloudVisitorID>` Cloud访客ID。

请参阅[支持的 XML 标签](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)。

## Java AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

AppMeasurement for Java 当前不支持 Experience Cloud ID 服务。