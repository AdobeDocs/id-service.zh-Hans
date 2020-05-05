---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 数据收集 CNAME 和跨域跟踪
title: 数据收集 CNAME 和跨域跟踪
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 数据收集 CNAME 和跨域跟踪{#data-collection-cnames-and-cross-domain-tracking}

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方Cookie的浏览器中，数据收集服务器在请求访客ID期间设置Cookie。 此Cookie允许访客ID服务在使用相同Experience Cloud组织ID配置的所有域上返回相同的Experience Cloud访客ID。

在拒绝第三方Cookie的浏览器中，将为每个域分配一个新的Experience Cloud访客ID。

demdex.net cookie使访客ID服务能够提供与Analytics中s_vi cookie相同级别的跨域跟踪，其中某些浏览器接受cookie并在域之间使用cookie，但其他浏览器拒绝。

## Data Collection CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/ec-cookies/cookies-first-party.html) to avoid issues with browsers that reject third-party cookies. 此过程将您的访客收集服务器域配置为与您的网站域匹配，因此将数据ID cookie设置为第一方cookie。

由于访客ID服务使用JavaScript直接在当前网站的域上设置访客cookie，因此不再需要此配置来设置第一方cookie。

具有单一 Web 属性（单一域）的客户可以从使用数据收集 CNAME 中迁移出来，改为使用其默认的数据收集主机名（`omtrdc.net` 或 `2o7.net`）。

但是，使用CNAME进行数据收集还有一个好处，它允许您在不接受第三方cookie的浏览器中跟踪主登录域和其他域之间的访客。 具有多个Web属性（多个域）的客户可能从维护数据收集CNAME中受益。 以下部分介绍跨域访客跟踪的工作方式。

## CNAME 如何启用跨域跟踪 {#section-78925af798e24917b9abed79de290ad9}

由于可以在 Apple Safari 和其他一些浏览器的第三方上下文中使用第一方 Cookie，CNAME 允许您跟踪主域和其他一些使用相同跟踪服务器的域之间的客户。

例如，您的主站点为 `mymainsite.com`。您将 CNAME 记录配置为指向安全的数据收集服务器：`smetrics.mymainsite.com`。

当用户访问 `mymainsite.com` 时，数据收集服务器将设置 ID 服务 Cookie。此操作是允许的，因为数据收集服务器的域与网站的域相匹配，也就是我们所说的在&#x200B;*第一方上下文*&#x200B;中使用 Cookie，或者说是使用&#x200B;*第一方 Cookie*。

如果您在其他站点（如 `myothersiteA.com` 和 `myothersiteB.com`）上也使用同样的数据收集服务器，那么当访客稍后访问这些站点时，访问 `mymainsite.com` 期间设置的 Cookie 将在 HTTPS 请求中发送给数据收集服务器（记住，浏览器会使用所有 HTTPS 请求将域的所有 Cookie 发送给该域，即使该域与当前网站的域不匹配也不例外）。这就是我们所说的在&#x200B;*第三方上下文*&#x200B;中使用 Cookie，或者说是使用&#x200B;*第三方 Cookie*，从而实现在其他域上使用同样的访客 ID。请注意，浏览器处理第三方上下文中 Cookie 的方式与处理第一方 Cookie 的方式有所不同。

*注意：Safari 会阻止第三方上下文中的所有 Cookie，而不管它们是如何设置的。*

因此，您的收集域应当为人们通常访问的域，以便系统能够在多个域上对访客进行识别。如果没有用于数据收集域的&#x200B;*通用*&#x200B;域，那么维护数据收集域的 CNAME 在跨域方面并没有任何优势。如果最先访问的不是主登录网站，那么访客在二级网站和主网站上将被视为不同的访客。

## 通过 Experience Cloud Identity 服务启用 CNAME 支持{#section-25d4feb686d944e3a877d7aad8dbdf9a}

通过设置 `visitor.marketingCloudServerSecure` 变量，可以启用数据收集服务器 CNAME 支持。
