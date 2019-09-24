---
description: 'null'
keywords: 操作顺序;ID 服务
seo-description: 'null'
seo-title: 数据收集 CNAME 和跨域跟踪
title: 数据收集 CNAME 和跨域跟踪
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 数据收集 CNAME 和跨域跟踪{#data-collection-cnames-and-cross-domain-tracking}

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方 Cookie 的浏览器中，Cookie 是由数据收集服务器在访客 ID 请求期间设置的。该 Cookie 允许访客 ID 服务在使用同一 Experience Cloud 组织 ID 配置的所有域上返回相同的 Experience Cloud 访客 ID。

在拒绝第三方 Cookie 的浏览器中，将会为每个域分配一个新的 Experience Cloud 访客 ID。

demdex.net Cookie 允许访客 ID 服务提供与 Analytics 中的 s_vi Cookie 相同级别的跨域跟踪，不过，某些浏览器会接受 demdex.net Cookie 并跨域使用，但是其他一些浏览器则拒绝。

## 数据收集 CNAME {#section-48fd186d376a48079769d12c4bd9f317}

过去数据收集服务器在设置 Analytics Cookie 时，许多客户都配置了数据收集服务器 CNAME 记录作为[第一方 Cookie 实施](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/)的一部分，以避免浏览器拒绝第三方 Cookie 的问题。这个过程是将您的数据收集服务器域配置成与您的网站域相匹配，从而将访客 ID Cookie 设置为第一方 Cookie。

由于访客 ID 服务使用 JavaScript 直接在当前网站的域上设置访客 Cookie，因此不再需要采用这种配置来设置第一方 Cookie。

具有单一 Web 属性（单一域）的客户可以从使用数据收集 CNAME 中迁移出来，改为使用其默认的数据收集主机名（`omtrdc.net` 或 `2o7.net`）。

然而，使用 CNAME 进行数据收集有一个额外的好处，即，您可以在不接受第三方 Cookie 的浏览器中跟踪往来于主登录域和其他域之间的访客。拥有多个 Web 属性（多个域）的客户可以从继续使用数据收集 CNAME 获益。以下部分解释了跨域访客跟踪的工作原理。

## CNAME 如何启用跨域跟踪 {#section-78925af798e24917b9abed79de290ad9}

由于可以在 Apple Safari 和其他一些浏览器的第三方上下文中使用第一方 Cookie，CNAME 允许您跟踪主域和其他一些使用相同跟踪服务器的域之间的客户。

例如，您的主站点为 `mymainsite.com`。您将 CNAME 记录配置为指向安全的数据收集服务器：`smetrics.mymainsite.com`。

当用户访问 `mymainsite.com` 时，数据收集服务器将设置 ID 服务 Cookie。此操作是允许的，因为数据收集服务器的域与网站的域相匹配，也就是我们所说的在&#x200B;*第一方上下文*&#x200B;中使用 Cookie，或者说是使用&#x200B;*第一方 Cookie*。

如果您在其他站点（如 `myothersiteA.com` 和 `myothersiteB.com`）上也使用同样的数据收集服务器，那么当访客稍后访问这些站点时，访问 `mymainsite.com` 期间设置的 Cookie 将在 HTTPS 请求中发送给数据收集服务器（记住，浏览器会使用所有 HTTPS 请求将域的所有 Cookie 发送给该域，即使该域与当前网站的域不匹配也不例外）。这就是我们所说的在&#x200B;*第三方上下文*&#x200B;中使用 Cookie，或者说是使用&#x200B;*第三方 Cookie*，从而实现在其他域上使用同样的访客 ID。请注意，浏览器处理第三方上下文中 Cookie 的方式与处理第一方 Cookie 的方式有所不同。

*注意：Safari 会阻止第三方上下文中的所有 Cookie，而不管它们是如何设置的。*

因此，您的收集域应当为人们通常访问的域，以便系统能够在多个域上对访客进行识别。如果没有用于数据收集域的&#x200B;*通用*&#x200B;域，那么维护数据收集域的 CNAME 在跨域方面并没有任何优势。如果最先访问的不是主登录网站，那么访客在二级网站和主网站上将被视为不同的访客。

## 通过 Experience Cloud Identity 服务启用 CNAME 支持{#section-25d4feb686d944e3a877d7aad8dbdf9a}

通过设置 `visitor.marketingCloudServerSecure` 变量，可以启用数据收集服务器 CNAME 支持。
