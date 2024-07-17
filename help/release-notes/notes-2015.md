---
description: 2015 版发行说明和更新。
keywords: ID 服务
title: 2015 版发行说明
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 100%

---

# 2015 版发行说明 {#release-notes}

2015 版发行说明和更新。

## 版本 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 [!DNL Experience Cloud] ID 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。请参阅 [Experience Cloud Identity 服务中的 COPPA 支持](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413)。适用于版本 1.5.3 或更高版本。

## 版本 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* 修复了 Safari 浏览器中的一个错误，当用户阻止使用第三方 Cookie 后，该错误会导致同步服务无法正常运行。(AAM-20764)
* 现在，调用 ID 服务的过程涉及 `d_visid_ver=` 参数中的版本 ID。返回的 ID 可帮助内部团队排除故障和解决支持问题。(AAM-20824)

## 版本 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 修复了一个错误，该错误会导致 ID 服务在没有可同步或可激发的数据时无法请求 iframe。(AAM-20164)
* 修复了一个错误，该错误会导致 ID 服务无法正确设置多部分顶级域名 Cookie。例如，如果您拥有类似于 `my_company.co.uk` 的域名，那么在某些情况下，ID 服务将只在 `co.uk` 中设置 Cookie。(AN-104683)

  这只会影响满足以下&#x200B;*所有*&#x200B;条件的几个客户端：

   * 正在使用 ID 服务。
   * 启用了[宽限期&#x200B;](../reference/analytics-reference/grace-period.md)*或者*&#x200B;正在使用第一方 Cookie 且用户阻止使用第三方 Cookie。

   * 拥有使用多部分顶级域名的页面。

此版本中的文档修订包括：

* [API 方法和代码库](../library/library.md#concept-ff27497375644a898d47984aefb21c97)：重新组织了内容和文本。在大部分情况下，每个方法都具有它自己的页面。
* [Experience Cloud Identity 服务的要求](../reference/requirements.md)：修订了内容，重新组织了文本。

## 版本 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID 服务支持多个 ID 和身份验证状态。此更改还删除了“将 [!DNL Audience Manager] DPID 映射到 `setCustomerIDs` 函数所用的用户 ID”的已弃用支持。请参阅[客户 ID 和身份验证状态](../reference/authenticated-state.md)

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

修复了对请求“AAM Blob”和“位置提示”时出现的超时的处理方式。现在，当出现超时时，系统会在当前页面上正确地将这些字段留空，并进行所有回调。超时被视为错误条件，因此它会在下一页上重试。（AN-94473、AN-94474）

## 版本 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

重新执行了 `<head>/<body>` 标签查找，以获取 JSONP 请求 `<script>` 标签容器，并且创建了 `<script>` 标签，以考虑根据区分大小写的各种可能设置，而形成的不同 DOM 实施（HTML 与 XHTML）。(AN-9355)
