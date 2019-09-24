---
description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID 服务
seo-description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
seo-title: 2019 版发行说明
title: 2019 版发行说明
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# 2019 发行说明 {#release-notes}

关于 Experience Cloud Identity 服务的功能发布、更新或更改。

## 2019 发行说明 {#topic-1b9a1c3ec5044e1c987785950f697e25}

关于 [!DNL Experience Cloud] ID 服务的功能发布、更新或更改。

## 版本 4.4 {#version-4point4}

**新功能**

[对 setCustomerIDs 的 SHA256 哈希处理支持](/help/reference/hashing-support.md)。Experience Cloud ID 服务 (ECID) 支持 SHA-256 哈希算法，该算法允许您传入客户 ID 或电子邮件地址，并传出经过哈希处理的 ID。

**修复、增强功能和改进功能**

* 我们对 `cookieDomain` 进行了配置更新。现在，ECID 库过滤出了 `initConfig` 中的空字符串 `cookieDomain`，且使用顶级 Cookie 域，该域是通过 getDomain 方法返回的。(CORE-29223)
* 我们修复了与 `localVisitor` 中的 `getVisitorValues` 相关的错误。(CORE-31287)
* 我们修复了 Safari 浏览器中的 MCOPTOUT 值（通过 `getVisitorValue` 方法返回）存在不一致的错误。(CORE-29719)
* 我们通过添加 `optIn.off` 以取消订阅事件，更新了“选择加入”库。
* 我们修复了一个与 setTimeout 函数相关的错误，其中 `setTimeout` 在某些客户站点上违反了内容安全策略 (CSP)。(CORE-30623)

## 版本 4.3 {#version-4point3}

**支持 ITP 2.1**。如果在第一方 CNAME 中设置了跟踪服务器，则会使用 ECID 值放置新的 cookie (s_ecid)。ECID 库会引用该值，以便将 ID 保留超过 7 天。请参阅 [Safari ITP 中的 ECID 库方法](/help/reference/ecid-library-methods.md)。

**修复了 secureCookie 配置的错误。**

## 4.0 版 {#section-51a4be943bbe41558f196ef2654513e2}

**选择加入服务**。选择加入是 Experience Cloud ID (ECID) 的一项扩展，它允许您控制 Experience Cloud 库是否可以为访客在网页上创建 Cookie，如果是，具体是哪些解决方案。Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 项目 | 描述 |
|---|---|
| `disableIdSyncs` 标记在传递字符串时不起作用。 | 已修复。现在接受对 `getInstance` 函数的 `disableidSyncs` 参数设置的值。 |
| 第三方 iFrame 没有获得 ECID | 修复了 Safari Mobil 上的 ECID 以及各种 iFrame 中的 ECID 不起作用的问题。 |

