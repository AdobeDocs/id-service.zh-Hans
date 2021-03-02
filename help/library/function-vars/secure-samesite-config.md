---
description: ECID中可用于支持Google AMP页面上的AMCV Cookie的配置。
keywords: ID 服务
seo-description: ECID中可用于支持Google AMP页面上的AMCV Cookie的配置。
seo-title: 安全和相同站点配置
title: 安全和相同站点配置
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# 安全和相同站点配置

此配置允许您更改Cookie的设置，并支持Google AMP页面上的[AMCV Cookie](../../introduction/cookies.md)。

Adobe访客ID服务将ECID Cookies设置为浏览器默认设置`SameSite = Lax`，如果页面加载到Google AMP页面等iframe中，则无法访问该设置。 要访问ECID Cookie，请使用以下配置将SameSite设置更新为`SameSite = None`。

>[!NOTE]
>
>在应用`SameSite = None`时，Cookie必须设置为`Secure`，这样才能通过HTTPS连接传递数据。

**实施**:

如果您使用Adobe Experience Platform Launch，请将您的Experience CloudID扩展升级到版本5.1.0并配置`secureCookie: true`和`sameSiteCookie: none`。

如果您没有使用Experience Platform Launch，请在初始化访客实例时更新到最新的访客 5.1.0库，并遵循以下配置：

**代码示例**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
