---
description: 借助此帮助程序方法，您可以将 Supplemental Data ID (SDID) 作为查询字符串参数附加到重定向 URL。 当使用 A4T 以及您需要在不同的页面间保留 SDID 并将这些不同的访问拼合在一起时，此方法很有用。 要使用此函数，您必须在源和目标域上使用相同的IMS组织ID实施了访客ID服务。
keywords: 访客 ID 服务
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 61%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

借助此帮助程序方法，您可以将 Supplemental Data ID (SDID) 作为查询字符串参数附加到重定向 URL。 当使用 A4T 以及您需要在不同的页面间保留 SDID 并将这些不同的访问拼合在一起时，此方法很有用。 要使用此函数，您必须在源和目标域上使用相同的IMS组织ID实施了访客ID服务。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 示例输出 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> 通过 sdidParamExpiry 更改 SDID 超时 </a> </li> 
</ul>

## 语法和代码示例 {#section-cbb0b2f73bcc418386796c24c01b2365}

**语法：**`appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**代码示例**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## 示例输出 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

如下所示，在对接收页面的调用中，URL重定向包含访客的SDID、您的IMS组织ID以及UNIX时间戳。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## 通过 sdidParamExpiry 更改 SDID 超时 {#section-99946715cefa4acc95200b093db5297e}

通过 [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 配置，您可以在使用 `appendSupplementalDataIDTo` 帮助程序函数将 SDID 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。 默认情况下，接收页面上的访客ID服务代码有30秒时间从引荐页面发送的URL获取SDID。 如果接收页面上的访客ID服务代码无法在30秒内检索SDID，它会请求新的SDID。 此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**`sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

在配置后，您的访客ID服务代码可能与以下示例类似。 此示例将 SDID 超时设为 15 秒。

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```

