---
description: 通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 Experience Cloud ID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
title: appendVisitorIDsTo（跨域跟踪）
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: fc630f3a161b65edab1c34ec3b3f07938bf13aaf
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 88%

---

# appendVisitorIDsTo（跨域跟踪）{#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>如果ECID最初被拒绝（或以前被拒绝），则跨域跟踪将无法按预期工作。 它不会检查通过URL传递的或以前存在于Cookie中的现有ID，考虑这些ID是同意设置为“NO”时的ID

通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 Experience Cloud ID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在浏览器阻止第三方 Cookie 时跨域跟踪访客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加访客 ID 代码示例 </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

## 在浏览器阻止第三方 Cookie 时跨域跟踪访客 {#section-7251d88befd440b4b79520e33c5aa44a}

当某人访问您的网站时，ID 服务会将第一方和第三方 Cookie 写入浏览器（请参阅 [Cookie 和 Experience Cloud 身份服务](../../introduction/cookies.md)）。第一方 Cookie 包含 MID，它是该访客的唯一 ID。第三方 Cookie 包含 ID 服务用于生成 MID 的其他 ID。如果浏览器阻止此第三方 Cookie，则 ID 服务无法执行以下操作：

* 当网站访客导航到其他域时，重新生成该网站访客的唯一 ID。
* 跨组织拥有的不同域跟踪访客。

要帮助解决此问题，请实施 ` Visitor.appendVisitorIDsTo( *`url`*)`。通过此属性，即使网站访客的浏览器阻止第三方 Cookie，ID 服务也可跨多个域跟踪网站访客。其工作方式如下：

* 当访客浏览您的其他域时，` Visitor.appendVisitorIDsTo( *`url`*)` 会将 MID 作为查询参数附加到从原始域到目标域的 URL 重定向中。
* 目标域上的 ID 服务代码会从 URL 中提取 MID，而不是向 Adobe 发送请求以获取该访客的 ID。此请求包含第三方 Cookie ID，而该 ID 在这种情况下不可用。
* 目标页面上的 ID 服务代码使用传入的 MID 跟踪访客。

有关详细信息，请参阅代码示例。

## 附加访客 ID 代码示例 {#section-62d55f7f986542b0b9238e483d50d7b0}

下面的示例代码可帮助您开始使用 `appendVisitorIDsTo` 功能：

>[!TIP]
>
>可将此代码放入作为 Adobe Analytics 扩展一部分的自定义代码编辑器或放在 [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html) 的顶部。

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
