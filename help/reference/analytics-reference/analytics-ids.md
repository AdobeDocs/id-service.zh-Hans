---
description: Experience Cloud Identity 服务取代了旧版 Analytics 访客 ID 方法。
keywords: ID 服务
title: 设置 Analytics 和 Experience Cloud ID
exl-id: 7399ea16-d13e-452c-b8d9-8d0699566aa2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 98%

---

# 设置 Analytics 和 Experience Cloud ID{#setting-analytics-and-experience-cloud-ids}

Experience Cloud Identity 服务取代了旧版 Analytics 访客 ID 方法。

在实施 ID 服务后，此代码将在 AppMeasurement 之前执行。ID 服务会检索 Experience Cloud ID 和 Analytics ID，以便这两个 ID 值在加载 AppMeasurement 时可以使用。

加载 AppMeasurement 时，将从 ID 服务请求 Experience Cloud ID 和 Analytics ID 值，并在每次服务器调用中将这两个值发送到数据收集。由于 ID 服务可确定访客 ID 并轻松将该 ID 传递给 AppMeasurement，因此必须先在每个页面上包含并实施 ID 服务，然后再实施 AppMeasurement JavaScript 文件。

## 对Analytics ID流程所做的更改 {#section-79bb86ae63f546419bb1a7ef5e710462}

迁移到 [!DNL Experience Cloud] ID 服务后，主要的变化是：ID Cookie 会使用 JavaScript 进行设置，而不是在由数据收集 Web 服务器返回的 HTTP 标头中进行设置。为了解此更改，以下各部分将介绍如何使用这两种方法设置 Cookie。

**HTTP 标头**

来自 Web 服务器的 HTTP 响应将在浏览器中设置 Cookie。这就是 `s_vi` Cookie 的设置方式。`s_vi` Cookie 可识别 Analytics 访客。设置完 Cookie 后，所有后续 HTTP 请求会将 Cookie 发送至该服务器。

请求发送至 Adobe 数据收集服务器后，将检查标头是否存在 `s_vi` Cookie。如果此 Cookie 位于请求中，则将其用于识别访客。如果此 Cookie 不在请求中，则服务器会生成一个唯一的 [!DNL Experience Cloud] ID，并将其设置为 HTTP 响应标头中的 Cookie，然后随请求发送回来。Cookie 存储在浏览器中，并会在随后访问网站期间发送回数据收集服务器。如此一来，便可以在每次访问中识别访客。

但是，某些浏览器（如 Apple Safari）不接受第三方 Cookie。第三方 Cookie 是指在浏览器中从当前网站之外的其他域设置的 Cookie。此外，如果访客之前未访问过第三方域，Safari 还会阻止第三方域上的 Cookie。例如，如果您在 `mysite.com` 上，您的数据收集服务器为 `mysite.omtrdc.net`，那么从 `mysite.omtrdc.net` 的 HTTP 标头中返回的 Cookie 可能会遭到浏览器的拒绝。

要避免此问题，许多客户为其数据收集服务器实施了 CNAME 记录。这会成为[第一方 Cookie 实施](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=zh-Hans)策略的有效部分。如果 CNAME 记录被配置为将客户域上的主机名映射至数据收集服务器（例如，将 `metrics.mysite.com` 映射至 `mysite.omtrdc.net`），则可以存储 [!DNL Experience Cloud] ID Cookie，因为数据收集域现在与网站的域相匹配。这增加了对 ID 服务 Cookie 进行存储的可能性。但是，这确实会带来一些额外的开销，因为您需要配置 CNAME 记录并维护数据收集服务器的 SSL 证书。

**JavaScript**

JavaScript 可以读写在第一方域（当前网站的域）中设置的 Cookie。[!DNL Experience Cloud] ID 服务可使用此方法来设置包含所有访客 ID 的 `AMCV_###@AdobeOrg` Cookie，这样一来，跟踪服务器的域便不再需要匹配网站的域，即可存储访客 ID Cookie。在大多数情况下，这是设置 ID 服务 Cookie 的首选方式，因为它消除了由 CNAME 记录和 SSL 证书产生的开销。

<!---However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).-->

## 自定义Analytics ID {#section-b6a7bd19e9ff432390010062450808f6}

使用 `s.visitorID` 设置客户 ID 是在 Analytics 中标识用户的一种方法。但是，如果在集成中使用 ID 服务导出或导入 Analytics 数据，则当访客使用 `s.visitorID`。

这包括但不限于，共享的受众、Analytics for Target (A4T) 和客户属性。对于这些集成，不支持设置自定义 Analytics ID。

## Analytics访客ID顺序 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

部署访客 ID 服务后，可采用五种方式在 Analytics 中标识访客（这五种方式按优先顺序列在下表中）：

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用顺序 </th> 
   <th colname="col2" class="entry"> 查询参数（收集方法） </th> 
   <th colname="col3" class="entry"> 前提条件 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=zh-Hans" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>已设置 s.visitorID </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hans" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>在您部署 <span class="keyword">Experience Cloud ID 服务</span>之前，访客已拥有 s_vi Cookie，或者您已配置<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">宽限期</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid（由 Experience Cloud 访客 ID 服务设置的 AMCV_ Cookie） </p> </td> 
   <td colname="col3"> <p>访客的浏览器接受第一方 Cookie </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=zh-Hans" format="http" scope="external">fid（H.25.3 或更高版本上的回退 Cookie，或者 AppMeasurement for JavaScript）</a> </p> </td> 
   <td colname="col3"> <p>浏览器不接受第三方 Cookie，并且将 Analytics 跟踪服务器设置为第三方跟踪服务器。 </p> <p> <p>注意：<span class="codeph">fid</span> 是旧版标识符，如果您已经在网站上实施了 ID 服务，则不会使用 fid。在这种情况下，不再需要 <span class="codeph">fid</span>，因为第一方 <a href="../../introduction/cookies.md" format="dita" scope="local">AMCV Cookie</a> 使其过时。之所以保留下来，是为了支持旧版代码，同时也出于一些历史原因。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=zh-Hans" format="http" scope="external"> IP 地址、用户代理、网关 IP 地址</a> </p> </td> 
   <td colname="col3"> <p>访客的浏览器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

在许多情况下，您可能会在一次调用中看到 2 个或 3 个不同的 ID，但是 Analytics 会将该列表中显示的第一个 ID 用作正式的 [!DNL Experience Cloud] ID。例如，如果您正在设置一个自定义访客 ID （包含在“vid”查询参数中），那么该 ID 将在同一次点击中出现的其他 ID 之前被使用。

>[!MORELIKETHIS]
>
>* [Analytics ID 操作顺序](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)
