---
audience: end-user
user-guide-title: Adobe访客ID服务帮助
breadcrumb-title: 访客ID服务指南
user-guide-description: Adobe访客ID服务提供了一个通用的永久性ID，用于在CX Enterprise的所有解决方案中标识您的访客。 它有助于取代CX Enterprise解决方案和服务的旧版ID生成代码。
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 45%

---


# Adobe访客ID服务帮助 {#using}

+ [访客ID服务帮助](home.md)
+ 概述 {#intro}
   + [概述](introduction/overview.md)
   + [关于访客ID服务](introduction/about-id-service.md)
   + [Cookie和访客ID服务](introduction/cookies.md)
   + [访客ID服务如何请求和设置ID](introduction/id-request.md)
   + [了解同步和匹配率](introduction/match-rates.md)
+ 实施 {#implementation}
   + [实施方法](implementation-guides/implementation-methods.md)
   + [实施指南](implementation-guides/implementation-guides.md)
   + [使用标记实施](implementation-guides/ecid-implement-with-launch.md)
   + [适用于Analytics的实施](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/overview){target=_blank}
   + [为 Target 实施](implementation-guides/setup-target.md)
   + [为 Analytics 和 Audience Manager 实施](implementation-guides/setup-aam-analytics.md)
   + [为 Analytics、Audience Manager 和 Target 实施](implementation-guides/setup-aam-analytics-target.md)
   + [在Target的A4T和服务器端实施中使用访客ID服务](implementation-guides/ecid-a4t-target.md)
   + [与访客ID服务的直接集成](implementation-guides/direct-integration.md)
   + [直接集成用例](implementation-guides/direct-integration-examples.md)
   + [测试和验证访客ID服务](implementation-guides/test-verify.md)
   + 选择加入服务 {#opt-in-service}
      + [选择加入服务概述](implementation-guides/opt-in-service/optin-overview.md)
      + [设置选择加入服务](implementation-guides/opt-in-service/getting-started.md)
      + [验证选择加入服务](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用标记配置选择加入](implementation-guides/opt-in-service/launch.md)
      + [在用户同意的基础上控制CX企业活动](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [选择加入用例](implementation-guides/opt-in-service/use-cases.md)
      + [选择加入参考](implementation-guides/opt-in-service/api.md)
      + [在 IAB 框架中使用选择加入服务](implementation-guides/opt-in-service/iab.md)
+ 访客ID服务API {#id-service-api}
   + [访客ID服务API概述](library/library.md)
   + 配置 {#configurations}
      + [配置概述](library/function-vars/function-vars.md)
      + [audienceManagerServer 和 audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Secure 和 SameSite 配置](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain 和 whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + 方法 {#methods}
      + [方法](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo（跨域跟踪）](library/get-set/appendvisitorid.md)
      + [callTimeOut 方法](library/get-set/timeout-functions.md)
      + [通过 URL 或数据源进行 ID 同步](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ 参考 {#reference}
   + [参考概述](reference/reference.md)
   + [Google Chrome SameSite 标签更改](reference/chrome-samesite-labelling.md)
   + [内容安全策略和访客ID服务](reference/csp.md)
   + [访客ID服务中的COPPA支持](reference/coppa.md)
   + [访客ID服务中的CORS支持](reference/cors.md)
   + [客户 ID 和身份验证状态](reference/authenticated-state.md)
   + [Safari ITP 中的 ECID 库方法](reference/ecid-library-methods.md)
   + [识别独特访客](reference/unique-vis-method.md)
   + [从AMCV Cookie或访客ID服务获取区域ID和用户ID](reference/regions.md)
   + [访客ID服务的要求](reference/requirements.md)
   + [视频心率和访客ID服务](reference/heartbeat.md)
   + [支持用 SHA256 哈希处理 setCustomerIDs](reference/hashing-support.md)
+ 常见问题解答 {#faqs}
   + [常见问题解答概述](faq-intro/faq-intro.md)
   + [访客ID服务常见问题解答](faq-intro/faq.md)
   + [其他CX企业解决方案的常见问题解答](faq-intro/other-faq.md)
+ 访客ID服务的发行说明 {#release-notes}
   + [2022 版发行说明](release-notes/notes-2022.md)
   + [2021 版发行说明](release-notes/notes-2021.md)
   + [2020 版发行说明](release-notes/notes-2020.md)
   + [2019 版发行说明](release-notes/notes-2019.md)
   + [2018 版发行说明](release-notes/notes-2018.md)
   + [2017 版发行说明](release-notes/notes-2017.md)
   + [2016 版发行说明](release-notes/notes-2016.md)
   + [2015 版发行说明](release-notes/notes-2015.md)
