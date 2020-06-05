---
title: 识别独特访客
description: 适用于 Adobe ECID（ID 服务）的文档
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 56%

---


# 识别独特访客

用于在多个上下文中识别独特访客的方法包括一个按优先级排列的顺序，以确保此确定的准确性。下表显示了此优先级顺序：

| 使用的订单 | 查询参数（收集方法） | post_visid_type列值 | 在 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` 。 |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html)  | 3  | Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/zh-Hans/id-service/using/reference/analytics-reference/grace-period.html) configured.  |
|  3  | 由[Identity Service设置的mid AMCV_ cookie](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html)  |  5  |  访客的浏览器接受cookies（第一方），并[!UICONTROL 部署Identity]Service。  |
|  4  | fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html)  |  4  |  访客的浏览器接受cookie（第一方）。  |
|  5  |  [HTTP移动订户头](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html)  |  2  |  设备被识别为移动设备。  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html)  |  1  |  访客的浏览器不接受cookie。 |

有关如何报告独特访客的信息，请参阅 [Analytics 中的独特访客](https://docs.adobe.com/content/help/zh-Hans/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
