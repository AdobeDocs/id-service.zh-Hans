---
description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
keywords: 操作顺序;ID 服务
seo-description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
seo-title: 数据收集 CNAME 和跨域跟踪
title: 数据收集 CNAME 和跨域跟踪
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 053d45656e941adc1950d49099c30da1d9a72aa0
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 100%

---


# 数据收集 CNAME 和跨域跟踪{#data-collection-cnames-and-cross-domain-tracking}

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方 Cookie 的浏览器中，数据收集服务器会在请求访客 ID 期间设置一个 Cookie。该 Cookie 允许访客 ID 服务在使用同一 Experience Cloud 组织 ID 配置的所有域上返回相同的 Experience Cloud 访客 ID。

在拒绝第三方 Cookie 的浏览器中，会为每个域分配一个新的 Experience Cloud 访客 ID。

通过 demdex.net Cookie，访客 ID 服务能够在 Analytics 中提供与 s_vi Cookie 相同级别的跨域跟踪，在 Analytics 中，该 Cookie 可被某些浏览器接受并跨域使用，但同时也会被其他浏览器拒绝。

## 数据收集 CNAME {#section-48fd186d376a48079769d12c4bd9f317}

在数据收集服务器设置 Analytics Cookie 时，许多客户都配置了数据收集服务器 CNAME 记录作为[第一方 Cookie 实施](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/ec-cookies/cookies-first-party.html)的一部分，以避免浏览器拒绝第三方 Cookie 的问题。此过程会将您的访客收集服务器域配置为与您的网站域相匹配，从而将访客 ID Cookie 设置为第一方 Cookie。

由于访客 ID 服务会使用 JavaScript 直接在当前网站的域上设置访客 Cookie，因此不再需要使用此配置来设置第一方 Cookie。

具有单一 Web 资产（单一域）的客户可以从使用数据收集 CNAME 中迁移出来，改为使用其默认的数据收集主机名（`omtrdc.net` 或 `2o7.net`）。

但是，使用 CNAME 进行数据收集还有另外一个好处，即允许您在不接受第三方 Cookie 的浏览器中的主登录域和其他域之间跟踪访客。对于具有多个 Web 资产（多个域）的客户，维护数据收集 CNAME 可能会使其受益。以下部分将介绍跨域访客跟踪的工作原理。

## 跨域跟踪 {#section-78925af798e24917b9abed79de290ad9}

在用户的隐私设置和浏览器设置允许的情况下，访客 ID 服务会使用 demdex.net 作为其跨域（但这些域归同一公司所有）跟踪访客的域。

CNAME 不提供其他跨域优势。例如，您的主站点为 `mymainsite.com`。您将 CNAME 记录配置为指向安全的数据收集服务器：`smetrics.mymainsite.com`。

当用户访问 `mymainsite.com` 时，数据收集服务器将设置 ID 服务 Cookie。此操作是允许的，因为数据收集服务器的域与网站的域相匹配，也就是我们所说的在&#x200B;*第一方上下文*&#x200B;中使用 Cookie，或者说是使用&#x200B;*第一方 Cookie*。

如果您在其他站点（如 `myothersiteA.com` 和 `myothersiteB.com`）上也使用同样的数据收集服务器，那么当访客稍后访问这些站点时，访问 `mymainsite.com` 期间设置的 Cookie 将在 HTTPS 请求中发送给数据收集服务器（记住，浏览器会使用所有 HTTPS 请求将域的所有 Cookie 发送给该域，即使该域与当前网站的域不匹配也不例外）。这称之为在&#x200B;*第三方上下文*&#x200B;中使用 Cookie，或简称为&#x200B;*第三方 Cookie*，即使您使用的是 CNAME 也是如此。Adobe 建议为每个唯一域使用一个 CNAME。

*注意：Safari 会阻止第三方上下文中的所有 Cookie，而不管它们是如何设置的。*

## 通过 Experience Cloud Identity 服务启用 CNAME 支持{#section-25d4feb686d944e3a877d7aad8dbdf9a}

通过设置 `visitor.marketingCloudServerSecure` 变量，可以启用数据收集服务器 CNAME 支持。
