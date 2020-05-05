---
description: 这些配置允许在iFrame中实现的ID服务代码的不同实例和父页面上的不同实例相互通信。 它们旨在帮助解决以下两种特定用例的问题：您可能控制父页面／域，并且您在您控制的域的iFrame中加载了ID服务代码。 它们在VisitorAPI.js代码版本2.2或更高版本中可用。
keywords: ID Service
seo-description: 这些配置允许在iFrame中实现的ID服务代码的不同实例和父页面上的不同实例相互通信。 它们旨在帮助解决以下两种特定用例的问题：您可能控制父页面／域，并且您在您控制的域的iFrame中加载了ID服务代码。 它们在VisitorAPI.js代码版本2.2或更高版本中可用。
seo-title: whitelistParentDomain 和 whitelistIframeDomains
title: whitelistParentDomain 和 whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# whitelistParentDomain 和 whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

这些配置允许在iFrame中实现的ID服务代码的不同实例和父页面上的不同实例相互通信。 它们旨在帮助解决以下两种特定用例的问题：您可能控制父页面／域，并且您在您控制的域的iFrame中加载了ID服务代码。 它们在VisitorAPI.js代码版本2.2或更高版本中可用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local">语法</a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> 代码示例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 用例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 配置安全性 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> 支持的访客 API 方法 </a> </li> 
</ul>

## 语法{#section-f645198bbaba4fba8961acb6e88d1470}

使用此代码时，需要两个配置元素。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 配置语法 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Domain name of parent page </span>" </span> </p> </td> 
   <td colname="col2"> <p>接受作为字符串传入的单个域名。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame domain","iFrame domain","iFrame domain" </span>] </span> </p> </td> 
   <td colname="col2"> <p>接受作为数组传入的一个或多个 iFrame 域名。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 代码示例 {#section-09d0049fe88a473baa69d404c50bf8ae}

您配置的 [!UICONTROL ID 服务]代码可能与以下示例类似。

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## 用例 {#section-fc2eeb93546b406fae3b102dbcd11de7}

这些配置有助于解决当浏览器阻止第三方Cookie并且如果满足以下任一条件时设置ID服务Cookie和分配访客ID的问题：

* 您是否控制父页面／域。
* ID服务代码未安装在父页面上，但是在iFrame中实现。

>[!TIP]
>
>在iFrame中提供视频时，您可能还需要实施这些 [配置](https://docs.adobe.com/content/help/zh-Hans/media-analytics/using/media-overview.html)。 视频心跳需要ID服务ID(MID)才能正常工作。

**用例1: 浏览器阻止第三方Cookie,ID服务在iFrame和父页面上实现**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例元素 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>此用例包括以下条件： </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">公司A在其主页上实现ID服务。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">公司A在iFrame中对其主页实施ID服务。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">公司A拥有父页面和iFrame，并已在这两个位置实施ID服务。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">客户在浏览器中加载父页面，该浏览器会阻止第三方Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>结果</b> </p> </td> 
   <td colname="col2"> <p>根据这些条件，ID服务： </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">在父页面上正常工作。 它请求并设置AMCV cookie，并为站点访客分配唯一ID。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">在iFrame中不工作。 这是因为浏览器将iFrame视为第三方域并阻止ID服务设置AMCV cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案</b> </p> </td> 
   <td colname="col2"> <p>使用这些白名单配置，修改 iFrame 中的 ID 服务 <span class="codeph">Visitor.getInstance</span> 函数。在代码中指定父域和子域。 这些配置允许iFrame中的ID服务代码检查父页面上的ID服务代码以查找访客ID。 </p> <p>如果iFrame中的ID服务代码未收到响应父页面，则这些配置将生成本地访客ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**用例2: 从嵌入在父页面中的iFrame请求ID，您无法控制或者它不使用ID服务**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例元素 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>此用例包括以下条件： </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">公司A不使用ID服务。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">公司A在页面上加载iFrame。 此iFrame由公司B拥有，并加载到与公司A不同的域中。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">浏览器会阻止第三方cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>结果</b> </p> </td> 
   <td colname="col2"> <p>根据这些条件，ID服务： </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">在iFrame中不工作。 这是因为浏览器将iFrame视为第三方域并阻止ID服务设置AMCV cookie。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">无法从父页面获取访客ID，因为公司A不使用此服务。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案</b> </p> </td> 
   <td colname="col2"> <p>使用这些白名单配置，修改 iFrame 中的 ID 服务 <span class="codeph">Visitor.getInstance</span> 函数。在代码中指定父域和子域。 这些配置允许iFrame中的ID服务代码检查父页面上的ID服务代码以查找访客ID。 </p> <p>如果iFrame中的ID服务代码未收到响应父页面，则这些配置将生成本地访客ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 配置安全性 {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

您可以安全地实施这些配置，因为：

* 在父域和iFrame域上实现的ID服务必须使用相同的组织ID。 当父组织或iFrame中的组织ID不同时，这些白色列表配置将不起作用。
* 这些配置仅与代码中指定的域和iFrames通信。
* iFrame与父页面之间的通信遵循特定格式。 如果父页面上的ID服务未收到预期格式的请求，则此共享过程将失败。

## 支持的访客 API 方法 {#section-30c6a9f4dcdc4265a1149260b97cc057}

在您实施这些白色列表配置时，ID服务支持有限的公共API方法集。 支持的方法因上述用例情景而异。

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例 </th> 
   <th colname="col2" class="entry"> 支持的方法 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>用例 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>用例 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

