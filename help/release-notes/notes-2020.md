---
description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID 服务
title: 2020 版发行说明
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 64%

---

# Experience Cloud发行说明 — 2020版 {#release-notes}

关于 Experience Cloud Identity 服务的功能发布、更新或更改。

## 版本 5.1.1

* 修补程序修复了在 `SameSite=None` 在iFrame中加载VisitorJS时。

## 版本 5.1.0

* 添加 `sameSiteCookie` 用于指定 `SameSite` 属性。 此配置支持 `SameSite` 属性：
   * `Strict`
   * `Lax`
   * `None`

有关这些属性值的更多信息，请访问 [web.dev](https://web.dev/samesite-cookies-explained/) 和 [Chromium项目的SameSite更新](https://www.chromium.org/updates/same-site/).

## 版本 5.0.1

* 修补程序修复(包括 `d_cf` 标记何时将新的IAB同意字符串发送到Adobe数据收集边缘。

## 版本 5.0.0

* Visitor 5.0.0版本，支持 `IAB 2.0`.

## 版本 4.6

* 默认情况下将 `loadSSL` 标记设为开启。所有对 Identity 服务的调用都将默认开启 `https`。如果客户希望在 http 上从其 `non-ssl` 页面调用 Identity 服务，则客户可以将其设置为 false。
* 更新了用于检测 `Internet-Explorer (IE)` 版本的功能，以修复由 `ESLint` 报告的问题。修复了为 ECID 指定选择加入 `pre-approval` 且稍后进行更新时，`Internet-Explorer (IE) 11` 上出现的性能问题。

## 版本 4.5

* 从版本 4.5 开始，ECID 将拒绝任何发送到 `setCustomerIDs` 方法中的空 ID。
* 修复了将选择加入配置为 `doesOptInApply=false` 和 `isIabContext=true` 后出现的问题。

请参阅 [Experience Cloud 发行说明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hans)，了解所有产品的月度发行说明。
