---
description: 当访客从一个域导航到另一个域时，此属性将覆盖其Experience Cloud和分析ID。 要覆盖ID，您必须拥有并已在每个域中实现了ID服务。 此代码不会覆盖您不控制的域上的ID。
keywords: ID Service
seo-description: 当访客从一个域导航到另一个域时，此属性将覆盖其Experience Cloud和分析ID。 要覆盖ID，您必须拥有并已在每个域中实现了ID服务。 此代码不会覆盖您不控制的域上的ID。
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 19%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

当访客从一个域导航到另一个域时，此属性将覆盖其Experience Cloud和分析ID。 要覆盖ID，您必须拥有并已在每个域中实现了ID服务。 此代码不会覆盖您不控制的域上的ID。

**语法：**`Visitor.overwriteCrossDomainMCIDAndAID: true|false`（默认值为 `false`。）

**代码示例**

您的JavaScript代码可能与以下示例类似。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**用例**

为跟踪网站访客，ID 服务会将 [!DNL Experience Cloud] ID（或 MID）写入浏览器 Cookie。下表列表并描述了您可能要覆盖由另一个域中的ID服务设置的现有MID的常见用例。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>识别不同域访客上的登陆页</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">每个域都有它自己的登陆页。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">访客在上次访问域B时已经设置了cookie（和MID）。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">如果访客从域A进入域B，您需要始终如一地识别该数据。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别登录和转化页面中的访客</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">域A是登陆页。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">域B是单独的转换、预订或其他工作流结束页面。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">访客在以前访问域B时已经设置了cookie（和MID），您知道这些是不太理想的客户端MID，而不是服务器端MID。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">如果访客从域A进入域B，您需要始终如一地识别该数据。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别从移动应用程序到Web浏览器的访客</b> </p> </td> 
   <td colname="col2"> <p>此用例略有不同。 它涉及在用户从移动应用程序移动到您的网站时识别用户。 在这种情况下，您的访客已经由移动应用程序在本地设置了MID，并且他们在您网站上的cookie中设置了不同的MID。 您可以设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>，以使用移动应用程序设置的 MID 覆盖浏览器 Cookie 中设置的 MID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

