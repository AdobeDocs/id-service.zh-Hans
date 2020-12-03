---
description: Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。
seo-description: Experience Cloud Identity 服务（以前称为访客 ID 服务或 Marketing Cloud ID 服务）允许将常用识别框架用于 Experience Cloud 服务，如客户属性和受众。
seo-title: Experience Cloud ID 服务概述
title: Experience Cloud ID 服务概述
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 76%

---


# Experience Cloud ID 服务概述

[!UICONTROL Experience Cloud Identity 服务]允许将通用识别框架用于 Platform Identity 服务中的 Experience Cloud 核心服务（如客户属性和受众）解决方案。

>[!NOTE]
>
> 您可能会看到 ID 服务作为缩写或以前的名称来引用，如 ECID、Marketing Cloud ID Service (MID) 和访客 ID 服务。这些都是指代 [!UICONTROL Experience Cloud Identity 服务]。您还可能会看到 [!UICONTROL Experience Platform Identity 服务]。澄清以下几点：

* [!UICONTROL Experience Platform Identity 服务]：用于链接身份的服务。它是用于基于人员的体验管理的设备链接服务。
* [!UICONTROL Experience Cloud ID 服务] (ECID)：分配给站点访客的唯一永久 ID。它是可由 Platform Identity 服务使用的特定实体。

当您的组织实施 ID 服务时，此 ID 允许您在不同的 Experience Cloud 解决方案中识别同一站点访客及其数据。

![](assets/ecid-new.png)

此外，ID服务还可以替换不同的解决方案特定ID（例如，Analytics AID）。 And, through the [Customer IDs and Authentication States](/help/reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the Experience Cloud. 但是，请记住，ID服务只适用于您已订阅的解决方案。 如果您未注册其他产品，它将不提供对其他产品的访问。

今后，ID 服务将成为许多当前和将来推出的 Experience Cloud 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。另外，如果您要参与 Adobe Experience Cloud 设备协作，也需要使用该服务。如果您还没有实施 ID 服务，现在是时候开始考虑迁移策略了。有关 ID 服务的重要性和角色的更多信息，请参阅[为什么您应考虑使用 Experience Cloud Identity 服务](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)。

## 功能摘要

总而言之， ID服务：

* 创建可用于链接用户档案和身份的公用密钥或ID。
* 唯一标识跨多个解决方案的设备。
* 在客户的域中设置第一方Cookie，以确保在同一域上进行跟踪。 See the document on [cookies and Experience Cloud Identity Service](https://docs.adobe.com/content/help/zh-Hans/id-service/using/intro/cookies.html) for more information.
* 接收来自 Experience Cloud 客户和合作伙伴的别名和 ID 映射。
* 管理 Experience Cloud 内部的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

## ID服务要求

您的解决方案和其他Adobe代码库必 [须满足某些要](/help/reference/requirements.md) 求，才能使用ID服务。

* [Cookie 和 Experience Cloud Identity 服务](cookies.md)：ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
* [Experience Cloud Identity 服务如何请求和设置 ID](id-request.md)：ID 请求和响应过程的概述。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
* [了解 ID 同步和匹配率](match-rates.md)：关于 Experience Cloud Identity 服务（包括 Adobe Media Optimizer 和 ID 服务）中 ID 同步流程和匹配率的概述。
