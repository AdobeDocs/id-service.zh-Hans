---
description: 调用此 ID 服务函数以确定此 ID 服务是否生成了客户端 Experience Cloud 访客 ID (MID)。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

调用此 ID 服务函数以确定此 ID 服务是否生成了客户端 Experience Cloud 访客 ID (MID)。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

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
   <td colname="col2"> <p>ID 服务无法或没有从 <span class="keyword">Experience Cloud</span> 服务器收到 MID。它会在浏览器（客户端）本地创建 MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>ID 服务从 <span class="keyword">Experience Cloud</span> 服务器收到了 MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>ID 服务没有对 <span class="keyword">Experience Cloud</span> 服务器进行调用。 </p> </td> 
  </tr> 
 </tbody> 
</table>
