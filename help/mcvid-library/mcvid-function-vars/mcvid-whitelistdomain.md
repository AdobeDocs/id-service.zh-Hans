---
description: 通过这些配置，iFrame 中和父页面上实施的不同 ID 服务代码实例可彼此进行通信。这些配置旨在帮助解决以下 2 个特定用例中存在的问题：在您能够控制或无法控制父页面/域的情况下，将 ID 服务代码加载到您所控制的域的 iFrame 中。这些配置可在 VisitorAPI.js 代码版本 2.2 或更高版本中使用。
keywords: ID 服务
seo-description: 通过这些配置，iFrame 中和父页面上实施的不同 ID 服务代码实例可彼此进行通信。这些配置旨在帮助解决以下 2 个特定用例中存在的问题：在您能够控制或无法控制父页面/域的情况下，将 ID 服务代码加载到您所控制的域的 iFrame 中。这些配置可在 VisitorAPI.js 代码版本 2.2 或更高版本中使用。
seo-title: whitelistParentDomain 和 whitelistIframeDomains
title: whitelistParentDomain 和 whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-3c4 f4 ab1 efb6
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# whitelistParentDomain 和 whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

通过这些配置，iFrame 中和父页面上实施的不同 ID 服务代码实例可彼此进行通信。这些配置旨在帮助解决以下 2 个特定用例中存在的问题：在您能够控制或无法控制父页面/域的情况下，将 ID 服务代码加载到您所控制的域的 iFrame 中。这些配置可在 VisitorAPI.js 代码版本 2.2 或更高版本中使用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local">语法</a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> 代码示例 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 用例 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 配置安全性 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> 支持的访客 API 方法 </a> </li> 
</ul>

## 语法{#section-f645198bbaba4fba8961acb6e88d1470}

使用以下代码时，需要这两个配置元素。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 配置语法 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain：“ <span class="varname"> 父页面的域名 </span>” </span> </p> </td> 
   <td colname="col2"> <p>接受作为字符串传入的单个域名。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistiframeDomains：[ <span class="varname"> “iFrame domain”，“iFrame domain”，“iFrame domain” </span>] </span> </p> </td> 
   <td colname="col2"> <p>接受作为数组传入的一个或多个 iFrame 域名。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 代码示例 {#section-09d0049fe88a473baa69d404c50bf8ae}

您所配置 [!DNL ID service] 的代码可能类似于此示例。

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

当浏览器阻止第三方 Cookie，并且满足以下任一条件时，这些配置可帮助解决有关设置 ID 服务 Cookie 和分配访客 ID 的问题：

* 您拥有或没有父页面/域的控制权。
* ID 服务代码未在父页面上安装，但在 iFrame 中实施。

>[!TIP]
>
>当您使用 [Video心率在iFrame中投放视频时，您也可能希望实施这些配置](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/)。视频心率需要 ID 服务 ID (MID) 才能正常运行。

**用例 1：浏览器阻止第三方 Cookie，并且 ID 服务在 iFrame 和父页面中实施**

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
   <td colname="col2"> <p>此用例包含以下条件： </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">公司 A 在其主页上实施 ID 服务。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">公司 A 在其主页上的 iFrame 中实施 ID 服务。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">公司 A 拥有父页面和 iFrame，并且在这两个位置都实施了 ID 服务。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">客户在阻止第三方 Cookie 的浏览器中加载父页面。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>结果</b> </p> </td> 
   <td colname="col2"> <p>根据以上条件，ID 服务： </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">在父页面上正常运行。ID 服务会请求和设置 AMCV Cookie，并将唯一 ID 分配给网站访客。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">无法在 iFrame 中运行。这是因为浏览器将 iFrame 视为第三方域，因而会阻止 ID 服务设置 AMCV Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案</b> </p> </td> 
   <td colname="col2"> <p>使用这些白名单配置，修改 iFrame 中的 ID 服务 <span class="codeph">Visitor.getInstance</span> 函数。在代码中指定父域和子域。通过这些配置，iFrame 中的 ID 服务代码可在父页面上的 ID 服务代码中检查访客 ID。 </p> <p>如果 iFrame 中的 ID 服务代码没有收到父页面的响应，这些配置会生成一个本地访客 ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**用例 2：从您没有控制权或未使用 ID 服务的父页面中内嵌的 iFrame 请求 ID**

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
   <td colname="col2"> <p>此用例包含以下条件： </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">公司 A 未使用 ID 服务。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">公司 A 在页面上加载 iFrame。此 iFrame 归公司 B 所有，且在与公司 A 不同的域中加载。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">浏览器阻止第三方 Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>结果</b> </p> </td> 
   <td colname="col2"> <p>根据以上条件，ID 服务： </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">无法在 iFrame 中运行。这是因为浏览器将 iFrame 视为第三方域，因而会阻止 ID 服务设置 AMCV Cookie。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">无法从父页面获取访客 ID，因为公司 A 未使用此服务。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案</b> </p> </td> 
   <td colname="col2"> <p>使用这些白名单配置，修改 iFrame 中的 ID 服务 <span class="codeph">Visitor.getInstance</span> 函数。在代码中指定父域和子域。通过这些配置，iFrame 中的 ID 服务代码可在父页面上的 ID 服务代码中检查访客 ID。 </p> <p>如果 iFrame 中的 ID 服务代码没有收到父页面的响应，这些配置会生成一个本地访客 ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 配置安全性 {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

您可以安全地实施这些配置，因为：

* 在父域和 iFrame 域中实施的 ID 服务必须使用相同的组织 ID。如果父域或 iFrame 中的组织 ID 不同，这些白名单配置将无法正常工作。
* 这些配置仅与代码中指定的域和 iFrame 进行通信。
* iFrame 和父页面之间的通信遵循特定的格式。如果父页面上的 ID 服务未收到采用预期格式的请求，此共享过程将失败。

## 支持的访客 API 方法 {#section-30c6a9f4dcdc4265a1149260b97cc057}

在实施这些白名单配置时，ID 服务支持一组有限的公共 API 方法。支持的方法根据上面所述的用例情景而有所不同。

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

