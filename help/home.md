---
description: 'Experience Cloud Identity 服务提供了一个通用的永久性 ID，用于在 Experience Cloud 的所有解决方案中标识您的访客。 '
keywords: ID 服务
title: Experience Cloud Identity 服务
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: ht
source-wordcount: '262'
ht-degree: 100%

---

# Adobe Experience Cloud Identity 服务 {#experience-cloud-id-service}

Adobe Experience Cloud Identity 服务（ID 服务）提供了一个通用的永久性 ID，用于在 Experience Cloud 的所有解决方案中标识您的访客。它可以取代各种服务（如 Analytics、Audience Manager、Target）以及其他 Experience Cloud 解决方案或功能的 ID 生成代码。

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>入门指南</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 概述 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Experience Cloud Identity 服务的要求 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans" format="html" scope="external">用 Platform 标记进行标准实施</a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript 库</b> </p> <p>用于 Experience Cloud Identity 服务的 JavaScript 位于：<a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>新增项目或特色项目</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 选择加入服务</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> 常见问题解答 </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>发行说明</b> </p> <p><b>版本 4.4</b> 2019 年 7 月 17 日发行版包括对 <a href="reference/hashing-support.md" format="dita" scope="local">SHA-256 哈希算法</a>的支持，该算法允许您传入客户 ID 或电子邮件地址，并传出经过哈希处理的 ID。</p><p><b>版本 4.0</b> 2019 年 2 月 12 日发行版包括<a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">选择加入服务</a>，用于确定当用户访问网站时您是否可以在其设备或浏览器上放置 Cookie。 </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 有关新增功能和修复，请参阅最新的 <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hans" format="https" scope="external">Experience Cloud 发行说明</a>。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">有关早期版本的信息，请参阅<a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hans" format="html" scope="external">之前的发行说明</a>。 </li> 
     </ul> </p> <p> <b>Experience Cloud 资源</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/cn/privacy.html" format="http" scope="external"> Adobe 隐私权中心</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=zh-Hans" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/cn/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 培训和教程</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/cn/support/experience-cloud.html" scope="external" format="https"> 产品文档主页</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
