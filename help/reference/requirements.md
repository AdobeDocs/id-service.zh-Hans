---
description: 查看此部分内容，确保使用 Experience Cloud Identity 服务所需的正确解决方案、服务和代码版本。
keywords: ID Service
seo-description: 查看此部分内容，确保使用 Experience Cloud Identity 服务所需的正确解决方案、服务和代码版本。
seo-title: Experience Cloud Identity 服务的要求
title: Experience Cloud Identity 服务的要求
uuid: 608b1082-6e9e-4101-b6cb-60027950109b
translation-type: ht
source-git-commit: 6e77622817d9881efd9039d9073ba4ae14e8e14e
workflow-type: ht
source-wordcount: '781'
ht-degree: 100%

---


# Experience Cloud Identity 服务的要求{#requirements-for-the-experience-cloud-id-service}

查看此部分内容，确保使用 Experience Cloud Identity 服务所需的正确解决方案、服务和代码版本。

## 要求确保实施成功和支持 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功的、受支持的实施符合（或超出）代码要求，并遵循 [!DNL Adobe] 帮助中显示的说明。不受支持的实施将产生意外结果，并妨碍客户关怀团队和我们的工程团队协助您排查或解决您遇到的 ID 服务问题。

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 实施类型 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> 标准实施</a> </p> </td> 
   <td colname="col2"> <p>对于通过动态标签管理 (DTM) 进行的标准实施，您必须： </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> 将嵌入页眉代码放入页面的 <span class="codeph">&lt;head&gt;</span> 部分中。 </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">将嵌入页脚代码放在结束 <span class="codeph">&lt;/body&gt;</span> 标记之前。 </li> 
    </ul> <p>在以下情况下，不支持标准实施： </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> 将这些 DTM 嵌入代码中的任意代码放置在标记和/或页面代码的其他位置。 </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> 使用异步方法、调用/回调方法或包装器附加、添加或加载 DTM 代码。 </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">在同一页面上包含嵌入代码的多个实例。 </li> 
    </ul> <p>另请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/dtm/using/client-side/deployment.html" format="https" scope="external">嵌入代码和托管选项</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> 非标准实施 </a> </p> </td> 
   <td colname="col2"> <p>对于非标准实施或手动实施，您必须按照本指南中所述的步骤设置 ID 服务。与上述 DTM 实施准则一样，若代码放置和加载不当，则将生成不受支持的实施。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Experience Cloud 要求：组织 ID {#section-a02f537129a64ffbb690d5738d360c26}

要使用 ID 服务，您的公司必须启用 [!DNL Experience Cloud] 并且拥有组织 ID。如果您不确定公司的 [!DNL Experience Cloud] 状态，并且需要查找您的组织 ID，请查看下面的列表。

>[!IMPORTANT]
>
>组织 ID 区分大小写，您必须完全按照所提供的样式使用。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 状态 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已启用</b> </p> </td> 
   <td colname="col2"> <p>如果贵公司已启用 <span class="keyword">Experience Cloud</span>，但您没有组织 ID，请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/core-services/interface/manage-users-and-products/organizations.html" format="https" scope="external">组织 ID</a>（向下滚动到“查找您的组织 ID”<i></i>部分。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不确定</b> </p> </td> 
   <td colname="col2"> <p> 如果您不清楚公司的 <span class="keyword">Experience Cloud</span> 状态，请咨询您的 Adobe 帐户管理人员，确认公司成员是否可以使用 Adobe ID 登录 <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a>。如果可以，则表明您已启用 Experience Cloud，并且管理员能够查看您的组织 ID。要找到组织 ID，请参阅 <a href="https://docs.adobe.com/help/zh-Hans/core-services/interface/experience-cloud.html" format="https" scope="external">Experience Cloud 管理</a>中的“管理页面”部分。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>未启用</b> </p> </td> 
   <td colname="col2"> <p> 如果您的公司未启用 Experience Cloud，请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/core-services/interface/about-core-services/core-services.html" format="https" scope="external">核心服务 - 启用您的解决方案</a>以开始启用。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics 要求：区域数据收集 (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

所有跟踪服务器都已转换为 RDC，因此无需更改 Analytics 跟踪服务器。[更多信息...](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## 代码库和版本要求 {#section-ad7542a4317d430fa79fc6b095beb84d}

以下部分列出了使用 [!DNL Experience Cloud] ID 服务所需的最低代码版本。

>[!TIP]
>
>我们建议您使用最新的代码版本，而不是使用要求的最低版本。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 解决方案 </th> 
   <th colname="col3" class="entry"> 代码库 </th> 
   <th colname="col4" class="entry"> 版本要求 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"></span>  Experience Cloud ID 服务</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 或更高版本 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>请参阅 <a href="https://docs.adobe.com/content/help/zh-Hans/analytics/implementation/js/overview.html" format="https" scope="external">AppMeasurement for JavaScript</a>。 </p> </td> 
   <td colname="col4"> <p>1.6.4 或更高版本 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>注意：<span class="keyword">随着 ID 服务版本 1.6.0 的发布，Analytics</span> s_code 版本 H.27 不再受到支持。请将您的代码升级到最新版本的 AppMeasurement。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>视频心率 </p> <p>请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/media-analytics/using/media-overview.html" format="https" scope="external">适用于 JavaScript 的视频心率 2.x</a>。 </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> 请参阅<a href="https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/dil-api/dil-overview.html" format="https" scope="external">数据集成库</a> (DIL)。 </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>请参阅 <a href="https://docs.adobe.com/content/help/zh-Hans/target/using/implement-target/client-side/mbox-implement/mbox-technical.html" format="https" scope="external">mbox 代码</a>。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>请参阅 <a href="https://docs.adobe.com/content/help/zh-Hans/target/using/implement-target/client-side/at-js/how-atjs-works.html" format="https" scope="external">at.js 实施</a>。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android 和 iOS 的 SDK 要求 {#section-73b2446fba8e463888642c7d7dfd94f1}

ID 服务至少需要使用下列 SDK 版本。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>我们建议您使用最新的代码版本，而不是使用要求的最低版本。

必须为 ID 服务启用您的 SDK 代码。请通过您的 [Adobe Mobile Services](https://mobilemarketing.adobe.com/) 帐户为每个应用程序启用并下载最新的 SDK 代码。另请参阅：

* [配置 SDK 访客 ID 服务选项](https://docs.adobe.com/content/help/zh-Hans/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html)
* [Android SDK 方法](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/experience-cloud-android/c-marketing-cloud.html)
* [iOS SDK 方法](https://docs.adobe.com/content/help/zh-Hans/mobile-services/ios/exp-cloud-ios/marketing-cloud.html)

>[!MORELIKETHIS]
>
>* [代码库](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

