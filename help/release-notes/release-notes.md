---
description: 功能发布、更新或对Experience Platform Identity Service的更改。
keywords: ID 服务
seo-description: 功能发布、更新或对Experience Platform Identity Service的更改。
seo-title: 2019 发行说明
title: 2019 发行说明
uuid: a5a59410-7f85-48f9-a30 a-fef1 c2 b558
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 2019 发行说明 {#release-notes}

功能发布、更新或对Experience Platform Identity Service的更改。

## 2019 发行说明 {#topic-1b9a1c3ec5044e1c987785950f697e25}

关于 [!DNL Experience Cloud] ID 服务的功能发布、更新或更改。

## 4.0 版 {#section-51a4be943bbe41558f196ef2654513e2}

**选择加入服务**。选择加入是 [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) 的一项扩展，它允许您控制 Experience Cloud 库是否可以为访客在网页上创建 Cookie，如果是，具体是哪些解决方案。使用 [Launch](https://docs.adobelaunch.com/)，您可以让 Analytics、Target、Audience Manager 以及其他或所有精选 Experience Cloud 解决方案能够选择加入您的同意管理系统，从而简化 Experience Cloud 解决方案收集访客是否同意选择加入的过程。

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 项目 | 描述 |
|---|---|
| `disableIdSyncs` 标记在传递字符串时不起作用。 | 已修复。现在支持 `disableidSyncs``getInstance` 在函数参数上设置的值。 |
| 第三方 iFrame 没有获得 ECID | 修复了 Safari Mobil 上的 ECID 以及各种 iFrame 中的 ECID 不起作用的问题。 |

