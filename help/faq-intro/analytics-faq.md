---
description: 与将 Analytics 和 Experience Cloud Identity 服务结合使用相关的特性、功能和问题的常见问题解答。
keywords: Experience Cloud Identity 服务
title: Analytics 和 Identity 服务常见问题解答
exl-id: 98aeca0d-41a2-4b18-b307-19a6de816e38
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 99%

---

# Analytics 和 Identity 服务常见问题解答{#analytics-and-id-service-faqs}

与将 Analytics 和 Identity 服务结合使用相关的特性、功能和问题的常见问题解答。

## 跟踪服务器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何查找跟踪服务器信息？**

每个正确配置的 AppMeasurement 代码都包含跟踪服务器信息。

但有时，客户可能会将其 Analytics AppMeasurement 文件拆分为若干文件。例如，一些客户可能将配置变量放在一个文件中，将插件放在第二个文件中，然后将 AppMeasurement 代码放在第三个文件中。不建议采取此做法。

如果找不到跟踪服务器信息，则可能无法正确配置 Analytics 实例。如果找不到跟踪服务器信息，请联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)。

**如果我在使用 Identity 服务时更改了我的跟踪服务器，会发生什么？**

对于已经由 Identity 服务识别的用户，不会发生任何变化。尚未迁移到 Identity 服务且仍然由 Analytics Cookie 识别的旧用户将被挂起。受影响用户的数量取决于 Identity 服务处于活动状态的时间。例如，对于 Identity 服务活动时间为一周的实施，其旧用户数量可能多于活动时间为六个月的实施，因为回访网站的用户已经迁移。

## 实施和配置 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**我是否必须设置 CNAME 才能跨域跟踪访客？**

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

在接受第三方 Cookie 的浏览器中，在检索访客 ID 的请求期间，会在 [demdex.net 域](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans)中设置 Cookie。该 Cookie 允许 Identity 服务在使用同一组织 ID 配置的所有域上返回相同的 Experience Cloud 访客 ID。在拒绝第三方 Cookie 的浏览器中，会为每个域分配一个新的 Experience Cloud 访客 ID。

即使配置了 CNAME，如果未先访问主要的登录网站，则在不接受第三方 Cookie 的浏览器中，访客在主网站和辅助网站上的标识将有所不同。

**为何 Experience Cloud ID (MID) 参数不在 Analytics 请求中？**

如果 Identity 服务正确返回了信息，但是您没有看到 `MID` 参数，请确保已将 AppMeasurement 升级到支持的版本。

**我的网站能否对 Identity 服务使用 H 代码和 AppMeasurement for JavaScript？**

能。只要两个文件引用同一个 VisitorAPI.js 文件，您就可以在网站中混合使用 H 代码和 AppMeasurement for JavaScript。

但是，VisitorAPI.js 代码版本 1.6 或更高版本不支持 H 代码。如果要升级到 VisitorAPI.js 版本 1.6（或更高版本），则将无法继续使用 H 代码。

**什么是宽限期？如何配置宽限期？**

请参阅 [Identity 服务宽限期](../reference/analytics-reference/grace-period.md)并联系[客户关怀团队](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)。

**为何需要迁移到实时数据收集 (RDC) 才能使用 Identity 服务？**

RDC 可提升全局性能，如果要确保您的实施已准备好接受即将推出的利用 Adobe 全球 Edge 备注网络的功能，则需要使用 RDC。请参阅 [Analytics 要求：区域数据收集 (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)

## 报告 {#section-123cd55a32e54a45a23beb140becfa8f}

**在将 Analytics 和 Identity 服务结合使用时，导致出现差异的原因可能有哪些？**

导致在使用 Identity 服务时出现差异的常见原因包括：

* 继续使用旧版 s_vi Cookie。这会导致数据收集出现不一致问题。
* 在访客从调查导航到弹出窗口时对访客进行重复计数。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**当 Identity 服务无法设置 AMCV Cookie 时，Analytics 中会出现什么情况？**

对于以下三种可能出现的情况，这会影响新访客的 Analytics 数据：

1. 最终用户在成功设置 AMCV Cookie（在 30 秒超时范围内）之前离开页面。

   如果访客在页面加载完成之前离开页面，则不会发送 Analytics 点击。在这种情况下，Analytics 不会收到数据，而是认为由于页面提前关闭而丢失数据。根据我们的测试（包括边远地区），我们发现这种情况对应的平均流量占比不到 1%。需要注意的是，即使不存在 Identity 服务，这种情况有时也会发生，因为它是在页面底部包含 Analytics 数据收集代码所导致的人为后果。

1. 由于连接速度缓慢或浏览器一直处于加载状态，未在 30 秒的超时时限内为最终用户分配 Identity 服务 ID 或 Analytics ID。

   Identity 服务 ID 和 Analytics ID 都不会进行设置，而是会为访客分配一个客户端 ID。虽然在这种情况下可以捕获 Analytics 数据，但如果在后续页面上设置了 Analytics ID，访客的配置文件将会中断。此外，客户端 ID 与存储在 Audience Manager 或 Analytics 中的任何现有访客配置文件都将不匹配。如果将两个不同的域发送到同一报表包，则此客户端 ID 还会在 Analytics 中显示为两个不同的访客。

1. 未在 30 秒的超时时限内为最终用户分配 Identity 服务 ID，但是为其分配了标准的 Analytics 跟踪 ID，同时未启用宽限期。

   由于使用了基于客户端的 ID，第 3 种情况的后果与第 2 种情况相同。

>[!TIP]
>
>在默认设置下使用 VisitorAPI.js 和 AppMeasurement.js 的最新更新，应该可以避免上述三种情况（虽不太可能出现）所产生的任何严重或重大影响。

>[!MORELIKETHIS]
>
>* [客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)
