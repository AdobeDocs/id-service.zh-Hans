---
description: 调用这些ID服务函数以确定Experience Platform Identity Service、Analytics或Audience Manager ID请求的超时状态。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
seo-description: 调用这些ID服务函数以确定Experience Platform Identity Service、Analytics或Audience Manager ID请求的超时状态。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
seo-title: callTimeOut 方法
title: callTimeOut 方法
uuid: e5047498-11db-4945-b356-c92 b7 d447573
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# callTimeOut 方法{#calltimeout-methods}

调用这些ID服务函数以确定Experience Platform Identity Service、Analytics或Audience Manager ID请求的超时状态。在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

## 超时函数 {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 解决方案或服务 </th> 
   <th colname="col2" class="entry"> 函数语法 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Platform Identity Service </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = reciptor. mCIDCalltimeout()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = reciptor. analyticsCalltimeout()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = reciptor. aiascalltimeout()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 函数响应 {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 响应 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>ID 服务发送了一个请求，并且该请求已超时。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>ID 服务发送了一个请求，并从服务器接收到成功的响应。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>ID 服务没有发送请求。 </p> </td> 
  </tr> 
 </tbody> 
</table>
