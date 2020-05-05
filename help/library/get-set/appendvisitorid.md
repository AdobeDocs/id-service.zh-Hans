---
description: 当浏览器阻止第三方Cookie时，此函数允许您跨域共享访客的Experience Cloud ID。 要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID Service
seo-description: 当浏览器阻止第三方Cookie时，此函数允许您跨域共享访客的Experience Cloud ID。 要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
seo-title: appendVisitorIDsTo（跨域跟踪）
title: appendVisitorIDsTo（跨域跟踪）
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# appendVisitorIDsTo（跨域跟踪）{#appendvisitoridsto-cross-domain-tracking}

当浏览器阻止第三方Cookie时，此函数允许您跨域共享访客的Experience Cloud ID。 要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在浏览器阻止第三方 Cookie 时跨域跟踪访客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加访客 ID 代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> 动态标签管理 (DTM) 和 SDK 支持 </a> </li> 
</ul>

## 在浏览器阻止第三方 Cookie 时跨域跟踪访客 {#section-7251d88befd440b4b79520e33c5aa44a}

当某人访问您的网站时，ID 服务会将第一方和第三方 Cookie 写入浏览器（请参阅 [Cookie 和 Experience Cloud Identity 服务](../../introduction/cookies.md)）。第一方Cookie包含MID，该MID是该访客的唯一ID。 第三方Cookie包含ID服务用于生成MID的另一个ID。 当浏览器阻止此第三方cookie时，ID服务无法：

* 当站点访客导航到其他域时，重新生成该站点的唯一ID。
* 跨组织拥有的不同域跟踪访客。

要帮助解决此问题，请实施 ` Visitor.appendVisitorIDsTo( *`url`*)`。通过此属性，ID服务可跨多个域跟踪站点访客，即使其浏览器阻止第三方Cookie时也是如此。 其工作方式如下：

* 当访客浏览您的其他域时，` Visitor.appendVisitorIDsTo( *`url`*)` 会将 MID 作为查询参数附加到从原始域到目标域的 URL 重定向中。
* 目标域上的ID服务代码从URL中提取MID，而不是向Adobe发送该访客的ID请求。 此请求包含第三方 Cookie ID，而该 ID 在这种情况下不可用。
* 目标页上的ID服务代码使用传入的MID跟踪访客。

有关详细信息，请参阅代码示例。

## 附加访客 ID 代码示例 {#section-62d55f7f986542b0b9238e483d50d7b0}

下面的示例可帮助您开始使用 ` Visitor.appendVisitorIDsTo( *`url`*)`。正确实施后，您的 JavaScript 代码可能与以下示例类似。

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## 动态标签管理 (DTM) 和 SDK 支持 {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 支持 </th> 
   <th colname="col2" class="entry"> 请参阅 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/cn/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> 在 DTM 中设置 appendVisitorIDTo 函数 </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/en/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID 服务方法 </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/en/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID 服务方法 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

