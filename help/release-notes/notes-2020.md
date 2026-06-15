---
description: 关于 Experience Cloud 身份标识服务的功能发布、更新或更改。
keywords: ID 服务
title: 2020 版发行说明
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 91%

---

# Experience Cloud 发行说明 - 2020 {#release-notes}

关于 Experience Cloud 身份标识服务的功能发布、更新或更改。

## 版本 5.1.1

* 提供了修补程序，用于在 iFrame 中加载 VisitorJS 时为 AMCV Cookie 设置 `SameSite=None`。

## 版本 5.1.0

* 添加 `sameSiteCookie` 配置以指定 AMCV Cookie 的 `SameSite` 属性。 此配置支持 `SameSite` 属性的以下值：
   * `Strict`
   * `Lax`
   * `None`

有关这些属性值的更多信息，请访问 [web.dev](https://web.dev/samesite-cookies-explained/) 和 [Chromium 项目的 SameSite 更新](https://www.chromium.org/updates/same-site/)。

## 版本 5.0.1

* 提供了修补程序，用于在将新的 IAB 同意字符串发送到 Adobe 数据收集边缘时包括 `d_cf` 标记。

## 版本 5.0.0

* Visitor 5.0.0 版本，支持 `IAB 2.0`。

## 版本 4.6

* 默认情况下将 `loadSSL` 标记设为开启。 所有对身份标识服务的调用都将默认开启 `https`。  如果客户希望在 http 上从其 `non-ssl` 页面调用身份标识服务，则客户可以将其设置为 false。
* 更新了用于检测`Internet-Explorer (IE)`版本的函数，以修复`ESLint`报告的问题。
修复了为ECID指定选择加入`pre-approval`且稍后更新时，`Internet-Explorer (IE) 11`上的性能问题。

## 版本 4.5

* 从版本 4.5 开始，ECID 将拒绝任何发送到 `setCustomerIDs` 方法中的空 ID。
* 修复了将选择加入配置为 `doesOptInApply=false` 和 `isIabContext=true` 后出现的问题。

请参阅 [Experience Cloud 发行说明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hans)，了解所有产品的月度发行说明。

