---
description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID Service
seo-description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
seo-title: 2020 版发行说明
title: 2020 版发行说明
translation-type: tm+mt
source-git-commit: d0057a8242dafca63101b1a2f569766bde11bea7
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 91%

---


# Experience Cloud 发行说明 - 2020 版 {#release-notes}

关于 Experience Cloud Identity 服务 (ECID) 的功能发布、更新或更改。

## 版本 4.6

* 默认情况下将 `loadSSL` 标记设为开启。所有对 Identity 服务的调用都将默认开启 `https`。如果客户希望在 http 上从其 `non-ssl` 页面调用 Identity 服务，则客户可以将其设置为 false。
* 更新了用于检测 `Internet-Explorer (IE)` 版本的功能，以修复由 `ESLint` 报告的问题。修复了为 ECID 指定选择加入 `pre-approval` 且稍后进行更新时，`Internet-Explorer (IE) 11` 上出现的性能问题。

## 版本 4.5

* 从版本 4.5 开始，ECID 将拒绝任何发送到 `setCustomerIDs` 方法中的空 ID。
* 修复了将选择加入配置为 `doesOptInApply=false` 和 `isIabContext=true` 后出现的问题。

请参 [阅Experience Cloud发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html) ，了解所有产品的月度发行说明。
