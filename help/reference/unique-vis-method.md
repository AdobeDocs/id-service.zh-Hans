---
title: 识别独特访客
description: 适用于 Adobe ECID（ID 服务）的文档
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '223'
ht-degree: 100%

---


# 识别独特访客

用于在多个上下文中识别独特访客的方法包括一个按优先级排列的顺序，以确保此确定的准确性。下表显示了此优先级顺序： 
| 使用的顺序 | 查询参数（收集方法）| post_visid_type 列值 | 提供条件 |--- |--- |--- |--- || 1 | [vid (s.visitorID)](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html) | 0 |设置了 s.visitorID。|
| 2 | [aid (s_vi Cookie)](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html) | 3 | 在您部署访客 ID 服务前访客已拥有一个现有的 s_vi Cookie，或者您配置了访客 ID [宽限期](https://docs.adobe.com/content/help/zh-Hans/id-service/using/reference/analytics-reference/grace-period.html)。 |
| 3 | [mid（由 Identity 服务设置的 AMCV_ cookie）](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html) | 5 | 访客的浏览器接受 Cookie（第一方）并部署了 Identity 服务。 |
| 4 | [fid（H.25.3 或更高版本上的回退 Cookie，或 AppMeasurement for javaScript）](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html) | 4 | 访客的浏览器接受 Cookie（第一方）。 |
| 5 | [HTTP 移动订阅者标题](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html) | 2 | 设备被识别为移动设备。 |
| 6 | [IP 地址、用户代理、网关 IP 地址](https://docs.adobe.com/content/help/zh-Hans/analytics/technotes/visitor-identification.html) | 1 | 访客的浏览器不接受 Cookie。|

有关如何报告独特访客的信息，请参阅 [Analytics 中的独特访客](https://docs.adobe.com/content/help/zh-Hans/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
