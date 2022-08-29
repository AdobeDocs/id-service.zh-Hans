---
description: Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。
title: Experience Cloud ID 服务概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 953a4932e581a7a0019bec354201be4bc39f8b6b
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 97%

---

# Experience Cloud ID 服务概述

[!UICONTROL Experience Cloud Identity 服务]允许将通用识别框架用于 Platform Identity 服务中的 Experience Cloud 核心服务（如客户属性和受众）解决方案。

>[!NOTE]
>
> 您可能会看到 ID 服务作为缩写或以前的名称来引用，如 ECID、Marketing Cloud ID Service (MID) 和访客 ID 服务。这些都是指代 [!UICONTROL Experience Cloud Identity 服务]。您还可能会看到 [!UICONTROL Experience Platform Identity 服务]。澄清以下几点：

* [!UICONTROL Experience Platform Identity 服务]：用于链接身份的服务。它是用于基于人员的体验管理的设备链接服务。
* [!UICONTROL Experience Cloud ID 服务] (ECID)：分配给站点访客的唯一永久 ID。它是可由 Platform Identity 服务使用的特定实体。

当您的组织实施 ID 服务时，此 ID 允许您在不同的 Experience Cloud 解决方案中识别同一网站访客及其数据。

![](assets/ecid-new.png)

另外，ID 服务可以替换不同的解决方案专属 ID（例如 Analytics AID）。并且，通过[客户 ID 和身份验证状态](/help/reference/authenticated-state.md)功能，ID 服务允许您将自己的客户 ID 传递到 Experience Cloud。但请注意，ID 服务只能与您已订阅的解决方案配合使用。它不会提供对您未注册的其他产品的访问权限。

今后，ID 服务将成为许多当前和将来推出的 Experience Cloud 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。如果尚未实施 ID 服务，则现在应考虑采用某种迁移策略。

## 功能摘要

总之，ID 服务会：

* 创建可用于关联配置文件和身份的公共键或 ID。
* 跨多种解决方案唯一标识设备。
* 在客户的域中设置第一方Cookie，以确保在同一域上进行跟踪。 请参阅有关 [Cookie 和 Experience Cloud Identity 服务](./cookies.md)的文档以了解更多信息。
* 接收来自 Experience Cloud 客户和合作伙伴的别名和 ID 映射。
* 管理 Experience Cloud 内部的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

## ID 服务要求

您的解决方案和其他 Adobe 代码库必须符合[特定要求](/help/reference/requirements.md)，您才能使用 ID 服务。

* [Cookie 和 Experience Cloud Identity 服务](cookies.md)：ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
* [Experience Cloud Identity 服务如何请求和设置 ID](id-request.md)：ID 请求和响应过程的概述。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
* [了解 ID 同步和匹配率](match-rates.md)：关于 Experience Cloud Identity 服务（包括 Adobe Media Optimizer 和 ID 服务）中 ID 同步流程和匹配率的概述。
