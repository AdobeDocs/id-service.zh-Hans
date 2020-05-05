---
description: 与将 Analytics 和 Experience Cloud Identity 服务结合使用相关的特性、功能和问题的常见问题解答。
keywords: Experience Cloud Identity Service
seo-description: 与将 Analytics 和 Identity 服务结合使用相关的特性、功能和问题的常见问题解答。
seo-title: Analytics 和 Identity 服务常见问题解答
title: Analytics 和 Identity 服务常见问题解答
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Analytics 和 Identity 服务常见问题解答{#analytics-and-id-service-faqs}

与将 Analytics 和 Identity 服务结合使用相关的特性、功能和问题的常见问题解答。

## 跟踪服务器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何找到跟踪服务器信息？**

每个正确配置的AppMeasurement代码都包含跟踪服务器信息。

但有时，客户可能会将其Analytics AppMeasurement文件分解为单独的文件。 例如，一些客户可能将配置变量放在一个文件中，对插件使用另一个文件，然后将AppMeasurement代码放到第三个文件中。 不建议这样做。

如果找不到跟踪服务器信息，则可能无法正确配置Analytics实例。 如果 [找不到](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html) 跟踪服务器信息，请与客户关怀联系。

**如果我在使用 Identity 服务时更改了我的跟踪服务器，会发生什么？**

对于已经由 Identity 服务识别的用户，不会发生任何变化。尚未迁移到 Identity 服务且仍然由 Analytics Cookie 识别的旧用户将被挂起。受影响用户的数量取决于 Identity 服务处于活动状态的时间。例如，对于 Identity 服务活动时间为一周的实施，其旧用户数量可能多于活动时间为六个月的实施，因为回访网站的用户已经迁移。

## 实施和配置 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**我是否必须设置CNAME来跨域跟踪访客?**

如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。

In browsers that accept third-party cookies, a cookie is set in the [demdex.net domain](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/reference/demdex-calls.html) during the request to retrieve a visitor ID. 该 Cookie 允许 Identity 服务在使用同一组织 ID 配置的所有域上返回相同的 Experience Cloud 访客 ID。在拒绝第三方Cookie的浏览器中，将为每个域分配一个新的Experience Cloud访客ID。

即使配置了CNAME，如果未先访问主入口站点，在辅助站点和不接受第三方Cookie的浏览器中，访客在主站点上的标识也会有所不同。

**为什么Experience Cloud ID(MID)参数不在Analytics请求中？**

如果 Identity 服务正确返回了信息，但是您没有看到 `MID` 参数，请确保已将 AppMeasurement 升级到支持的版本。

**我的网站能否对 Identity 服务使用 H 代码和 AppMeasurement for JavaScript？**

能。只要两个文件引用同一个VisitorAPI.js文件，您就可以在整个站点中混合使用H代码和AppMeasurement for JavaScript。

但是，visitorAPI.js代码版本1.6或更高版本不支持H代码。 如果要升级到visitorAPI.js v 1.6（或更高版本），则无法继续使用H代码。

**宽限期是什么？如何配置宽限期？**

请参阅 [Identity 服务宽限期](../reference/analytics-reference/grace-period.md)并联系[客户关怀团队](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)。

**为何需要迁移到实时数据收集 (RDC) 才能使用 Identity 服务？**

RDC增加了全局性能优势，并且需要确保您的实施已准备好迎接利用Adobe全球边缘注释网络的即将推出的功能。 See [Analytics Requirements: Regional Data Collection (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## 报表 {#section-123cd55a32e54a45a23beb140becfa8f}

**在将 Analytics 和 Identity 服务结合使用时，导致出现差异的原因可能有哪些？**

导致在使用 Identity 服务时出现差异的常见原因包括：

* 继续使用旧版s_vi cookie。 这导致数据收集不一致。
* 多次在访客从调查导航到弹出窗口时对其进行计数。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**当 Identity 服务无法设置 AMCV Cookie 时，Analytics 中会出现什么情况？**

有三种潜在情形会影响新访客的Analytics数据：

1. 最终用户在AMCV cookies设置成功之前（在30秒超时窗口内）离开页面。

   如果访客在加载完页面之前离开页面，则不会发送Analytics点击。 分析将不会从此方案接收数据，并将考虑由于页面提前关闭而丢失的数据。 根据我们的测试（包括边远地区），我们发现，这种情况平均占流量的比例不到1%。 需要注意的是，即使不存在 Identity 服务，这种情况有时也会发生，因为它是在页面底部包含 Analytics 数据收集代码所导致的人为后果。

1. 由于连接速度缓慢或浏览器一直处于加载状态，未在 30 秒的超时时限内为最终用户分配 Identity 服务 ID 或 Analytics ID。

   Identity 服务 ID 和 Analytics ID 都不会进行设置，而是会为访客分配一个客户端 ID。虽然这允许捕获Analytics数据，但在后续页面上设置Analytics ID时，访客的用户档案将被中断。 客户端ID也与存储在访客管理器或分析中的任何现有用户档案受众不匹配。 如果将两个单独的域发送到同一报告包，则此客户端ID在Analytics中也将显示为两个不同的访客。

1. 未在 30 秒的超时时限内为最终用户分配 Identity 服务 ID，但是为其分配了标准的 Analytics 跟踪 ID，同时未启用宽限期。

   由于使用了基于客户端的 ID，第 3 种情况的后果与第 2 种情况相同。

>[!TIP]
>
>在默认设置下使用 VisitorAPI.js 和 AppMeasurement.js 的最新更新，应该可以避免上述三种情况（虽不太可能出现）所产生的任何严重或重大影响。

>[!MORELIKETHIS]
>
>* [客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)

