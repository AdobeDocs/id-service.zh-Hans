---
description: 当访客从一个域转到另一个域时，此属性会覆盖该访客的 Experience Cloud 和 Analytics ID。要覆盖 ID，您必须拥有 ID 服务并在每个域上实施了该服务。此代码不允许您在您无法控制的域上覆盖 ID。
keywords: ID 服务
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '397'
ht-degree: 100%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

当访客从一个域转到另一个域时，此属性会覆盖该访客的 Experience Cloud 和 Analytics ID。要覆盖 ID，您必须拥有 ID 服务并在每个域上实施了该服务。此代码不允许您在您无法控制的域上覆盖 ID。

**语法：**`Visitor.overwriteCrossDomainMCIDAndAID: true|false`（默认值为 `false`。）

**代码示例**

您的 JavaScript 代码可能类似于以下示例。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**用例**

为跟踪网站访客，ID 服务会将 [!DNL Experience Cloud] ID（或 MID）写入浏览器 Cookie。下表列出并描述了您可能需要在另一个域中覆盖由 ID 服务设置的现有 MID 的常见用例。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>识别不同域登陆页面上的访客</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">每个域都有各自的登陆页面。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">某位访客已经在上次访问域 B 时设置了 Cookie（和 MID）。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">您希望以一致方式识别从域 A 前往域 B 的访客。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别登陆页面和转化页面上的访客</b> </p> </td> 
   <td colname="col2"> <p>比如说您自己的域 A 和 B。在这种情况下，您可以在以下条件下设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">域 A 是一个登陆页面。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">域 B 是一个单独的转化、预订或其他工作流程结束页面。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">某位访客已经在上次访问域 B 时设置了 Cookie（和 MID），并且您知道这是不太理想的客户端 MID（而非服务器端 MID）。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">您希望以一致方式识别从域 A 前往域 B 的访客。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>识别从移动应用程序转到 Web 浏览器的访客</b> </p> </td> 
   <td colname="col2"> <p>此用例略有不同。它涉及识别从移动应用程序切换到您网站的用户。在这种情况下，您的访客已经在移动应用程序本地设置了一个 MID，并在您网站上的 Cookie 中设置了一个不同的 MID。您可以设置 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>，以使用移动应用程序设置的 MID 覆盖浏览器 Cookie 中设置的 MID。 </p> </td> 
  </tr> 
 </tbody> 
</table>
