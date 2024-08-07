---
description: 浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud Identity 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。
keywords: ID 服务
title: Experience Cloud Identity 服务中的 CORS 支持
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 96%

---

# Experience Cloud Identity 服务中的 CORS 支持 {#cors-support-in-the-experience-cloud-id-service}

浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud Identity 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。

## 同域策略和ID服务请求的问题 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

同域策略是由 Web 浏览器强制实施的安全控制或限制。在此级别强制实施这些策略后，Web 浏览器本身会确定是允许还是阻止从一个页面向另一个页面发出的资源请求。为确定某个请求是否为同域请求，该浏览器会比较：

* 统一资源标识符 (URI)
* 主机名（例如 http://www.my-webpage-example.com）
* 端口号（例如 HTTP 和 HTTPS 请求对应的端口号分别为 80 和 440）

如果两个页面都具有这些特征，浏览器会允许请求成功；否则会阻止资源请求。

## CORS会根据同域策略解决问题 {#section-76c87ec3295d447bab220c84f138c235}

CORS 提供一种安全高效的方法来跨不同域请求资源。CORS 规范包含一组 HTTP 标头，供浏览器用于发送、接收和评估资源请求。评估资源请求称为 *`preflight check`*。此检查可让浏览器和服务器确定允许或阻止哪些请求。预检对请求资源的应用程序、API 或脚本是透明的。在资源请求流程中很重要的两个标头包括：

* `Origin`：识别请求源的请求标头。
* `Access-Control-Allow-Origin`：指示某个资源能否与请求者共享的响应标头。

下面我们看一看这些标头的工作方式。在此示例中，假设有一家金融服务公司在其网站 www.finance-website.com 上实施了 [!DNL Experience Cloud] ID 服务。下表定义了 CORS 请求和响应标头如何检查对资源的访问权限。

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
   <td colname="col2"> <p>加载金融公司页面时，浏览器向 <span class="codeph">dpm.demdex.net</span> 提出请求。这会调用 ID 服务使用的数据收集服务器 (DCS) 的域。此跨域请求包括以下标头： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>响应</b> </p> </td> 
   <td colname="col2"> <p>来自 DCS 域的响应包括这些为金融公司授予对所需资源访问权限的标头： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另请参阅 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用CORS的其他好处 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表介绍了 CORS 为使用 ID 服务的客户带来的一些优势。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 好处 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>增强的安全性</b> </p> </td> 
   <td colname="col2"> <p>CORS 使用 <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> 请求和传输数据。此方法比 JSONP 请求更安全。它可确保无法执行任意 JavaScript，后者可能包含在来自 DCS 的响应中。CORS XMLHttpRequest 响应载荷由 ID 服务 JavaScript 解析，而不只是在回调函数中执行。 </p> <p> <p>注意：要接受 Cookie，<span class="codeph">XMLHttpRequest</span> 对象的 <span class="codeph">withCredentials</span> 属性需要设置为 <span class="codeph">true</span>。此属性在 Chrome、Firefox、Internet Explorer (v10+)、Opera 和 Safari 中受支持。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>改进了性能</b> </p> </td> 
   <td colname="col2"> <p>CORS 有助于改进性能，这是因为： </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">浏览器会管理资源请求。请求过程对 ID 服务是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">与异步 JSONP 请求不同，浏览器不会降低 CORS 请求的优先级并将其加入队列。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID 服务会允诺做出响应。这意味着当 URL 作为 <span class="codeph">Origin</span> 传入时，ID 服务会向页面授予所需资源的访问权限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
