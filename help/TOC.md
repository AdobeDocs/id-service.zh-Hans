---
cloud: platform-cloud
product: ID 服务
audience: 最终用户
user-guide-title: Experience Cloud ID服务帮助
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID Service Help {#using}

+ [ID服务帮助](home.md)
+ 概述 {#intro}
   + [概述](introduction/overview.md)
   + [关于ID服务](introduction/about-id-service.md)
   + [Cookie 和 ID 服务](introduction/cookies.md)
   + [ID服务请求和设置ID的方式](introduction/id-request.md)
   + [了解同步和匹配速率](introduction/match-rates.md)
+ Implementation guides {#implementation-guides}
   + [实施指南](implementation-guides/implementation-guides.md)
   + [实施方法](implementation-guides/implementation-methods.md)
   + [使用 Launch 实施](implementation-guides/ecid-implement-with-launch.md)
   + [使用 DTM 实施](implementation-guides/standard.md)
   + [实现Analytics](implementation-guides/setup-analytics.md)
   + [实现目标](implementation-guides/setup-target.md)
   + [为Analytics和Audience Manager实现](implementation-guides/setup-aam-analytics.md)
   + [针对Analytics、Audience Manager和Target实施](implementation-guides/setup-aam-analytics-target.md)
   + [在 Target 的 A4T 和服务器端实施中使用 ID 服务](implementation-guides/ecid-a4t-target.md)
   + [与ID服务直接集成](implementation-guides/direct-integration.md)
   + [直接集成用例](implementation-guides/direct-integration-examples.md)
   + [测试和验证ID服务](implementation-guides/test-verify.md)
   + Opt-in Documentation {#opt-in-service}
      + [选择服务概述](implementation-guides/opt-in-service/optin-overview.md)
      + [设置参与服务](implementation-guides/opt-in-service/getting-started.md)
      + [验证参与服务](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Launch 配置选择加入](implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 配置选择加入](implementation-guides/opt-in-service/optin-dtm.md)
      + [选择加入用例](implementation-guides/opt-in-service/use-cases.md)
      + [选择加入参考](implementation-guides/opt-in-service/api.md)
      + [(测试版)使用IAB Framework中的选择服务](implementation-guides/opt-in-service/iab.md)
+ ID 服务 API {#id-service-api}
   + [ID Service API概述](library/library.md)
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
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion ](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
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
   + Analytics 参考资料 {#analytics-reference}
      + [分析参考概述](reference/analytics-reference/analytics-reference.md)
      + [设置 Analytics 和 Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID 操作顺序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID服务迁移决策点](reference/analytics-reference/migration-decisions.md)
      + [ID服务迁移场景](reference/analytics-reference/migration-scenarios.md)
      + [分析和标识请求](reference/analytics-reference/legacy-analytics.md)
      + [数据收集 CNAME 和跨域跟踪](reference/analytics-reference/cname.md)
      + [结合了 JavaScript 技术的服务器端实施](reference/analytics-reference/server-side.md)
      + [ID 服务宽限期](reference/analytics-reference/grace-period.md)
   + [内容安全策略和ID服务](reference/csp.md)
   + [ID服务中的COPPA支持](reference/coppa.md)
   + [ID服务中的CORS支持](reference/cors.md)
   + [客户 ID 和身份验证状态](reference/authenticated-state.md)
   + [Safari ITP世界中的EID库方法](reference/ecid-library-methods.md)
   + [从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID](reference/regions.md)
   + [ID服务的要求](reference/requirements.md)
   + [Video Heartbat和ID服务](reference/heartbeat.md)
   + [Data Workbench和ID服务](reference/dwb.md)
+ 常见问题解答 {#faqs}
   + [常见问题解答概述](faq-intro/faq-intro.md)
   + [ID 服务常见问题解答](faq-intro/faq.md)
   + [Analytics 和 ID 服务常见问题解答](faq-intro/analytics-faq.md)
   + [其他 Experience Cloud 解决方案的常见问题解答](faq-intro/other-faq.md)
+ Release notes for ID Service {#release-notes}
   + [2019 版发行说明](release-notes/release-notes.md)
   + [2018 版发行说明](release-notes/notes-2018.md)
   + [2017 版发行说明](release-notes/notes-2017.md)
   + [2016 版发行说明](release-notes/notes-2016.md)
   + [2015 版发行说明](release-notes/notes-2015.md)
