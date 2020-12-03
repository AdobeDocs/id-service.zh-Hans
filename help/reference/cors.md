---
description: 浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud Identity 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。
keywords: ID Service
seo-description: 浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud Identity 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。
seo-title: Experience Cloud Identity 服务中的 CORS 支持
title: Experience Cloud Identity 服务中的 CORS 支持
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 46%

---


# Experience Cloud Identity 服务中的 CORS 支持{#cors-support-in-the-experience-cloud-id-service}

浏览器使用跨域资源共享 (CORS) 从某个域而非当前域请求资源。Experience Cloud Identity 服务支持可启用这些客户端跨域资源请求的 CORS 标准。ID 服务会在旧版浏览器或不支持 CORS 的浏览器上还原为 JSONP 请求。

## 同域策略和 ID 服务请求的问题 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

相同来源策略是Web浏览器实施的安全控制或限制。 当在此级别上强制实施时，Web浏览器本身会确定是否允许或阻止对从一个页面到另一个页面进行的资源请求。 要确定请求是否为同一来源请求，浏览器会比较：

* 统一资源标识符(URI)
* 主机名(例如，http://www.my-webpage-example.com)
* 端口号（例如，端口80和440用于HTTP和HTTPS请求）

如果两个页面共享这些特性，则浏览器允许请求成功；如果两个页面不共享，则阻止资源请求。

## CORS解决了同来源策略的问题 {#section-76c87ec3295d447bab220c84f138c235}

CORS为跨不同域请求资源提供了一种安全、有效的方法。 CORS规范包括一组HTTP头，浏览器使用这些头发送、接收和评估资源请求。 评估资源请求称为 *`preflight check`*。 通过此检查，浏览器和服务器可确定允许或阻止哪些请求。 预检检查对请求资源的应用程序、API或脚本是透明的。 在资源请求流程中很重要的两个标题包括：

* `Origin`：识别请求源的请求标头。
* `Access-Control-Allow-Origin`：指示某个资源能否与请求者共享的响应标头。

下面我们看一看这些标头的工作方式。在此示例中，假设有一家金融服务公司在其网站 www.finance-website.com 上实施了 [!DNL Experience Cloud] ID 服务。下表定义了CORS请求和响应头检查对资源访问的方式。

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
   <td colname="col2"> <p>加载金融公司页面时，浏览器向 <span class="codeph">dpm.demdex.net</span> 提出请求。这是对ID服务使用的数据收集服务器(DCS)域的调用。 此跨域请求包含标题： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>响应</b> </p> </td> 
   <td colname="col2"> <p>来自DCS域的响应包括以下标头，这些标头使财务公司能够访问所需资源： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另请参阅 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用 CORS 的其他好处 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表说明了CORS为使用ID服务的客户提供的一些优势。

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
   <td colname="col2"> <p>CORS使 <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest" format="https" scope="external"> 用XMLHttpRequest</a> 来请求和传输数据。 此方法比JSONP请求更安全。 它确保无法执行任意JavaScript，该任意JavaScript可能包含在DCS的响应中。 CORS XMLHttpRequest响应负载由ID服务JavaScript解析，而不是简单地在回调函数中执行。 </p> <p> <p>注意：要接受 Cookie，<span class="codeph">XMLHttpRequest</span> 对象的 <span class="codeph">withCredentials</span> 属性需要设置为 <span class="codeph">true</span>。Chrome、Firefox、Internet Explorer(v10+)、Opera和Safari中支持此属性。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>性能改进</b> </p> </td> 
   <td colname="col2"> <p>CORS有助于提高性能，因为： </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">浏览器管理资源请求。 请求过程对ID服务是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">与异步JSONP请求不同，浏览器不会取消CORS请求的优先级并排队。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID服务可以允许地做出响应。 这意味着当 URL 作为 <span class="codeph">Origin</span> 传入时，ID 服务会向页面授予所需资源的访问权限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

