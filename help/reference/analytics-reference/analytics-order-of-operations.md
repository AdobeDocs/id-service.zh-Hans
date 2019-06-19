---
description: 部署访客 ID 服务后，可以在 Analytic 以 5 种方式识别访客。
keywords: ID 服务
seo-description: 部署访客 ID 服务后，可以在 Analytic 以 5 种方式识别访客。
seo-title: Analytics ID 操作顺序
title: Analytics ID 操作顺序
uuid: cb1d136e-093f-43b0e1-96f1e61fda0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Analytics ID 操作顺序{#order-of-operations-for-analytics-ids}

部署访客 ID 服务后，可以在 Analytic 以 5 种方式识别访客。

在许多情况下，您可能会在一次调用中看到 2 个或 3 个不同的 ID，但是 Analytics 会将该列表中显示的第一个 ID 用作正式的 [!DNL Experience Cloud] ID。例如，假如您设置了一个自定义访客 ID（包含在 `vid` 查询参数中），将会使用该 ID，而不是同一点击中可能出现的其他 ID。有关更多信息，请参阅 [设置Analytics和Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) 。

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
   <td colname="col1"> <p> <b><sup>第 1</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>设置 <span class="codeph">s.visitorID</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b><sup>第 2</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>在部署 <span class="keyword"> Experience Cloud</span> ID服务或配置 <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> 了宽限期</a> 之前，访客有一个现有的s_ vi cookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b><sup>第 3</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local">Experience Cloud ID (MID)</a> </p> </td> 
   <td colname="col3"> <p>访客的浏览器接受第一方 Cookie。此参数通过 AMCV Cookie 设置。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b><sup>第 4</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external">fid（H.25.3 或更高版本上的回退 Cookie，或者 AppMeasurement for JavaScript）</a> </p> </td> 
   <td colname="col3"> <p>浏览器不接受第三方 Cookie，并且将 Analytics 跟踪服务器设置为第三方跟踪服务器。 </p> <p> <p>注意：<span class="codeph">fid</span> 是旧版标识符，如果您已经在网站上实施了 ID 服务，则不会使用 fid。在这种情况下，不需要 <span class="codeph"> fid</span> ，因为第一方的 <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV cookie会</a> 使其废弃。之所以保留下来，是为了支持旧版代码，同时也出于一些历史原因。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b><sup>第 5</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP 地址、用户代理、网关 IP 地址</a> </p> </td> 
   <td colname="col3"> <p>访客的浏览器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

