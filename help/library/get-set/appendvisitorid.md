---
description: 通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 Experience Cloud ID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
seo-description: 通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 Experience Cloud ID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
seo-title: appendVisitorIDsTo（跨域跟踪）
title: appendVisitorIDsTo（跨域跟踪）
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# appendVisitorIDsTo（跨域跟踪）{#appendvisitoridsto-cross-domain-tracking}

通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 Experience Cloud ID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在浏览器阻止第三方 Cookie 时跨域跟踪访客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加访客 ID 代码示例 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> 动态标签管理 (DTM) 和 SDK 支持 </a> </li> 
</ul>

## 在浏览器阻止第三方 Cookie 时跨域跟踪访客 {#section-7251d88befd440b4b79520e33c5aa44a}

ID service writes a first- and third-party cookie to the browser when a person visit your site (see [Cookies and the Experience Cloud Identity Service](../../introduction/cookies.md) ). 第一方 Cookie 包含 MID，即该访客的唯一 ID。第三方 Cookie 包含 ID 服务用来生成 MID 的其他 ID。如果浏览器阻止第三方 Cookie，ID 服务将无法执行以下操作：

* 在该网站访客导航到其他域时，重新为其生成唯一 ID。
* 在您的组织所拥有的不同域中跟踪访客。

要帮助解决此问题，请实施 ` Visitor.appendVisitorIDsTo( *`url`*)`。通过此属性，即使网站访客的浏览器阻止了第三方 Cookie，ID 服务仍可跨多个域跟踪网站访客。它的工作过程如下：

* 当访客浏览您的其他域时，` Visitor.appendVisitorIDsTo( *`url`*)` 会将 MID 作为查询参数附加到从原始域到目标域的 URL 重定向中。
* 目标域上的 ID 服务代码会从 URL 中提取 MID，而不是向 Adobe 发送请求以获取该访客的 ID。此请求包含第三方 Cookie ID，而该 ID 在这种情况下不可用。
* 目标页面上的 ID 服务代码使用传入的 MID 跟踪访客。

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
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> 在 DTM 中设置 appendVisitorIDTo 函数 </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> Android ID 服务方法 </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> iOS ID 服务方法 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

