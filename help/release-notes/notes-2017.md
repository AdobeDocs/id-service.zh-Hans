---
description: 关于 2017 版 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID 服务
seo-description: 关于 2017 版 Experience Cloud Identity 服务的功能发布、更新或更改。
seo-title: 2017 版发行说明
title: 2017 版发行说明
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '762'
ht-degree: 100%

---

# 2017 版发行说明 {#release-notes}

关于 2017 版 Experience Cloud Identity 服务的功能发布、更新或更改。

[Experience Cloud 发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html)中也记录了这些更改。

>[!NOTE]
>
>2017 年 3 月、4 月、5 月和 10 月未发布面向客户的发行说明或代码更改。在这些月份中，ID 服务代码未进行更改，版本仍为 2.1。

## 版本 2.5 {#section-27b441509124493f80984ed09bd9e88b}

2017 年 9 月

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>这是一个异步 API，在默认情况下可返回 Analytics 和 ID 服务中的标识符、选择禁用数据收集的用户标识符、以及地理位置和元数据“blob”内容中的标识符。此外，您还可以通过可选的 <span class="codeph">visitor.FIELDS</span> 枚举来控制要返回哪些 ID。请参阅 <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local">getVisitorValues</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**错误修复和其他更改**

* 修复了一个与 Chrome 相关的错误，在该浏览器中单击“返回”按钮时，该错误会导致 ID 服务出错。
* 现在，当事件调用响应中的区域 ID 发生更改时，ID 服务会重新触发 ID 同步。
* 新增了[内容安全策略和 Experience Cloud Identity 服务](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)文档，该文档说明了如何将 ID 服务使用的 Adobe 域调用添加到白名单中。

## 版本 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

2017 年 8 月

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>这是一个可选的布尔型配置，用于确定 ID 服务是否会将数据发送到 Adobe Experience Cloud 设备协作。请参阅 <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**修订的文档**

更新并修改了[常见问题解答](/help/faq-intro/faq-intro.md)，以包含针对不同 [!DNL Experience Cloud] 解决方案的单独常见问题解答。

## 版本 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

2017 年 7 月

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>添加到 <span class="codeph">Visitor.getInstance</span> 函数后，此配置允许您在将补充数据 ID (SDID) 从一个页面传递到另一个页面时，覆盖该 ID 的默认过期时间间隔。您可以将 <span class="codeph">sdidParamExpiry</span> 用于 <span class="codeph">appendSupplimentalDataTo</span> 帮助程序函数。请参阅 <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。请参阅 <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**错误修复和其他更改**

* 修复了 VisitorAPI.js v2.2 中 ID 服务和 Target 无法在 Internet Explorer 中一起使用的错误。
* 修改了代码，以帮助改进 ID 服务向 Destination Publishing iFrame 发送数据的方式。这有助于降低 CPU 使用量。

## 版本 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

发行日期：2017 年 6 月

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain 和 whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>通过这些配置，在 iFrame 中和父页面上实施的 ID 服务代码的不同实例可以相互通信。它们旨在帮助解决以下两种特定用例中出现的问题：您可能会（也可能不会）控制父页面/域，以及您在自己控制的域的 iFrame 中加载 ID 服务代码。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 5 月份的文档更新 {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主题 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> 常见问题解答 </a> </p> </td> 
   <td colname="col2"> <p>更新了 <span class="keyword">Analytics</span> 部分中有关如何查找跟踪服务器信息的内容。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 4 月份的文档更新 {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主题 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer 和 audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>添加了 <span class="keyword">Audience Manager</span> 文档的链接，该文档介绍了对 <span class="codeph">demdex.net</span> 域的调用。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> 了解 ID 同步和匹配率 </a> </p> </td> 
   <td colname="col2"> <p>修订了 <span class="keyword">Media Optimizer</span> 部分，以介绍对 <span class="codeph">cm.eversttech.net</span> 的调用。这是由 ID 服务执行的与 <span class="keyword">Media Optimizer</span> 之间的自动 ID 同步。此功能于 2017 年 1 月发布。请参阅下面的<a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">版本 2.0</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

发行日期：2017 年 2 月

**功能**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID 服务 API 属性，<span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>此属性可设置由 <span class="keyword">Audience Manager</span> 用来进行 ID 同步的容器 ID。请参阅 <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external">idSyncContainerID</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID 服务 API 方法，<span class="codeph">appendSupplementalDataIDTo( <span class="varname"> URL </span>, <span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>此公共方法可将<span class="wintitle">补充数据 ID</span> (SDID) 作为查询字符串参数附加到重定向 URL。请参阅 <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local">appendSupplementalDataIDTo</a>。(MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**修复**

修复了导致以下问题的错误：ID 服务进行冗余服务器调用以获取 ID，而不使用存储在 AMCV Cookie 中的 ID。(MCID-296)

**新文档**

[将 DNS 预获取用于不同的 Experience Cloud 解决方案和服务](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/more-resources/dns-prefetch.html)

## 版本 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

2017 年 1 月

>[!IMPORTANT]
>
>默认情况下，ID 服务代码 v2.0 将与 Adobe Media Optimizer 自动同步 ID。这表示您将在页面中看到对 `cm.eversttech.net`（由 [!DNL Adobe] 控制的旧版 [!DNL Media Optimizer] 域）的调用。另请参阅[了解 ID 同步和匹配率](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)。

**修复和改进功能**

* 修复了导致 AppMeasurement 无法对 Analytics 发起跟踪调用的错误。（MCID-254、MCID-256、MCID-286）
* 修复了一个在以下情况中 ID 服务无法立即失败的错误：访客启用了广告拦截器，并且将其配置为排除 demdex.net 域。这种错误非常少见，因为大多数广告拦截工具并不拦截 demdex.net 域。(MCID-233)
* 修复了由 ID 服务代码和客户网站上的自定义脚本之间的交互而导致的错误。此问题导致 Internet Explorer 9 无法加载网页。(MCID-206)

## 早期年份 {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

ID 服务的早期发行说明。
