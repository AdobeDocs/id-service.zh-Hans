---
description: Experience Cloud Identity Service 在 Adobe Experience Cloud 中的角色。
title: Experience Cloud标识服务概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Experience Cloud标识服务概述

Experience Cloud标识服务为Experience Cloud应用程序服务启用通用标识框架。 您可以使用Experience Cloud标识服务来设置 [Experience CloudID(ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

ECID是跨Adobe Experience Platform和Experience Cloud应用程序使用的共享身份命名空间，用于跟踪访客行为并确保每个设备都具有可在多个会话中持久保留的唯一标识符。

>[!TIP]
>
>Experience Cloud标识服务、Experience Platform标识服务和ECID分为三个 **不同** 实体。

Experience Cloud标识服务可以替换不同的特定于应用程序的ID，并使用 [客户ID和身份验证状态](/help/reference/authenticated-state.md) 功能，让您将自己的客户ID传递到Experience Cloud。

>[!NOTE]
>
>Experience Cloud标识服务仅适用于您订阅的Experience Cloud应用程序服务，如果您未订阅，将不提供对其他应用程序服务的访问权限。

Experience Cloud标识服务支持以下应用程序：

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

今后，ID 服务将成为许多当前和将来推出的 Experience Cloud 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。如果尚未实施 ID 服务，则现在应考虑采用某种迁移策略。

## 功能摘要

总之，Experience Cloud身份服务可帮助：

* 跨多个应用程序唯一标识设备上的访客。
* 在客户的域中设置第一方 Cookie 以确保在同一域上跟踪。请参阅有关 [Cookie 和 Experience Cloud Identity Service](./cookies.md) 的文档以了解更多信息。
* 接收来自 Experience Cloud 客户和合作伙伴的别名和 ID 映射。
* 管理 Experience Cloud 内部的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

## Experience CloudIdentity服务要求

您的解决方案和其他Adobe代码库必须满足 [特定要求](/help/reference/requirements.md) 才能使用Identity服务。

* [Cookie和Experience Cloud标识服务](cookies.md):Experience Cloud身份服务Identity服务使用您的组织ID、Experience CloudAMCV Cookie和Demdex Cookie来为网站访客创建和存储唯一的永久性标识符。 通过这些Cookie，Identity服务可以跨不同的域跟踪访客，并在不同的Experience Cloud解决方案之间实现数据共享。
* [Experience Cloud Identity Service 如何请求和设置 ID](id-request.md)：ID 请求和响应过程的概述。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
* [了解ID同步和匹配率](match-rates.md):有关Experience CloudIdentity服务(包括Adobe Media Optimizer和Identity服务)中ID同步流程和匹配率的概述。
