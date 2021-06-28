---
title: 识别独特访客
description: 适用于 Adobe ECID（ID 服务）的文档
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: ht
source-wordcount: '253'
ht-degree: 100%

---

# 识别独特访客

用于在多个上下文中识别独特访客的方法包括一个按优先级排列的顺序，以确保此确定的准确性。下表显示了此优先级顺序：

| 使用顺序 | 查询参数（收集方法） | post_visid_type 列值 | 前提条件 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=zh-Hans)  | 0  | 设置 `s.visitorID`。 |
|  2  | aid  [s_vi Cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=zh-Hans#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | 在您部署访客 ID 服务前访客已拥有一个现有的 s_vi Cookie，或者您配置了访客 ID [宽限期](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=zh-Hans)。 |
|  3  | mid [由 Identity 服务设置的 AMCV_ Cookie](../introduction/cookies.md) |  5  | 访客的浏览器接受 Cookie（第一方），并部署 [!DNL Identity Service]。 |
|  4  | fid [H.25.3 或更高版本上的回退 Cookie，或者 AppMeasurement for JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=zh-Hans#section-65e33f9bfc264959ac1513e2f4b10ac7) |  4  | 访客的浏览器接受 Cookie（第一方）。  |
|  5  |  [HTTP 移动订阅者标头](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=zh-Hans)  |  2  |  设备被识别为移动设备。  |
|  6  |  [IP 地址、用户代理、网关 IP 地址](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=zh-Hans) |  1  | 访客的浏览器不接受 Cookie。 |

{style=&quot;table-layout:auto&quot;}

有关如何报告独特访客的信息，请参阅 [Analytics 中的独特访客](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=zh-Hans)。
