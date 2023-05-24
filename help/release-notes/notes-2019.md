---
description: 关于 Experience Cloud 身份服务的功能发布、更新或更改。
keywords: ID 服务
title: 2019 版发行说明
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Experience Cloud 发行说明 - 2019 {#release-notes}

关于 Experience Cloud 身份服务的功能发布、更新或更改。

## 版本 4.4.1

在 ECID Launch 扩展中，为媒体分析添加了预先准备的选择加入批准复选框。

**修复**

* 解析 ECID Launch 扩展 preOptInApprovals 输入字符串时出现问题。
* 使用 trackingServer 时性能下降。

## 版本 4.4 {#version-4point4}

**新功能**

[对 setCustomerIDs 的 SHA256 哈希处理支持](/help/reference/hashing-support.md)。Experience Cloud ID 服务 (ECID) 支持 SHA-256 哈希算法，该算法允许您传入客户 ID 或电子邮件地址，并传出经过哈希处理的 ID。

**修复、增强功能和改进功能**

* 我们对 `cookieDomain` 进行了配置更新。现在，ECID 库过滤出了 `initConfig` 中的空字符串 `cookieDomain`，且使用顶级 Cookie 域，该域是通过 getDomain 方法返回的。
* 我们修复了与 `getVisitorValues` 中的 `localVisitor` 相关的错误。
* 我们修复了 Safari 浏览器中的 MCOPTOUT 值（通过 `getVisitorValue` 方法返回）存在不一致的错误。
* 我们通过添加 `optIn.off` 以取消订阅事件，更新了“选择加入”库。
* 我们修复了一个与 setTimeout 函数相关的错误，其中 `setTimeout` 在某些客户站点上违反了内容安全策略 (CSP)。

## 版本 4.3 {#version-4point3}

**支持 ITP 2.1**。如果在第一方 CNAME 中设置了跟踪服务器，则会使用 ECID 值放置新的 cookie (s_ecid)。ECID 库会引用该值，以便将 ID 保留超过 7 天。请参阅 [Safari ITP 中的 ECID 库方法](/help/reference/ecid-library-methods.md)。

**修复了 secureCookie 配置的错误。**

## 版本 4.1

根据新 API 更改，对 `publishDestinations` 进行更新。通过此更新，可以根据需要在 ID 同步期间公开此页面的反向链接信息。

## 版本 4.2

支持适用于 IAB TCF 的 Audience Manager 插件，该插件可通过 ECID 选择加入对象获取。

**修复**

* IAB + OptIn 无法获得重新访问客户的 MID。
* 修复了 DTM 中选择加入 doesOptInApply 配置的错误。
* ECID 选择退出会禁用 ID 同步。

## 版本 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**选择加入服务**。选择加入是 Experience Cloud ID (ECID) 的一项扩展，它允许您控制 Experience Cloud 库是否可以为访客在网页上创建 Cookie，如果是，具体是哪些解决方案。借助 [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)，您可以让 Analytics、Target、Audience Manager 以及其他或所有精选 Experience Cloud 解决方案能够选择加入您的同意管理系统，从而简化 Experience Cloud 解决方案收集访客是否同意选择加入的过程。

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 项目 | 描述 |
|---|---|
| `disableIdSyncs` 标记在传递字符串时不起作用。 | 已修复。现在接受对 `getInstance` 函数的 `disableidSyncs` 参数设置的值。 |
| 第三方 iFrame 无法获得 ECID | 修复了 Safari Mobil 和各种 iFrame 中的 ECID 不起作用的问题。 |
