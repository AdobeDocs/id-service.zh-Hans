---
description: 有关与Experience Cloud Identity Service使用Analytics相关的功能、功能和问题的常见问题解答。
keywords: Experience Cloud Identity Service
seo-description: 有关在Identity Service使用Analytics的功能、功能和问题的常见问题解答。
seo-title: 分析和标识服务常见问题解答
title: 分析和标识服务常见问题解答
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

有关在Identity Service使用Analytics的功能、功能和问题的常见问题解答。

## 跟踪服务器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何查找我的跟踪服务器信息？**

每一段正确配置的 AppMeasurement 代码均包含您的跟踪服务器信息。

但是，客户有时可能会将他们的 Analytics AppMeasurement 文件拆分为多个不同的文件。例如，有些客户可能会将配置变量放置在一个文件中，将插件放置在第二个文件中，再将 AppMeasurement 代码放置在第三个文件中。不建议客户采取这种做法。

如果您找不到自己的跟踪服务器信息，则可能是因为您的 Analytics 实例配置不正确。如果您找不到自己的跟踪服务器信息，请联系[客户关怀团队](https://helpx.adobe.com/marketing-cloud/contact-support.html)。

**如果我使用标识服务并更改跟踪服务器，会出现什么情况？**

对于已经被标识服务识别的用户，没有任何变化。尚未迁移到标识服务且仍通过分析cookie识别的旧访客将被剪辑。受影响的用户数取决于Identity Service处于活动状态的期限。例如，“标识服务”处于活动状态的实施可能比“身份服务”处于活动状态已有个月的实施用户有更多旧版用户，因为返回站点的用户会被迁移。

## 实施和配置 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**是否必须设置 CNAME 才能跨域跟踪访客？**

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方 Cookie 的浏览器中，会在请求检索访客 ID 期间，在 [demdex.net 域](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)中设置一个 Cookie。此Cookie允许标识服务在使用同一组织ID配置的所有域上返回同一Experience Cloud访客ID。在拒绝第三方 Cookie 的浏览器中，将会为每个域分配一个新的 Experience Cloud 访客 ID。

即使配置了 CNAME，如果在不支持第三方 Cookie 的浏览器中最先访问的不是主登录网站，那么访客在辅助网站和主登录网站上将被视为不同的访客。

**为何 Analytics 请求中没有 Experience Cloud ID (MID) 参数？**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you've upgraded to a supported version of AppMeasurement.

**我的站点是否可以使用H代码和AppMeasurement for JavaScript使用Identity Service？**

能。只要这两个文件引用的是同一个 VisitorAPI.js 文件，就可以在您的网站中结合使用 H 代码和 AppMeasurement for JavaScript。

但是，visitorAPI.js 代码版本 1.6 或更高版本不支持 H 代码。如果您想要升级到 visitorAPI.js v 1.6（或更高版本），则不能继续使用 H 代码。

**什么是宽限期？如何配置宽限期？**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**为何需要迁移到实时数据收集(RDC)才能使用Identity Service？**

RDC 除了具有全局性能的优势之外，还可以确保您的实施能够为将来利用 Adobe 前沿全局网络的新功能做好准备。请参阅 [Analytics 要求：区域数据收集 (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)。

## 报表 {#section-123cd55a32e54a45a23beb140becfa8f}

**在将Analytics与Identity Service一起使用时，有哪些可能导致出现差异？**

使用标识服务时出现的常见错误包括：

* 持续使用旧版 s_vi Cookie。这可能会导致数据收集方面的差异。
* 在访客从调查导航到弹出窗口时，对访客进行重复计数。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**当标识服务无法设置AMCV cookie时，Analytics中会出现什么情况？**

可能会出现以下三种情况，在每种情况下，Analytics 的新访客数据均会受到影响：

1. 最终用户在 AMCV Cookie 成功设置（在 30 秒的超时时限内）之前离开页面。

   如果访客在页面完成加载之前离开页面，则不会发送 Analytics 点击。在这种情况下，Analytics 将不会收到相应数据，并且会认为数据是因为提前关闭页面而丢失的。根据我们的测试（测试包括一些偏远的地理位置），我们发现这种情况所涉及的流量平均少于 1%。请务必注意，这种情况有时甚至不存在标识服务-这是包含在页面底部的Analytics数据收集代码的伪像。

1. 由于连接或浏览器“旋转”，最终用户未在30秒超时窗口中分配Identity Service或Analytics ID。

   标识服务和分析ID都将不会设置，访客将被分配一个客户端ID。虽然这允许捕获 Analytics 数据，但是在后续页面上设置了 Analytics ID 后，访客的配置文件将会中断。客户端 ID 还与存储在 Audience Manager 或 Analytics 中的任何现有访客配置文件都不匹配。此外，如果将两个不同的域发送到同一个报表包，则客户端 ID 会在 Analytics 中显示为两个不同的访客。

1. 在30秒超时窗口内未分配最终用户身份服务ID，但分配了标准Analytics跟踪ID且未启用宽限期。

   由于使用了基于客户端的 ID，第 3 种情况的后果与第 2 种情况相同。

>[!TIP]
>
>在默认设置下使用 VisitorAPI.js 和 AppMeasurement.js 的最新更新，应该可以避免上述三种情况（虽不太可能出现）所产生的任何严重或重大影响。

>[!MORE_LIKE_THIS]
>
>* [客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)

