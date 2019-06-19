---
description: Experience Platform Identity Service替换旧版Analytics访客ID方法。
keywords: ID 服务
seo-description: Experience Platform Identity Service替换旧版Analytics访客ID方法。
seo-title: 设置 Analytics 和 Experience Cloud ID
title: 设置 Analytics 和 Experience Cloud ID
uuid: 421cf597-a3 e0-4ca3-8ce8-d0 c80 cbb6 aca
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 设置 Analytics 和 Experience Cloud ID{#setting-analytics-and-experience-cloud-ids}

Experience Platform Identity Service替换旧版Analytics访客ID方法。

实施 ID 服务后，此代码可在 AppMeasurement 之前执行。ID 服务可检索 Experience Cloud ID 和 Analytics ID，以便在加载 AppMeasurement 时，将这些值准备就绪。

加载 AppMeasurement 时，将从 ID 服务请求 Experience Cloud ID 值和 Analytics ID 值，并会将这些值随每次服务器调用发送至数据收集。由于 ID 服务可以确定访客 ID 并将其传送至 AppMeasurement，所以在执行 AppMeasurement JavaScript 文件之前，必须对每个页面添加并实施 ID 服务。

## Analytics ID 流程的变化 {#section-79bb86ae63f546419bb1a7ef5e710462}

迁移到 [!DNL Experience Cloud] ID 服务后，主要的变化是：ID Cookie 会使用 JavaScript 进行设置，而不是在由数据收集 Web 服务器返回的 HTTP 标头中进行设置。为了让您了解此变化，下面的部分介绍了如何使用这两种方法设置 Cookie。

**HTTP 标头**

来自 Web 服务器的 HTTP 响应可在浏览器中设置 Cookie。这就是 `s_vi` Cookie的设置方式。`s_vi` cookie可识别Analytics访客。设置完 Cookie 后，所有后续 HTTP 请求会将 Cookie 发送至该服务器。

请求发送至 Adobe 数据收集服务器后，将检查标头是否存在 `s_vi` Cookie。如果此 Cookie 位于请求中，则将其用于识别访客。如果此 Cookie 不在请求中，则服务器会生成一个唯一的 [!DNL Experience Cloud] ID，并将其设置为 HTTP 响应标头中的 Cookie，然后随请求发送回来。此 Cookie 存储在浏览器中，并且会在后续访问网站期间被发送回数据收集服务器。进而可以通过访问量识别访客。

但是，某些浏览器（例如 Apple Safari）不接受第三方 Cookie。这些浏览器中设置的 Cookie 均来自于域，而并非当前网站。此外，如果访客此前未曾访问该域，Safari 则会阻止第三方域上的 Cookie。例如，如果您在 `mysite.com` 上，您的数据收集服务器为 `mysite.omtrdc.net`，那么从 `mysite.omtrdc.net` 的 HTTP 标头中返回的 Cookie 可能会遭到浏览器的拒绝。

要避免此问题，许多客户为其数据收集服务器实施了 CNAME 记录。这是[第一方 Cookie 实施](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/)策略的一个有效部分。如果 CNAME 记录被配置为将客户域上的主机名映射至数据收集服务器（例如，将 `metrics.mysite.com` 映射至 `mysite.omtrdc.net`），则可以存储 [!DNL Experience Cloud] ID Cookie，因为数据收集域现在与网站的域相匹配。这增加了存储 ID 服务 Cookie 的可能性。但是，这也会带来一些开销，因为您需要为数据收集服务器配置 CNAME 记录并维护 SSL 证书。

**JavaScript**

JavaScript 可读写在第一方域（当前网站的域）中设置的 Cookie。[!DNL Experience Cloud] ID 服务可使用此方法来设置包含所有访客 ID 的 `AMCV_###@AdobeOrg` Cookie，这样一来，跟踪服务器的域便不再需要匹配网站的域，即可存储访客 ID Cookie。在大多数情况下，这是设置 ID 服务 Cookie 的首选方法，因为该方法消除了 CNAME 记录和 SSL 证书的开销。

然而，有少数情况是将 Cookie 设置在 HTTP 标头中，这样有利于跨域跟踪，相关内容将在[数据收集 CNAME 和跨域跟踪](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d)部分进行介绍。

## 自定义 Analytics ID {#section-b6a7bd19e9ff432390010062450808f6}

使用 `s.visitorID` 设置客户 ID 是在 Analytics 中标识用户的一种方法。但是，如果在集成中使用 ID 服务导出或导入 Analytics 数据，则当访客使用 `s.visitorID`.

这包括但不限于，共享的受众、Analytics for Target (A4T) 和客户属性。对于这些集成，不支持设置自定义 Analytics ID。

## Analytics 访客 ID 订购 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

当部署了访客 ID 服务后，有五种方法可用来在 Analytics 中识别访客（按优先顺序列在下表中）：

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用顺序 </th> 
   <th colname="col2" class="entry"> 查询参数（收集方法） </th> 
   <th colname="col3" class="entry"> 显示时间 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>已设置 s.visitorID </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>在部署 <span class="keyword"> Experience Cloud</span> ID服务或配置 <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> 了宽限期</a> 之前，访客有一个现有的s_ vi cookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid（由 Experience Cloud 访客 ID 服务设置的 AMCV_ Cookie） </p> </td> 
   <td colname="col3"> <p>访客的浏览器接受第一方 Cookie </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external">fid（H.25.3 或更高版本上的回退 Cookie，或者 AppMeasurement for JavaScript）</a> </p> </td> 
   <td colname="col3"> <p>浏览器不接受第三方 Cookie，并且将 Analytics 跟踪服务器设置为第三方跟踪服务器。 </p> <p> <p>注意：<span class="codeph">fid</span> 是旧版标识符，如果您已经在网站上实施了 ID 服务，则不会使用 fid。在这种情况下，不需要 <span class="codeph"> fid</span> ，因为第一方的 <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV cookie会</a> 使其废弃。之所以保留下来，是为了支持旧版代码，同时也出于一些历史原因。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP 地址、用户代理、网关 IP 地址</a> </p> </td> 
   <td colname="col3"> <p>访客的浏览器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

在许多情况下，您可能会在一次调用中看到 2 个或 3 个不同的 ID，但是 Analytics 会将该列表中显示的第一个 ID 用作正式的 [!DNL Experience Cloud] ID。例如，如果您正在设置一个自定义访客 ID （包含在“vid”查询参数中），那么该 ID 将在同一次点击中出现的其他 ID 之前被使用。

>[!MORE_ LIKE_ This]
>
>* [Analytics ID 操作顺序](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

