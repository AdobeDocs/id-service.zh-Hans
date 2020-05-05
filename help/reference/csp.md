---
description: 内容安全策略(CSP)是HTTP头和安全功能，它使浏览器能够控制在网页上加载的资源类型。 如果您使用ID服务并有严格的CSP，则请查看本节，这些CSP使用白名单来接受来自受信任域的资源。 您需要将此处列出的Adobe域添加到您的CSP白名单中。
keywords: ID Service
seo-description: 内容安全策略(CSP)是HTTP头和安全功能，它使浏览器能够控制在网页上加载的资源类型。 如果您使用ID服务并有严格的CSP，则请查看本节，这些CSP使用白名单来接受来自受信任域的资源。 您需要将此处列出的Adobe域添加到您的CSP白名单中。
seo-title: 内容安全策略和 Experience Cloud Identity 服务
title: 内容安全策略和 Experience Cloud Identity 服务
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 内容安全策略和 Experience Cloud Identity 服务{#content-security-policies-and-the-experience-cloud-id-service}

内容安全策略(CSP)是HTTP头和安全功能，它使浏览器能够控制在网页上加载的资源类型。 如果您使用ID服务并有严格的CSP，则请查看本节，这些CSP使用白名单来接受来自受信任域的资源。 您需要将此处列出的Adobe域添加到您的CSP白名单中。

## CSP评论 {#section-5fde5c00a678455c914b8307a8caab82}

CSP 使用 HTTP 标头 `Content-Security-Policy` 来控制浏览器在页面上接受或加载的资源类型。应用CSP可以帮助您防止：

* 如果源未知或未包含在白名单中，则从加载JavaScript文件。
* 跨站点脚本(XXS)攻击。
* 数据注入攻击。
* 现场破坏攻击。
* 恶意软件分发。

CSP的使用是常见的，也是众所周知的。 本文档并非详细说明CSP的目的（有关详细信息，请参见下面的相关信息链接）。 重要的是，如果您使用CSP并有严格的安全策略，您应该添加哪些Adobe域名。 添加这些域后，访问您网站的访客浏览器会对您使用的Experience Cloud资源进行重要调用。

## 要添加到白名单的 Experience Cloud 域 {#section-30693e9a96834edfbf04de9e698cf2aa}

为您使用的每个列表Experience Cloud解决方案或服务将这些域名或URL添加到您的CSP。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud解决方案或服务 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>修改CSP以包含以下内容： </p> <p> 
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
   <td colname="col1"> <p> <b>Experience Cloud ID 服务和 Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含以下域。</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>如果您使用 Adobe Launch 来部署标记，则还必须将 <code>https://assets.adobedtm.com</code> 添加到域列表。</li></ul></p> <p><span class="codeph">demdex.net</span> 域调用可用于生成 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 和 Experience Cloud Identity 服务</a>及 ID 同步。另请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">了解 Demdex 域调用</a>。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 插件</b> </p> </td> 
 <td colname="col2"> <p>修改您的 CSP 以包含 *.adobe.com。**注意**：如果您在 2020 年 1 月之前已经安装 Activity Map，您的浏览器仍会看到对 *.omniture.com 的初始请求，但会被重定向到 *.adobe.com。 </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [内容安全策略参考](https://content-security-policy.com/)
>* [MDN：内容安全策略](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CSP)
>* [Wikipedia：内容安全策略](https://en.wikipedia.org/wiki/Content_Security_Policy)

