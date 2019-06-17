---
description: 与将 Analytics 和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。
keywords: ID 服务
seo-description: 与将 Analytics 和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。
seo-title: Analytics 和 ID 服务常见问题解答
title: Analytics 和 ID 服务常见问题解答
uuid: 35ed79a9-ecCC-4b544-845-606f091 c73 b7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Analytics 和 ID 服务常见问题解答{#analytics-and-id-service-faqs}

与将 Analytics 和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。

## 跟踪服务器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何查找我的跟踪服务器信息？**

每一段正确配置的 AppMeasurement 代码均包含您的跟踪服务器信息。

但是，客户有时可能会将他们的 Analytics AppMeasurement 文件拆分为多个不同的文件。例如，有些客户可能会将配置变量放置在一个文件中，将插件放置在第二个文件中，再将 AppMeasurement 代码放置在第三个文件中。不建议客户采取这种做法。

如果您找不到自己的跟踪服务器信息，则可能是因为您的 Analytics 实例配置不正确。如果您找不到自己的跟踪服务器信息，请联系[客户关怀团队](https://helpx.adobe.com/marketing-cloud/contact-support.html)。

**如果我在使用 ID 服务时更改了我的跟踪服务器，会发生什么？**

对于已经由 ID 服务识别的用户，不会发生任何变化。尚未迁移到 ID 服务且仍然由 Analytics Cookie 识别的旧用户将被挂起。受影响用户的数量取决于 ID 服务处于活动状态的时间。例如，对于 ID 服务活动时间为一周的实施，其旧用户数量可能多于活动时间为六个月的实施，因为回访网站的用户已经迁移。

## 实施和配置 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**是否必须设置 CNAME 才能跨域跟踪访客？**

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方 Cookie 的浏览器中，会在请求检索访客 ID 期间，在 [demdex.net 域](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)中设置一个 Cookie。该 Cookie 允许 ID 服务在使用同一组织 ID 配置的所有域上返回相同的 Experience Cloud 访客 ID。在拒绝第三方 Cookie 的浏览器中，将会为每个域分配一个新的 Experience Cloud 访客 ID。

即使配置了 CNAME，如果在不支持第三方 Cookie 的浏览器中最先访问的不是主登录网站，那么访客在辅助网站和主登录网站上将被视为不同的访客。

**为何 Analytics 请求中没有 Experience Cloud ID (MID) 参数？**

如果 ID 服务正确返回了信息，但是您没有看到 `MID` 参数，请确保已将 AppMeasurement 升级到支持的版本。

**我的网站能否对 ID 服务使用 H 代码和 AppMeasurement for JavaScript？**

可以。只要这两个文件引用的是同一个 VisitorAPI.js 文件，就可以在您的网站中结合使用 H 代码和 AppMeasurement for JavaScript。

但是，visitorAPI.js 代码版本 1.6 或更高版本不支持 H 代码。如果您想要升级到 visitorAPI.js v 1.6（或更高版本），则不能继续使用 H 代码。

**什么是宽限期？如何配置宽限期？**

请参阅 [ID服务宽限期](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) 并联系 [客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)。

**为何需要迁移到实时数据收集 (RDC) 才能使用 ID 服务？**

RDC 除了具有全局性能的优势之外，还可以确保您的实施能够为将来利用 Adobe 前沿全局网络的新功能做好准备。请参阅 [Analytics 要求：区域数据收集 (RDC)](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)。

## 报表 {#section-123cd55a32e54a45a23beb140becfa8f}

**在将 Analytics 和 ID 服务结合使用时，导致出现差异的原因可能有哪些？**

导致在使用 ID 服务时出现差异的常见原因包括：

* 持续使用旧版 s_vi Cookie。这可能会导致数据收集方面的差异。
* 在访客从调查导航到弹出窗口时，对访客进行重复计数。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**当 ID 服务无法设置 AMCV Cookie 时，Analytics 中会出现什么情况？**

可能会出现以下三种情况，在每种情况下，Analytics 的新访客数据均会受到影响：

1. 最终用户在 AMCV Cookie 成功设置（在 30 秒的超时时限内）之前离开页面。

   如果访客在页面完成加载之前离开页面，则不会发送 Analytics 点击。在这种情况下，Analytics 将不会收到相应数据，并且会认为数据是因为提前关闭页面而丢失的。根据我们的测试（测试包括一些偏远的地理位置），我们发现这种情况所涉及的流量平均少于 1%。记住，这种情况有时甚至不会出现，甚至不存在MCID服务-这是包含在页面底部的Analytics数据收集代码的伪像。

1. 由于连接速度缓慢或浏览器一直处于加载状态，未在 30 秒的超时时限内为最终用户分配 ID 服务 ID 或 Analytics ID。

   ID 服务 ID 和 Analytics ID 都不会进行设置，而是会为访客分配一个客户端 ID。虽然这允许捕获 Analytics 数据，但是在后续页面上设置了 Analytics ID 后，访客的配置文件将会中断。客户端 ID 还与存储在 Audience Manager 或 Analytics 中的任何现有访客配置文件都不匹配。此外，如果将两个不同的域发送到同一个报表包，则客户端 ID 会在 Analytics 中显示为两个不同的访客。

1. 未在 30 秒的超时时限内为最终用户分配 ID 服务 ID，但是为其分配了标准的 Analytics 跟踪 ID，同时未启用宽限期。

   由于使用了基于客户端的 ID，第 3 种情况的后果与第 2 种情况相同。

>[!TIP]
>
>使用默认设置对VisitorAPI. js和AppMeasurement. js的最新更新应避免上述三个不可能的情况造成严重或显著的影响。

>[!MORE_ LIKE_ This]
>
>* [客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)

