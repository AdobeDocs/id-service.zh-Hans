---
description: 此帮助程序方法允许您将补充数据 ID (SDID) 作为查询字符串参数附加到重定向 URL。在使用 A4T，同时您需要将 SDID 从一个页面保留到另一个页面，并将那些单独的访问整合到一起时，此方法非常有用。要使用此函数，您必须已使用同一组织 ID 在源域和目标域中实施了 ID 服务。
keywords: ID 服务
seo-description: 此帮助程序方法允许您将补充数据 ID (SDID) 作为查询字符串参数附加到重定向 URL。在使用 A4T，同时您需要将 SDID 从一个页面保留到另一个页面，并将那些单独的访问整合到一起时，此方法非常有用。要使用此函数，您必须已使用同一组织 ID 在源域和目标域中实施了 ID 服务。
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

此帮助程序方法允许您将补充数据 ID (SDID) 作为查询字符串参数附加到重定向 URL。在使用 A4T，同时您需要将 SDID 从一个页面保留到另一个页面，并将那些单独的访问整合到一起时，此方法非常有用。要使用此函数，您必须已使用同一组织 ID 在源域和目标域中实施了 ID 服务。

目录：

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 示例输出 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> 通过 sdidParamExpiry 更改 SDID 超时 </a> </li> 
</ul>

## 语法和代码示例 {#section-cbb0b2f73bcc418386796c24c01b2365}

**语法：**` appendSupplementalDataIDTo( *`URLSID`*, *``*)`

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## 示例输出 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

如下所示，在对接收页面的调用中，URL 重定向包含访客的 SDID、您的组织 ID 以及 UNIX 时间戳。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## 通过 sdidParamExpiry 更改 SDID 超时 {#section-99946715cefa4acc95200b093db5297e}

[sdidParameterPresence](../../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 配置允许您使用 `appendSupplementalDataIDTo` 辅助功能，在将该ID从一个页面传递到另一个页面时更改默认SSID过期间隔。默认情况下，接收页面上的 ID 服务代码将有 30 秒的时间从反向链接页面发送的 URL 中获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒内检索 SDID，它会请求一个新的 SDID。此功能主要适用于需要在页面间传递 SDID 并希望控制此超时间隔的 A4T 客户。

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *`时间(以秒计)`*`

**代码示例**

配置完成后，您的 ID 服务代码可能与以下示例类似。此示例将 SDID 超时设置为 15 秒。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

