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

[SHA256散列支持setCustomerID](/help/reference/hashing-support.md)。Experience Cloud ID服务(EID)支持SHA-256哈希哈希算法，它允许您传递客户ID或电子邮件地址，并传递散列的ID。

**修复、增强和改进**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## 版本 4.3 {#version-4point3}

**支持ITP2.1**。如果在第一方CNAME中设置了跟踪服务器，则将使用EID值放置新cookie(s_ ecid)。ECID库引用该值，将ID保留在天之外。See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Secretokie config错误修复。**

## 4.0 版 {#section-51a4be943bbe41558f196ef2654513e2}

**选择加入服务**。选择加入是 Experience Cloud ID (ECID) 的一项扩展，它允许您控制 Experience Cloud 库是否可以为访客在网页上创建 Cookie，如果是，具体是哪些解决方案。Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 项目 | 描述 |
|---|---|
| `disableIdSyncs` 标记在传递字符串时不起作用。 | 已修复。现在接受对 `getInstance` 函数的 `disableidSyncs` 参数设置的值。 |
| 第三方 iFrame 没有获得 ECID | 修复了 Safari Mobil 上的 ECID 以及各种 iFrame 中的 ECID 不起作用的问题。 |

