---
description: 浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud ID 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。
keywords: ID 服务
seo-description: 浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud ID 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。
seo-title: Experience Cloud ID 服务中的 CORS 支持
title: Experience Cloud ID 服务中的 CORS 支持
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID 服务中的 CORS 支持 {#cors-support-in-the-experience-cloud-id-service}

浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud ID 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。

## 同域策略和 ID 服务请求的问题 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

同域策略是 Web 浏览器所实施的安全控制或限制。当在此级别实施时，Web 浏览器本身会确定是允许还是阻止从一个页面到另一个页面的资源请求。要确定请求是否是同域请求，浏览器将比较以下项：

* 统一资源标识符 (URI)
* 主机名（例如 http://www.my-webpage-example.com）
* 端口号（例如，分别用于 HTTP 和 HTTPS 请求的端口 80 和 440）

如果两个页面共享这些特征，则浏览器将允许请求成功，否则将阻止资源请求。

## CORS 可解决同域策略问题 {#section-76c87ec3295d447bab220c84f138c235}

CORS 提供了一种安全、有效的方式，可跨越不同的域请求资源。CORS 规范包括一组 HTTP 标头，浏览器将使用这些标头来发送、接收和评估资源请求。评估资源请求被称为 *`preflight check`*。浏览器和服务器可通过此检查确定允许或阻止的请求。预检检查对请求资源的应用程序、API 或脚本来说是透明的。在资源请求流程中，两个重要的标头是：

* `Origin`：识别请求源的请求标头。
* `Access-Control-Allow-Origin`：指示某个资源能否与请求者共享的响应标头。

下面我们看一看这些标头的工作方式。在此示例中，假设有一家金融服务公司在其网站 www.finance-website.com 上实施了 [!DNL Experience Cloud] ID 服务。下表定义了 CORS 请求和响应标头如何检查对资源的访问。

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 操作 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>请求</b> </p> </td> 
   <td colname="col2"> <p>加载金融公司页面时，浏览器向 <span class="codeph">dpm.demdex.net</span> 提出请求。也就是调用 ID 服务所使用的数据收集服务器 (DCS) 域。此跨域请求包含以下标头： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>响应</b> </p> </td> 
   <td colname="col2"> <p>来自 DCS 域的响应包含以下标头，它们可为金融公司的站点提供对所需资源的访问权限： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另请参阅 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用 CORS 的其他好处 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表描述了 CORS 为使用 ID 服务的客户带来的一些益处。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 好处 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>安全性提升</b> </p> </td> 
   <td colname="col2"> <p>CORS 使用 <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> 请求和传输数据。这种方法比 JSONP 请求更加安全。它可以确保没有办法执行可能包含在 DCS 响应中的任何 JavaScript。CORS XMLHttpRequest 响应负载由 ID 服务 JavaScript 解析，而不是简单地在回调函数中执行。 </p> <p> <p>注意：要接受 Cookie，<span class="codeph">XMLHttpRequest</span> 对象的 <span class="codeph">withCredentials</span> 属性需要设置为 <span class="codeph">true</span>。Chrome、Firefox、Internet Explorer（版本 10 及更高版本）、Opera 和 Safari 都支持此属性。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>性能改进</b> </p> </td> 
   <td colname="col2"> <p>CORS 可以帮助改进性能，因为： </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">浏览器可以管理资源请求。请求流程对 ID 服务来说是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">与异步 JSONP 请求不同，浏览器不会对 CORS 请求取消优先级和排队。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID 服务可自由响应。这意味着当 URL 作为 <span class="codeph">Origin</span> 传入时，ID 服务会向页面授予所需资源的访问权限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

