---
description: 调用这些 ID 服务函数，可确定 Experience Cloud 身份标识服务、Analytics 或 Audience Manager ID 请求的超时状态。 在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。
keywords: ID 服务
title: callTimeOut 方法
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
TQID: https://experienceleague.adobe.com/DIis78iaPQ7qpawlKwWCwReXbh5Mt0K8J3w-5KYdhmg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 96%

---

# callTimeOut 方法{#calltimeout-methods}

调用这些 ID 服务函数，可确定 Experience Cloud 身份标识服务、Analytics 或 Audience Manager ID 请求的超时状态。 在 VisitorAPI.js 版本 1.7.0 或更高版本中可用。

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
   <td colname="col1"> <p>Experience Cloud 身份标识服务 </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
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

