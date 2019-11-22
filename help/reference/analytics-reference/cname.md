---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 数据收集 CNAME 和跨域跟踪
title: 数据收集 CNAME 和跨域跟踪
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# 数据收集和标识{#data-collection-and-identity}

在分析中，有三种方法可用于识别访客。

- 使用访 [客ID服务](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- 使用旧 [版Analytics访客ID](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- 提供自己的身份

## Using the Visitor ID Service{#using-the-visitor-id-service}

建议使用访客ID服务来识别访客。 它基于两个组件

- 第一方ID —— 可用于测量您自己网站的访客的第一方ID。 此ID存储在第一部分ID中，同时存储在客户端Cookie和服务器端Cookie中（带有CNAME）。
- 第三方ID（可选）-存储在demdex.net上的单独第三方ID，可用于跨多个域（例如example.com和example.net）测量访客

分析将始终使用第一方ID，如果启用并提供第三方ID，则每个站点上的第一方ID将相同。 但是，如果您的设置或浏览器阻止第三方Cookies而禁用了第三方ID，则无法将这两个站点上的流量绑定在一起。

## 旧版分析域

几年前，在启动访客ID服务之前，许多客户使用本机分析域设置ID cookie。 这些 `omtrdc.net`包 `2o7.net` 括或CNAME的域。 `omtrdc.net`, `2o7.net` 并且在某些情况下，CNAME'd域用于存储第三方Cookie。 以这种方式设置的Cookie始终仅限于单个客户，因此客户无法跨公司合并其数据。 只有当客户希望跨自己拥有的站点跟踪用户时(例如example.com、example.co.jp)，才使用第三方CNAMED'd域（有时称为友好的第三方域）。 不建议使用此方法，以便提供更强健和更了解隐私的访客ID服务。 客户应在可行时尽快使用每个域的CNAME转到访客ID服务。

## 提供您自己的身份

如果客户选择通过Adobe的识别系统，并通过提供自定义访客ID来实施自 [己的系统](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)。 如果选择此路线，有些事情需要注意。

- 您需要实施退出和适当的隐私控制
- 该ID将仅适用于Analytics
- 您有责任保持该ID

## 数据收集CNAMES

Adobe仍建议将CNAME与访客ID服务结合使用。 这允许第一方访客ID使用HTTP cookies进行持久保存，这使Cookies更加耐用。

## 选择退出

Adobe提供API与我们的系统共享退出信号，以便您为用户提供退出跟踪的方法。 我们提供了关于退出和 [选择加入](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md)[的详细说明](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## 通过 Experience Cloud Identity 服务启用 CNAME 支持{#section-25d4feb686d944e3a877d7aad8dbdf9a}

通过在Experience Cloud Identity service中设 [置变量以及在AppMeasurement中设置，可启用数据收集服务器CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md)`visitor.marketingCloudServerSecure``s.trackingServerSecure` 支持。
