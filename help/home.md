---
description: 'Experience Platform Identity Service提供一个通用的永久ID，可在Experience Cloud中的所有解决方案中识别访客。 '
keywords: ID 服务
seo-description: Adobe Experience Platform Identity Service提供一个通用的永久ID，可在Experience Cloud中的所有解决方案中识别访客。它可以取代各种服务（如 Analytics、Audience Manager、Target）以及其他 Experience Cloud 解决方案或功能的 ID 生成代码。
seo-title: Experience Platform Identity Service
title: Experience Platform Identity Service
uuid: b68194b-e549-4f6 f-bfaf-7744926aaac
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Experience Platform Identity Service {#experience-cloud-id-service}

Experience Platform Identity Service(ID服务)提供一个通用的永久ID，可在Experience Cloud中的所有解决方案中识别访客。它可以取代各种服务（如 Analytics、Audience Manager、Target）以及其他 Experience Cloud 解决方案或功能的 ID 生成代码。

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>入门指南</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 概述 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Experience Platform Identity Service的要求 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> 使用 DTM 实现标准实施 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript 库</b> </p> <p>Experience Platform Identity Service JavaScript位于： <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>新增项目或特色项目</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 选择服务</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> 常见问题解答 </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>公告：</b> </p> 
     <p> <p>重要：Internet Explorer6、和的ID服务支持已弃用，将在将来的版本中停止。 </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>发行说明</b> </p> <p><b>2019</b> 年月12日版本版本包含 <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 用于识别您是否可以在访问站点时将Cookie放置到用户设备或浏览器上的选择加入服务</a> 。 </p> <p>2018 年 1 月 18 日版本包含 3.0.0 JavaScript 更新以及 API 方法更新。请参阅<a href="library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> DisableIDSyncs</a> 和 <a href="library/function-vars/disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> searchthirdPartyCookie</a>。 </p> 
    <draft-comment> 
     <p>2017年10月版不包括ID服务的任何代码更改或更新。ID服务代码在v2.5处保持不变。 </p> 
    </draft-comment> 
    <draft-comment> 
     <p> 2017年月版本将ID服务代码增加到v2.5。 </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 有关新增功能和修复，请参阅最新的 <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Experience Cloud 发行说明</a>。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">有关早期版本的信息，请参阅<a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">之前的发行说明</a>。 </li> 
     </ul> </p> <p> <b>Experience Cloud 资源</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe 隐私权中心</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 培训和教程</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> 产品文档主页</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

