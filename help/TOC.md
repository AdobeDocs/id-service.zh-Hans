---
audience: end-user
user-guide-title: Experience Cloud Identity Service 帮助
breadcrumb-title: Identity Service 指南
user-guide-description: Adobe Experience Cloud Identity Service 提供了一个通用的永久性 ID，用于在 Experience Cloud 的所有解决方案中标识您的访客。它有助于替换 Experience Cloud 解决方案和服务的旧版 ID 生成代码。
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 6ef86bdb7bc10e24dbd3efe2481cb2e6e6c270fb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 98%

---


# Experience Cloud Identity Service 帮助 {#using}

+ [Identity Service 帮助](home.md)
+ 概述 {#intro}
   + [概述](introduction/overview.md)
   + [关于 ID 服务](introduction/about-id-service.md)
   + [Cookie 和 ID 服务](introduction/cookies.md)
   + [ID 服务如何请求和设置 ID](introduction/id-request.md)
   + [了解同步和匹配率](introduction/match-rates.md)
+ 实施 {#implementation}
   + [实施方法](implementation-guides/implementation-methods.md)
   + [实施指南](implementation-guides/implementation-guides.md)
   + [用 Experience Platform 标记进行实施](implementation-guides/ecid-implement-with-launch.md)
   + [为 Analytics 实施](implementation-guides/setup-analytics.md)
   + [为 Target 实施](implementation-guides/setup-target.md)
   + [为 Analytics 和 Audience Manager 实施](implementation-guides/setup-aam-analytics.md)
   + [为 Analytics、Audience Manager 和 Target 实施](implementation-guides/setup-aam-analytics-target.md)
   + [将 ID 服务用于 A4T 以及 Target 的某个服务器端实施](implementation-guides/ecid-a4t-target.md)
   + [直接与 ID 服务集成](implementation-guides/direct-integration.md)
   + [直接集成用例](implementation-guides/direct-integration-examples.md)
   + [测试和验证 ID 服务](implementation-guides/test-verify.md)
   + 选择加入服务 {#opt-in-service}
      + [选择加入服务概述](implementation-guides/opt-in-service/optin-overview.md)
      + [设置选择加入服务](implementation-guides/opt-in-service/getting-started.md)
      + [验证选择加入服务](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Experience Platform Launch 配置选择加入](implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 配置选择加入](implementation-guides/opt-in-service/optin-dtm.md)
      + [经用户同意控制 Experience Cloud 活动](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [选择加入用例](implementation-guides/opt-in-service/use-cases.md)
      + [选择加入参考](implementation-guides/opt-in-service/api.md)
      + [在 IAB 框架中使用选择加入服务](implementation-guides/opt-in-service/iab.md)
+ ID 服务 API {#id-service-api}
   + [ID 服务 API 概述](library/library.md)
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
   + Analytics 参考 {#analytics-reference}
      + [Analytics 参考概述](reference/analytics-reference/analytics-reference.md)
      + [CNAME 实施概述](reference/analytics-reference/cname.md)
      + [设置 Analytics 和 Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID 操作顺序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID 服务迁移决策点](reference/analytics-reference/migration-decisions.md)
      + [ID 服务迁移方案](reference/analytics-reference/migration-scenarios.md)
      + [Analytics 和 Identity 请求](reference/analytics-reference/legacy-analytics.md)
      + [结合了 JavaScript 技术的服务器端实施](reference/analytics-reference/server-side.md)
      + [ID 服务宽限期](reference/analytics-reference/grace-period.md)
   + [Google Chrome SameSite 标签更改](reference/chrome-samesite-labelling.md)
   + [内容安全策略和 ID 服务](reference/csp.md)
   + [ID 服务中的 COPPA 支持](reference/coppa.md)
   + [ID 服务中的 CORS 支持](reference/cors.md)
   + [客户 ID 和身份验证状态](reference/authenticated-state.md)
   + [Safari ITP 中的 ECID 库方法](reference/ecid-library-methods.md)
   + [识别独特访客](reference/unique-vis-method.md)
   + [从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID](reference/regions.md)
   + [ID 服务的要求](reference/requirements.md)
   + [视频心率和 ID 服务](reference/heartbeat.md)
   + [Data Workbench 和 ID 服务](reference/dwb.md)
   + [支持用 SHA256 哈希处理 setCustomerIDs](reference/hashing-support.md)
+ 常见问题解答 {#faqs}
   + [常见问题解答概述](faq-intro/faq-intro.md)
   + [ID 服务常见问题解答](faq-intro/faq.md)
   + [Analytics 和 ID 服务常见问题解答](faq-intro/analytics-faq.md)
   + [其他 Experience Cloud 解决方案的常见问题解答](faq-intro/other-faq.md)
+ ID 服务的发行说明 {#release-notes}
   + [2022版发行说明](release-notes/notes-2022.md)
   + [2021版发行说明](release-notes/notes-2021.md)
   + [2020 版发行说明](release-notes/notes-2020.md)
   + [2019 版发行说明](release-notes/notes-2019.md)
   + [2018 版发行说明](release-notes/notes-2018.md)
   + [2017 版发行说明](release-notes/notes-2017.md)
   + [2016 版发行说明](release-notes/notes-2016.md)
   + [2015 版发行说明](release-notes/notes-2015.md)
+ [Analytics 测试，不会在目录中显示](analytics-test-file-hidetoc.md)
