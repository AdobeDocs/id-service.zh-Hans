---
description: 与将其他 Experience Cloud 解决方案和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。
keywords: ID 服务
title: 其他 Experience Cloud 解决方案的常见问题解答
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '186'
ht-degree: 100%

---

# 其他 Experience Cloud 解决方案的常见问题解答{#faqs-for-other-experience-cloud-solutions}

与将其他 Experience Cloud 解决方案和 ID 服务结合使用相关的特性、功能和问题的常见问题解答。

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**我可以使用动态标签管理部署访客 ID 服务吗？**

可以，这是首选和推荐的部署选项。

请参阅[使用 DTM 实现标准实施](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)。

## Analytics 和 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**在实施 Experience Cloud Identity 服务后，用户的访问历史记录是否会从 [!DNL Adobe Analytics] 导出到 [!DNL Audience Manager]？**

下面提供了两种选项：

* 如果用户在实施 ID 服务后有任何访问活动，则访客及其历史记录将会包含在导出到 [!DNL Audience Manager] 的数据中。
* 如果在实施 ID 服务后用户没有任何访问活动，该访客及其历史记录将不会添加到导出至 Audience Manager 的数据中。由于新活动不存在，因此我们无法将 Analytics ID 与 Experience Cloud ID 关联起来。
