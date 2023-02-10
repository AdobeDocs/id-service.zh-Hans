---
description: 借助此帮助程序方法，您可以将 Supplemental Data ID (SDID) 作为查询字符串参数附加到重定向 URL。当使用 A4T 以及您需要在不同的页面间保留 SDID 并将这些不同的访问拼合在一起时，此方法很有用。要使用此函数，您必须在源和目标域中使用同一组织 ID 实施了 ID 服务。
keywords: ID 服务
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
source-git-commit: 5710539b45a81394061cd4af2ef3edc27b49092e
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 100%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

借助此帮助程序方法，您可以将 Supplemental Data ID (SDID) 作为查询字符串参数附加到重定向 URL。当使用 A4T 以及您需要在不同的页面间保留 SDID 并将这些不同的访问拼合在一起时，此方法很有用。要使用此函数，您必须在源和目标域中使用同一组织 ID 实施了 ID 服务。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 示例输出 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> 通过 sdidParamExpiry 更改 SDID 超时 </a> </li> 
</ul>

## 语法和代码示例 {#section-cbb0b2f73bcc418386796c24c01b2365}

**语法：**` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**代码示例**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## 示例输出 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

如下所示，在对接收页面的调用中，URL 重定向包含访客的 SDID、您的组织 ID 以及 UNIX 时间戳。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## 通过 sdidParamExpiry 更改 SDID 超时 {#section-99946715cefa4acc95200b093db5297e}

通过 [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 配置，您可以在使用 `appendSupplementalDataIDTo` 帮助程序函数将 SDID 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码有 30 秒时间从引荐页面发送的 URL 获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒之内检索 SDID，它会请求新的 SDID。此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

若已配置，您的 ID 服务代码可能类似于此示例。此示例将 SDID 超时设为 15 秒。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
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
