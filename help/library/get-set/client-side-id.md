---
description: 调用此访客ID服务函数，以确定访客ID服务是否生成了客户端ECID (MID)。 在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: 访客 ID 服务
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

调用此访客ID服务函数，以确定访客ID服务是否生成了客户端ECID (MID)。 在`VisitorAPI.js`版本1.7.0或更高版本中可用。

**语法**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

下表列出并描述了此函数返回的响应。

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 响应 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>访客ID服务无法或没有从CX Enterprise服务器收到MID。 它会在浏览器（客户端）本地创建 MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>访客ID服务从CX Enterprise服务器收到了MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>访客ID服务没有对CX Enterprise服务器进行调用。 </p> </td> 
  </tr> 
 </tbody> 
</table>

