---
description: 内容安全策略 (CSP) 是一项 HTTP 标头和安全功能，允许浏览器控制在网页上加载的资源类型。如果您使用 ID 服务，并且具有严格的 CSP 以使用白名单接受来自受信任域的资源，请参阅此部分内容。您需要将此处所列的 Adobe 域添加到您的 CSP 白名单中。
keywords: ID 服务
seo-description: 内容安全策略 (CSP) 是一项 HTTP 标头和安全功能，允许浏览器控制在网页上加载的资源类型。如果您使用 ID 服务，并且具有严格的 CSP 以使用白名单接受来自受信任域的资源，请参阅此部分内容。您需要将此处所列的 Adobe 域添加到您的 CSP 白名单中。
seo-title: 内容安全策略和 Experience Cloud ID 服务
title: 内容安全策略和 Experience Cloud ID 服务
uuid: 7399edf3-01c1-4730-834e-e2 dd2 c5791 ff
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 内容安全策略和 Experience Cloud ID 服务 {#content-security-policies-and-the-experience-cloud-id-service}

内容安全策略 (CSP) 是一项 HTTP 标头和安全功能，允许浏览器控制在网页上加载的资源类型。如果您使用 ID 服务，并且具有严格的 CSP 以使用白名单接受来自受信任域的资源，请参阅此部分内容。您需要将此处所列的 Adobe 域添加到您的 CSP 白名单中。

## CSP 内容回顾 {#section-5fde5c00a678455c914b8307a8caab82}

CSP 使用 HTTP 标头 `Content-Security-Policy` 来控制浏览器在页面上接受或加载的资源类型。应用 CSP 可帮助您防止以下情况发生：

* 来源未知或未包含在白名单中时加载 JavaScript 文件。
* 跨网站脚本 (XXS) 攻击。
* 数据注入攻击。
* 网站污损攻击。
* 恶意软件分发。

CSP 的使用很常见且易于理解。本文档的目的并不在于详细介绍 CSP（请访问下面的相关信息链接，以了解更多信息）。本文档的重点是让您了解在使用 Adobe 域并且具有严格的安全策略时，应该将哪些 Adobe 域名添加到 CSP。通过添加这些域，访问您网站的访客浏览器可以高效调用您使用的 Experience Cloud 资源。

## 要添加到白名单的 Experience Cloud 域 {#section-30693e9a96834edfbf04de9e698cf2aa}

对于下表中列出的您所使用的每个 Experience Cloud 解决方案或服务，请将下面的域名或 URL 添加到您的 CSP。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 解决方案或服务 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含以下域名： </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含 <span class="codeph">*.tt.omtrdc.net</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>访客 ID 服务</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含 <span class="codeph">*.demdex.net</span>。 </p> <p><span class="codeph"> demdex. net</span> 域调用用于生成 <a href="../introduction/cookies.md" format="dita" scope="local"> Cookie和Experience Cloud ID服务</a> 以及ID同步。另请参阅<a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">了解 Demdex 域调用</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ This]
>
>* [内容安全策略参考](https://content-security-policy.com/)
>* [MDN：内容安全策略](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia：内容安全策略](https://en.wikipedia.org/wiki/Content_Security_Policy)

