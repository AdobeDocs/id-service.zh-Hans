---
description: Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。
keywords: ID 服务
title: 概述
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 96%

---

# 关于 ID 服务{#aboutidservice}

Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。

<!--
mcvid-functionality.xml
-->

## Experience Cloud Identity 服务：核心服务的基本元素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud Identity 服务允许将通用识别框架用于 Experience Cloud 核心服务、解决方案、客户属性和受众。它的工作方式是为网站访客分配一个唯一的永久ID。 当您的组织实施 ID 服务时，此 ID 允许您在不同的 Experience Cloud 解决方案中识别同一网站访客及其数据。

![](assets/ecid-new.png)

另外，ID 服务可以替换不同的解决方案专属 ID（例如 Analytics AID）。而且，通过[客户 ID 和身份验证状态](../reference/authenticated-state.md)功能，ID 服务允许您将自己的客户 ID 传递到 [!DNL Experience Cloud]。但请注意，ID 服务只能与您已订阅的解决方案配合使用。它不会提供对您未注册的其他产品的访问权限。

今后，ID 服务将成为许多当前和将来推出的 [!DNL Experience Cloud] 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。另外，如果您要参与 [!DNL Adobe Experience Cloud] 设备协作，也需要使用该服务。如果尚未实施 ID 服务，则现在应考虑采用某种迁移策略。

## 功能摘要 {#section-96555473455c4bf8924c2d56ff4f3255}

总之，ID 服务会：

* 创建可用于关联配置文件和身份的公共键或 ID。
* 跨多种解决方案唯一标识设备。
* 在客户的域中设置第一方 Cookie 以确保在同一域上跟踪。请参阅 [Experience Cloud](../introduction/cookies.md)。
* 接收来自 [!DNL Experience Cloud] 客户和合作伙伴的别名和 ID 映射。
* 管理 [!DNL Experience Cloud] 内的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。
