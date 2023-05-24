---
description: Experience Cloud Identity Service 在 Adobe Experience Cloud 中的角色。
title: Experience Cloud Identity Service 概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Experience Cloud Identity Service 概述

Experience Cloud Identity Service 允许将通用识别框架用于 Experience Cloud 应用程序服务。您可以使用 Experience Cloud Identity Service 来设置 [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html)。

ECID 是一个跨 Adobe Experience Platform 和 Experience Cloud 应用程序使用的共享身份命名空间，可用于跟踪访客行为并确保每个设备都有一个唯一标识符（该标识符可以跨多个会话持续存在）。

>[!TIP]
>
>Experience Cloud Identity Service、Experience Platform Identity Service 和 ECID 是三个&#x200B;**不同的**&#x200B;实体。

Experience Cloud Identity Service 可以替换不同的应用程序特定 ID，并使用[客户 ID 和身份验证状态](/help/reference/authenticated-state.md)功能让您将自己的客户 ID 传递到 Experience Cloud。

>[!NOTE]
>
>Experience Cloud Identity Service 仅适用于您订阅的 Experience Cloud 应用程序服务，不会为您提供对您没有订阅的其他应用程序服务的访问权限。

Experience Cloud Identity Service 支持以下应用程序：

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

今后，ID 服务将成为许多当前和将来推出的 Experience Cloud 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。如果尚未实施 ID 服务，则现在应考虑采用某种迁移策略。

## 功能摘要

总之，Experience Cloud Identity Service 有助于：

* 跨多个应用程序在设备上唯一地标识访客。
* 在客户的域中设置第一方 Cookie 以确保在同一域上跟踪。请参阅有关 [Cookie 和 Experience Cloud Identity Service](./cookies.md) 的文档以了解更多信息。
* 接收来自 Experience Cloud 客户和合作伙伴的别名和 ID 映射。
* 管理 Experience Cloud 内部的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

## Experience Cloud Identity Service 的要求

您的解决方案和其他 Adobe 代码库必须符合[特定要求](/help/reference/requirements.md)，您才能使用 Identity Service。

* [Cookie 和 Experience Cloud Identity Service](cookies.md)：Experience Cloud Identity Service 使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 Identity Service 跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
* [Experience Cloud Identity Service 如何请求和设置 ID](id-request.md)：ID 请求和响应过程的概述。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
* [了解 ID 同步和匹配率](match-rates.md)：关于 Experience Cloud Identity Service（包括 Adobe Media Optimizer 和 Identity Service）中 ID 同步流程和匹配率的概述。
