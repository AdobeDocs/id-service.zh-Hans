---
description: 2015 版发行说明和更新。
keywords: ID 服务
seo-description: 2015 版发行说明和更新。
seo-title: 2015 版发行说明
title: 2015 版发行说明
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 2015 版发行说明 {#release-notes}

2015 版发行说明和更新。

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

儿童在线隐私保护法案(COPPA)禁止13岁以下儿童在线收集个人信息，不可核实地征得家长的同意。关注 COPPA 的客户可以在其 [!DNL Experience Cloud] ID 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。See [COPPA Support in the Experience Cloud ID Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). 适用于版本 1.5.3 或更高版本。

## 版本 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* 修复了 Safari 浏览器中存在的一个错误，当用户阻止第三方 Cookie 时，该错误会妨碍同步服务正常工作。(AAM-20764)
* Calls to the ID service now include the version ID in the `d_visid_ver=` parameter. 返回的 ID 可帮助内部团队进行疑难解答和解决支持问题。(AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 修复了在没有可同步或可激发的数据时造成 ID 服务无法请求 iframe 的错误。(AAM-20164)
* 修复了造成 ID 服务无法正确设置多部分顶级域名 Cookie 的错误。例如，如果您拥有类似于 `my_company.co.uk` 的域名，那么在某些情况下，ID 服务将只在 `co.uk` 中设置 Cookie。(AN-104683)

   此问题仅影响*全部*满足以下条件的少数客户：

   * 使用 ID 服务。
   * 启用了[宽限期](../reference/analytics-reference/grace-period.md)*或者*正在使用第一方 Cookie 且用户阻止使用第三方 Cookie。

   * 拥有使用多部分顶级域名的页面。

此版本中的文档修订包括：

* [API方法和代码库](../library/library.md#concept-ff27497375644a898d47984aefb21c97)：重新组织内容和文本。在大部分情况下，每个方法都具有它自己的页面。
* [Experience Cloud ID 服务的要求](../reference/requirements.md)：修订了内容，重新组织了文本。

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID 服务支持多个 ID 和身份验证状态。此更改还删除了“将 [!DNL Audience Manager] DPID 映射到 `setCustomerIDs` 函数所用的用户 ID”的已弃用支持。See [Customer IDs and Authentication States](../reference/authenticated-state.md)

## 版本 1.4 {#section-f5c596f355b14da28f45c798df513572}

2015 年 5 月

从 1.4 版本开始，配置对象中设置配置的首选方法将作为 `Visitor.getInstance` 函数的第二个参数进行传递。

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

请参阅 [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)。

## 版本 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

2015 年 2 月

修复了对 AAM Blob 和位置提示请求的超时处理。现在，对于超时而言，系统将可以正确地把当前页面的这些字段留空并执行所有回调。该超时将被认为是一个错误条件，因此会在下一页面进行重试。（AN-94473、AN-94474）

## 版本 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

Reworked `<head>/<body>` tag finding for JSONP request `<script>` tag container, as well as the creation of the `<script>` tag to account for different DOM implementations (HTML vs XHTML) with possibly different case sensitivity settings. (AN-9355)
