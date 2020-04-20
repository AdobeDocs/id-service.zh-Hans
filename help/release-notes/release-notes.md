---
description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID Service
seo-description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
seo-title: 2020 版发行说明
title: 2020 版发行说明
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud 发行说明 - 2020 版 {#release-notes}

关于 Experience Cloud Identity 服务 (ECID) 的功能发布、更新或更改。

## 版本 4.6

* 默认 `loadSSL` 情况下为开启标记。 默认情况下，对Identity Service的所有调用 `https` 都将打开。  如果客户希望从其页面的http上调用Identity Services，则可将其设置为 `non-ssl` false。
* 更新了用于检测版本 `Internet-Explorer (IE)` 的函数，以修复由报告的问题 `ESLint`。
修复了ECID在获得选 `Internet-Explorer (IE) 11` 择加入并稍后更新时 `pre-approval` 的性能问题。

## 版本 4.5

* 从版本 4.5 开始，ECID 将拒绝任何发送到 `setCustomerIDs` 方法中的空 ID。
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.
