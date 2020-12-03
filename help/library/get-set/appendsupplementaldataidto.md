---
description: 此帮助程序方法允许您将补充数据ID(SDID)作为查询字符串参数附加到重定向URL。 当使用A4T时，此功能很有用，您需要将SDID从一个页面保留到另一个页面，并将这些单独的访问拼合在一起。 要使用此函数，您必须在源域和目标域上使用相同的组织ID实现ID服务。
keywords: ID Service
seo-description: 此帮助程序方法允许您将补充数据ID(SDID)作为查询字符串参数附加到重定向URL。 当使用A4T时，此功能很有用，您需要将SDID从一个页面保留到另一个页面，并将这些单独的访问拼合在一起。 要使用此函数，您必须在源域和目标域上使用相同的组织ID实现ID服务。
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 28%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

此帮助程序方法允许您将补充数据ID(SDID)作为查询字符串参数附加到重定向URL。 当使用A4T时，此功能很有用，您需要将SDID从一个页面保留到另一个页面，并将这些单独的访问拼合在一起。 要使用此函数，您必须在源域和目标域上使用相同的组织ID实现ID服务。

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

通过 [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 配置，您可以在使用 `appendSupplementalDataIDTo` 帮助程序函数将 SDID 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的ID服务代码有30秒钟从引用页面发送的URL获取SDID。 如果接收页上的ID服务代码在30秒内无法检索SDID，则它会请求新的SDID。 此功能主要针对需要将SDID从一个页面传递到另一个页面并希望控制此超时时间间隔的A4T客户。

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

配置后，您的ID服务代码可能与此示例类似。 此示例将SDID超时设置为15秒。

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

