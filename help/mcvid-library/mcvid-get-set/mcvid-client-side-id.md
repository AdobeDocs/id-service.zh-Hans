---
description: 调用此 ID 服务函数可确定 ID 服务是否生成了客户端 Experience Cloud 访客 ID (MID)。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
seo-description: 调用此 ID 服务函数可确定 ID 服务是否生成了客户端 Experience Cloud 访客 ID (MID)。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2 ea-30d680 e61 e10
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

调用此 ID 服务函数可确定 ID 服务是否生成了客户端 Experience Cloud 访客 ID (MID)。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

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

