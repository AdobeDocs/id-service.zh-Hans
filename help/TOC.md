---
cloud: experience-cloud
product: ID 服务
audience: 最终用户
user-guide-title: ID服务帮助
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: c8020fc1cc5acd5fccb1e8a2e2787d95aa1294ab

---


# ID服务帮助 {#using}

+ [Experience Cloud ID 服务](mcvid-home.md)
+ 概述 {#mcvid-introduction}
   + [概述](mcvid-introduction/mcvid-overview.md)
   + [关于ID服务](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookie 和 Experience Cloud ID 服务](mcvid-introduction/mcvid-cookies.md)
   + [Experience Cloud ID服务请求的请求和设置ID](mcvid-introduction/mcvid-id-request.md)
   + [了解ID同步和匹配率](mcvid-introduction/mcvid-match-rates.md)
+ 实施指南 {#implementation-guides}
   + [实施指南](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [实施方法](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [使用 Launch 实施](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [使用动态标签管理实现](mcvid-implementation-guides/mcvid-standard.md)
   + [实施适用于 Analytics 的 Experience Cloud ID 服务](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [实施适用于 Target 的 Experience Cloud ID 服务](mcvid-implementation-guides/mcvid-setup-target.md)
   + [实施适用于 Analytics 和 Audience Manager 的 Experience Cloud ID 服务](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [实施适用于 Analytics、Audience Manager 和 Target 的 Experience Cloud ID 服务](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [在 Target 的 A4T 和服务器端实施中使用 Experience Cloud ID 服务](mcvid-implementation-guides/ecid-a4t-target.md)
   + [与 Experience Cloud ID 服务的直接集成](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [直接集成用例](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [测试和验证Experience Cloud ID服务](mcvid-implementation-guides/mcvid-test-verify.md)
   + 选择加入文档 {#opt-in-service}
      + [选择服务概述](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [设置参与服务](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [验证参与服务](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Launch 配置选择加入](mcvid-implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 配置选择加入](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [选择加入用例](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [选择加入参考](mcvid-implementation-guides/opt-in-service/api.md)
      + [(测试版)使用IAB Framework中的选择服务](mcvid-implementation-guides/opt-in-service/iab.md)
+ ID 服务 API {#id-service-api}
   + 配置 {#configurations}
      + [配置概述](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer 和 audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion ](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain 和 whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + 方法 {#methods}
      + [方法](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo（跨域跟踪）](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [callTimeOut 方法](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [通过 URL 或数据源进行 ID 同步](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ 参考 {#reference}
   + Analytics 参考资料 {#analytics-reference}
      + [分析参考概述](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [设置 Analytics 和 Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Analytics ID 操作顺序](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Experience Cloud ID 服务迁移决策点](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Experience Cloud ID 服务迁移方案](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Analytics 和 Experience Cloud ID 请求](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [数据收集 CNAME 和跨域跟踪](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [结合了 JavaScript 技术的服务器端实施](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [ID 服务宽限期](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)
   + [内容安全策略和 Experience Cloud ID 服务](mcvid-reference/mcvid-csp.md)
   + [Experience Cloud ID 服务中的 COPPA 支持](mcvid-reference/mcvid-coppa.md)
   + [Experience Cloud ID 服务中的 CORS 支持](mcvid-reference/mcvid-cors.md)
   + [客户 ID 和身份验证状态](mcvid-reference/mcvid-authenticated-state.md)
   + [从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID](mcvid-reference/mcvid-regions.md)
   + [Experience Cloud ID 服务的要求](mcvid-reference/mcvid-requirements.md)
   + [视频心率和 Experience Cloud ID 服务](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench 和 Experience Cloud ID 服务](mcvid-reference/mcvid-dwb.md)
+ 常见问题解答 {#faqs}
   + [常见问题解答概述](mcvid-faq-intro/mcvid-faq-intro.md)
   + [ID 服务常见问题解答](mcvid-faq-intro/mcvid-faq.md)
   + [Analytics 和 ID 服务常见问题解答](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [其他 Experience Cloud 解决方案的常见问题解答](mcvid-faq-intro/mcvid-other-faq.md)
+ ID服务的发行说明 {#release-notes}
   + [2019 版发行说明](mcvid-release-notes/mcvid-release-notes.md)
   + [2018 版发行说明](mcvid-release-notes/mcvid-notes-2018.md)
   + [2017 版发行说明](mcvid-release-notes/mcvid-notes-2017.md)
   + [2016 版发行说明](mcvid-release-notes/mcvid-notes-2016.md)
   + [2015 版发行说明](mcvid-release-notes/mcvid-notes-2015.md)
