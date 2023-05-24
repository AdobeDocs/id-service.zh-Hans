---
description: 概述 Experience Cloud Identity 服务如何处理旧版 Analytics ID。
keywords: ID 服务
title: Analytics 和 Experience Cloud ID 请求
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 100%

---

# Analytics 和 Experience Cloud ID 请求{#analytics-and-experience-cloud-id-requests}

概述 Experience Cloud Identity 服务如何处理旧版 Analytics ID。

## 概要 {#section-64d8523ff7634cb987d0c6480f587dd3}

从历史上看，Experience Cloud Identity 服务已经紧密地集成在 Adobe Analytics 中。它一直是 Analytics 的一个组成部分，但是如今，它在 [!DNL Experience Cloud] 的其他解决方案和功能中也发挥着举足轻重的作用。由于这个历史遗留原因，检查或编写 Analytics ID 的方式与 [Experience Cloud Identity 服务如何请求和设置 ID...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) 中描述的通用流程略有不同。有关检查 ID 操作顺序的其他信息，请参阅[设置 Analytics 和 Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)。

## 浏览器中未设置 AMCV Cookie {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

如果 [!DNL Experience Cloud] (AMCV) Cookie 不存在，则对 [!DNL Adobe] 的 ID 服务调用会生成一个响应，该响应将依据旧版 Analytics ID 的存在与否而有所变化。旧版 [!DNL Analytics] ID 存储在 [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hans) 中。下表描述了如何根据 s_vi Cookie 的状态，将 ID 写入 AMCV Cookie。

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi Cookie 状态 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>未设置 s_vi Cookie</b> </p> </td> 
   <td colname="col2"> <p>ID 服务可为访客分配一个 <span class="keyword">Experience Cloud</span> ID (MID)。MID 可在 <span class="keyword">Analytics</span> 和其他 <span class="keyword">Experience Cloud</span> 解决方案中标识访客。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>已设置 s_vi Cookie</b> </p> </td> 
   <td colname="col2"> <p>当设置了 s_vi Cookie 的网站访客首次体验 Experience Cloud Identity 服务时，该服务将执行以下操作： </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">将存储在 s_vi Cookie 中的 <span class="keyword">Analytics</span> ID 写入 AMCV Cookie。此 ID 将作为 <span class="keyword">Analytics</span> ID (AID) 写入。此操作<i>不会</i>影响您的访客计数。<span class="keyword">Analytics</span> 将继续使用其旧版 ID 来标识该用户。 </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">将 MID 写入 AMCV Cookie。MID 可在不同解决方案中标识用户。 </li> 
    </ul> <p> <p>注意：通过<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">宽限期</a>，数据中心响应将始终包括旧版 ID，并将其存储在 s_vi Cookie 中。在宽限期内，旧版 ID 将作为 AID 值写入 AMCV Cookie。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>对于通过 s_fid Cookie 标识的用户而言，其旧版 FID 值将不会被迁移至 AMCV Cookie 中。这些使用 s_fid Cookie 的用户将像不具备 s_vi Cookie 一样进行迁移（请参阅上文），并将以网站新访客的身份出现。有关更多信息，请参阅 [Analytics Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hans)。

## 浏览器中已设置 AMCV Cookie {#section-01c088fc565c4b24ba1722c7cc240310}

如果设置了 AMCV Cookie，但是此 Cookie 中没有旧版 [!DNL Analytics] ID 值，那么 [!DNL Analytics] 将使用 MID 作为 Analytics 标识符。
