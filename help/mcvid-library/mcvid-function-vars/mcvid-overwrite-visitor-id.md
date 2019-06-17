---
description: 当访客从一个域导航到另一个域时，此属性将覆盖其 Experience Cloud ID 和 Analytics ID。要覆盖 ID，您必须拥有域，并且已经在每个域上实施了 ID 服务。您无法通过此代码在没有控制权的域上改写 ID。
keywords: ID 服务
seo-description: 当访客从一个域导航到另一个域时，此属性将覆盖其 Experience Cloud ID 和 Analytics ID。要覆盖 ID，您必须拥有域，并且已经在每个域上实施了 ID 服务。您无法通过此代码在没有控制权的域上改写 ID。
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: e48127a-ac62-4ea0-9756-2a27 b20 ecbcf
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

当访客从一个域导航到另一个域时，此属性将覆盖其 Experience Cloud ID 和 Analytics ID。要覆盖 ID，您必须拥有域，并且已经在每个域上实施了 ID 服务。您无法通过此代码在没有控制权的域上改写 ID。

**语法：**`Visitor.overwriteCrossDomainMCIDAndAID: true|false` (默认为 `false`)

**代码示例**

您的 JavaScript 代码可能与以下示例类似。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**用例**

为跟踪网站访客，ID 服务会将 [!DNL Experience Cloud] ID（或 MID）写入浏览器 Cookie。下表列出并描述了一些常见用例，其中您可能需要覆盖由其他域中的 ID 服务设置的现有 MID。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>识别不同域登录页上的访客</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">每个域都拥有它自己的登录页面。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">访客已在之前的域 B 访问中设置了 Cookie（和 MID）。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">如果访客从域 A 来到域 B，您需要始终识别他们。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别登录和转化页面间的访客</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">域 A 是登录页面。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">域 B 是单独的转化、预订或其他工作流程结束页面。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">访客已在之前的域 B 访问中设置了 Cookie（和 MID），而且您知道这些是不太理想的客户端 MID，而不是服务器端 MID。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">如果访客从域 A 来到域 B，您需要始终识别他们。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别从移动应用程序到 Web 浏览器的访客</b> </p> </td> 
   <td colname="col2"> <p>这种用例稍有不同。它涉及识别从移动应用程序移动到您的网站的用户。在这种情况下，您的访客已通过移动应用程序在本地设置了一个 MID，并且他们在您的网站上的 Cookie 中设置了一个不同的 MID。您可以设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>，以使用移动应用程序设置的 MID 覆盖浏览器 Cookie 中设置的 MID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

