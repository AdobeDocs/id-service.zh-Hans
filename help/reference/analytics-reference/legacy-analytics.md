---
description: 概述Experience Cloud ID Service如何与传统Analytics ID配合使用。
keywords: ID 服务
seo-description: 概述Experience Cloud ID Service如何与传统Analytics ID配合使用。
seo-title: Analytics 和 Experience Cloud ID 请求
title: Analytics 和 Experience Cloud ID 请求
uuid: 28bed16-7ef9-4824-8e82-853930756a82-853930756
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Analytics 和 Experience Cloud ID 请求{#analytics-and-experience-cloud-id-requests}

概述Experience Cloud ID Service如何与传统Analytics ID配合使用。

## 概要 {#section-64d8523ff7634cb987d0c6480f587dd3}

过去，Experience Cloud ID服务已紧密集成到Adobe Analytics中。它一直是 Analytics 的一个组成部分，但是如今，它在 [!DNL Experience Cloud] 的其他解决方案和功能中也发挥着举足轻重的作用。Because of this historical legacy, checking for or writing an Analytics ID works a little differently than with the generic process described in [How the Experience Cloud ID Service Requests and Sets IDs...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). For additional information on the order of operations for checking IDs, see [Setting Analytics and Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## 浏览器中未设置 AMCV Cookie {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

如果 [!DNL Experience Cloud] (AMCV) Cookie 不存在，则对 [!DNL Adobe] 的 ID 服务调用会生成一个响应，该响应将依据旧版 Analytics ID 的存在与否而有所变化。旧版 [!DNL Analytics] ID 存储在 [s_vi Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) 中。下表描述了如何根据 s_vi Cookie 的状态，将 ID 写入 AMCV Cookie。

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
   <td colname="col2"> <p>当具有s_ vi cookie的站点访客首次遇到Experience Cloud ID服务时，此服务： </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">将存储在 s_vi Cookie 中的 <span class="keyword">Analytics</span> ID 写入 AMCV Cookie。此 ID 将作为 <span class="keyword">Analytics</span> ID (AID) 写入。此操作<i>不会</i>影响您的访客计数。<span class="keyword">Analytics</span> 将继续使用其旧版 ID 来标识该用户。 </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">将 MID 写入 AMCV Cookie。MID 可在不同的解决方案中标识用户。 </li> 
    </ul> <p> <p>Note: With a <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> grace period</a>, the data center response always includes a legacy ID that is stored in the s_vi cookie. 在宽限期内，旧版 ID 将作为 AID 值写入 AMCV Cookie。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>由s_ fid cookie识别的用户不会将其原有的FID值迁移到AMCV cookie。这些使用 s_fid Cookie 的用户将作为不具备 s_vi Cookie 的用户（请参见上方描述的内容），按照网站新访客的身份出现。更多信息，请参阅 [Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html)。

## 浏览器中已设置 AMCV Cookie {#section-01c088fc565c4b24ba1722c7cc240310}

如果设置了 AMCV Cookie，但是此 Cookie 中没有旧版 [!DNL Analytics] ID 值，那么 将使用 MID 作为 [!DNL Analytics]Analytics 标识符。
