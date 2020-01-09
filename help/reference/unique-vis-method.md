---
title: 识别独特访客
description: Adobe ECID（ID服务）文档
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 识别独特访客

在多个上下文中识别唯一访客的方法包括确定优先级顺序以确保该确定的准确性。 下表显示了此优先顺序：


 
|使用的顺序|查询参数（收集方法）| post_visid_type列值|在||—|—|—|—|| 1 |[vid(s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 | s.visitorID已设置。| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid（由Identity service设置的AMCV_ cookie）](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 |访客的浏览器接受Cookie（第一方），然后部署Identity Service。 || 4 |[fid（H.25.3或更高版本上的回退cookie，或AppMeasurement for javaScript）](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 |访客的浏览器接受cookie（第一方）。 || 5 |[HTTP移动订阅者标题](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 |设备被识别为移动设备。 || 6 |[IP地址、用户代理、网关IP地址](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 |访客的浏览器不接受cookie。 |


有关如何报告独特访客的信息，请参阅Analytics [中的独特访客](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
