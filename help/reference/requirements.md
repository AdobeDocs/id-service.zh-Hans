---
description: 查看此部分内容可确保您使用的是访客ID服务所需的正确解决方案、服务和代码版本。
keywords: 访客 ID 服务
title: Adobe访客ID服务的要求
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Adobe访客ID服务的要求 {#requirements-for-the-experience-cloud-id-service}

查看此部分内容可确保您使用的是访客ID服务所需的正确解决方案、服务和代码版本。

## 要求确保实施成功和支持 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功的、受支持的实施符合（或超出）代码要求，并遵循Adobe帮助中的说明。 不受支持的实施将产生意外结果，并妨碍客户关怀团队和我们的工程团队协助您排除或解决访客ID服务相关问题。

### 标准实施

请参阅Adobe Experience Platform数据收集中的[标记](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)以了解您的标准实施。

### 非标准实施

对于非标准实施或手动实施，您必须按照本指南中所述的步骤设置访客ID服务。 与上面的标准实施指南一样，如果代码放置和加载不当，则会创建不受支持的实施。

## CX企业要求：IMS组织ID {#section-a02f537129a64ffbb690d5738d360c26}

要使用访客ID服务，您的公司必须启用CX Enterprise并拥有IMS组织ID。 如果您不确定公司的CX企业版状态并需要查找您的IMS组织ID，请查看以下列表。

>[!IMPORTANT]
>
>IMS组织ID区分大小写，必须完全按照所提供的样式使用。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX企业版状态 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已启用</b> </p> </td> 
   <td colname="col2"> <p>如果贵公司已启用CX Enterprise，但您没有您的IMS组织ID，请参阅<a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=zh-Hans" format="https" scope="external">组织ID</a> （向下滚动到<i>查找您的组织ID</i>部分。） </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不确定</b> </p> </td> 
   <td colname="col2"> <p> 如果您不清楚公司的CX企业状态，请咨询您的Adobe帐户管理人员，确认公司成员是否可以使用Adobe ID登录<a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a>。 如果可以，则表示您已启用，并且管理员可以查看您的IMS组织ID。 要查找IMS组织ID，请参阅<a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=zh-Hans" format="https" scope="external"> CX Enterprise Administration</a>中的“管理页面”部分。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>未启用</b> </p> </td> 
   <td colname="col2"> <p> 如果贵公司未启用CX Enterprise，请参阅<a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=zh-Hans" format="https" scope="external">核心服务 — 启用您的解决方案</a>以开始使用。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics 要求：区域数据收集 (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

所有跟踪服务器都已转换为 RDC，因此无需更改 Analytics 跟踪服务器。 [更多信息...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=zh-Hans)

## 代码库和版本要求 {#section-ad7542a4317d430fa79fc6b095beb84d}

以下部分列出了使用访客ID服务所需的最低代码版本。

>[!TIP]
>
>我们建议您使用最新的代码版本，而不是使用要求的最低版本。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX企业解决方案 </th> 
   <th colname="col3" class="entry"> 代码库 </th> 
   <th colname="col4" class="entry"> 版本要求 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>访客ID服务</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 或更高版本 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>请参阅 <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=zh-Hans" format="https" scope="external">AppMeasurement for JavaScript</a>。 </p> </td> 
   <td colname="col4"> <p>1.6.4 或更高版本 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>注意： <span class="keyword"> Analytics</span> s_code版本H.27不再受访客ID服务版本1.6.0的支持。 将您的代码升级到最新版本的AppMeasurement。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>视频心率 </p> <p>请参阅<a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hans" format="https" scope="external">适用于 JavaScript 的视频心率 2.x</a>。 </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> 请参阅<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=zh-Hans" format="https" scope="external">数据集成库</a> (DIL)。 </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>请参阅 <a href="https://experienceleague.adobe.com/zh-hans/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">mbox 代码</a>。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>请参阅 <a href="https://experienceleague.adobe.com/zh-hans/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">at.js 实施</a>。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android 和 iOS 的 SDK 要求 {#section-73b2446fba8e463888642c7d7dfd94f1}

访客ID服务至少需要使用下面列出的SDK版本。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>我们建议您使用最新的代码版本，而不是使用要求的最低版本。

必须为访客ID服务启用您的SDK代码。 请通过您的 [Adobe Mobile Services](https://mobilemarketing.adobe.com/) 帐户为每个应用程序启用并下载最新的 SDK 代码。 另请参阅：

* [配置 SDK 访客 ID 服务选项](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=zh-Hans)
* [Android SDK 方法](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=zh-Hans)
* [iOS SDK方法](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=zh-Hans)

>[!MORELIKETHIS]
>
>* [代码库](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
