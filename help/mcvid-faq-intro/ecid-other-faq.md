---
description: 与将其他 Experience Cloud 解决方案和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。
keywords: ID 服务
seo-description: 与将其他 Experience Cloud 解决方案和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。
seo-title: 其他Experience Cloud解决方案的常见问题解答
title: 其他Experience Cloud解决方案的常见问题解答
uuid: 7d848663-6cbb-4d80-ab06-7b6 d2 dc20 e2 b
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# 其他Experience Cloud解决方案的常见问题解答{#faqs-for-other-experience-cloud-solutions}

与将其他 Experience Cloud 解决方案和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**能否使用动态标签管理来部署访客 ID 服务？**

能，这是推荐的首选部署方式。

请参阅[使用 DTM 实现标准实施](../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)。

## Analytics 和 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**在实施 Experience Cloud ID 服务后，用户的访问历史记录是否将会从[!DNL Adobe Analytics]导出到[!DNL Audience Manager]？**

下面提供了两种选项：

* 如果用户在实施 ID 服务后有任何访问活动，则访客及其历史记录将会包含在导出到 [!DNL Audience Manager] 的数据中。
* 如果用户在实施 ID 服务后没有任何访问活动，则访客及其历史记录将不会包含在导出到 Audience Manager 的数据中。由于不存在新活动，因此我们无法将 Analytics ID 与 Experience Cloud ID 相关联。
