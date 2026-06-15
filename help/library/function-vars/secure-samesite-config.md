---
description: ECID 内可用于在 Google AMP 页面上支持 AMCV Cookie 的配置。
keywords: ID 服务
title: Secure 和 SameSite 配置
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
ht-degree: 100%

---

# Secure 和 SameSite 配置

通过此设置，可更改 Cookie 的设置并在 Google AMP 页面上支持 [AMCV Cookie](../../introduction/cookies.md).

Adobe 访客 ID 服务为 ECID Cookie 设置 `SameSite = Lax` 的浏览器默认设置，如果在 Google AMP 页面等 iframe 中加载页面，则无法访问这些 Cookie。 要访问 ECID Cookie，请使用下方配置将 SameSite 设置更新为 `SameSite = None`。

>[!NOTE]
>
>在应用 `SameSite = None` 时，必须将 Cookie 设置为 `Secure`，以使只能通过 HTTPS 连接传递数据。

**实施**：

如果使用 Adobe Experience Platform Launch，请将 Experience Cloud ID 扩展升级到 5.1.0 版，并配置 `secureCookie: true` 和 `sameSiteCookie: none`。

如果不使用 Experience Platform Launch，请更新到最新的访客 5.1.0 库，并在初始化访客实例时遵循下方配置：

**代码示例**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

