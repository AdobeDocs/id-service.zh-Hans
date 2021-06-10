---
description: ECID 内可用于在 Google AMP 页面上支持 AMCV Cookie 的配置。
keywords: ID 服务
title: Secure 和 SameSite 配置
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 100%

---

# Secure 和 SameSite 配置

通过此设置，可更改 Cookie 的设置并在 Google AMP 页面上支持 [AMCV Cookie](../../introduction/cookies.md).

Adobe 访客 ID 服务为 ECID Cookie 设置 `SameSite = Lax` 的浏览器默认设置，如果在 Google AMP 页面等 iframe 中加载页面，则无法访问这些 Cookie。要访问 ECID Cookie，请使用下方配置将 SameSite 设置更新为 `SameSite = None`。

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
