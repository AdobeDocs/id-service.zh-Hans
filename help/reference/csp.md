---
description: 内容安全策略 (CSP) 是一种 HTTP 标头和安全功能，该功能使浏览器能够控制在网页上加载的资源类型。如果您使用 ID 服务并具有严格的 CSP（使用白名单接受来自受信任域的资源），请查看此部分内容。您需要将此处列出的 Adobe 域添加到您的 CSP 白名单中。
keywords: ID 服务
title: 内容安全策略和 Experience Cloud Identity 服务
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '547'
ht-degree: 100%

---

# 内容安全策略和 Experience Cloud Identity 服务{#content-security-policies-and-the-experience-cloud-id-service}

内容安全策略 (CSP) 是一种 HTTP 标头和安全功能，该功能使浏览器能够控制在网页上加载的资源类型。如果您使用 ID 服务并具有严格的 CSP（使用白名单接受来自受信任域的资源），请查看此部分内容。您需要将此处列出的 Adobe 域添加到您的 CSP 白名单中。

## CSP 审查 {#section-5fde5c00a678455c914b8307a8caab82}

CSP 使用 HTTP 标头 `Content-Security-Policy` 来控制浏览器在页面上接受或加载的资源类型。应用 CSP 可帮助阻止以下情况：

* 当源未知或未包含在白名单中时，阻止加载 JavaScript 文件。
* 跨站点脚本 (XXS) 攻击。
* 数据注入攻击。
* 网站篡改攻击。
* 恶意软件分发。

CSP 得到了广泛使用和认可。本文档并非旨在详细介绍 CSP（有关更多信息，请访问下面提供的相关信息链接）。让您了解在使用严格 CSP 策略时应该将哪些 Adobe 域名添加到 CSP 白名单中才是本文档的重点。添加这些域后，访问您网站的访客浏览器便可以对您使用的 Experience Cloud 资源进行重要调用。

## 要添加到白名单的 Experience Cloud 域 {#section-30693e9a96834edfbf04de9e698cf2aa}

对于您使用的每个 Experience Cloud 解决方案或服务，将这些域名或 URL 添加到您的 CSP 白名单中。

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
   <td colname="col2"> <p>修改您的 CSP 白名单以包含以下域： </p> <p> 
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
   <li>如果您使用 Adobe Launch 来部署标记，则还必须将 <code>https://assets.adobedtm.com</code> 添加到域列表。</li></ul></p> <p><span class="codeph">demdex.net</span> 域调用可用于生成 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 和 Experience Cloud Identity 服务</a>及 ID 同步。另请参阅<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans" format="https" scope="external">了解 Demdex 域调用</a>。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 插件</b> </p> </td> 
 <td colname="col2"> <p>修改您的 CSP 以包含 *.adobe.com。**注意**：如果您在 2020 年 1 月之前已经安装 Activity Map，您的浏览器仍会看到对 *.omniture.com 的初始请求，但会被重定向到 *.adobe.com。 </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>如果您对查询字符串参数应用了控制，请务必将参数“s_kwcid”和“ef_id”列入白名单。从技术上讲，Advertising Analytics 仅使用“s_kwcid”，但如果您选取 Ad Cloud Search 或 DSP，则它也使用“ef_id”。这些查询字符串参数采用的是字母数字。“s_kwcid”参数使用“!”字符，“ef_id”参数使用“:”字符。如果您在 URL 中阻止“!”字符，则还需要将该字符列入白名单。</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [内容安全策略参考](https://content-security-policy.com/)
>* [MDN：内容安全策略](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CSP)
>* [Wikipedia：内容安全策略](https://en.wikipedia.org/wiki/Content_Security_Policy)

