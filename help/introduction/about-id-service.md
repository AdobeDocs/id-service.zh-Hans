---
description: Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。
keywords: ID Service
seo-description: Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。
seo-title: 关于 ID 服务
title: 概述
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 69%

---


# 关于 ID 服务{#aboutidservice}

Experience Cloud Identity 服务在 Adobe Experience Cloud 中的角色。

<!--
mcvid-functionality.xml
-->

## Experience Cloud Identity 服务：核心服务的基本元素{#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud Identity 服务允许将通用识别框架用于 Experience Cloud 核心服务、解决方案、客户属性和受众。Identity Service 通过向网站访客分配一个唯一的永久性 ID 来工作。当您的组织实施 ID 服务时，此 ID 允许您在不同的 Experience Cloud 解决方案中识别同一站点访客及其数据。

![](assets/ecid-new.png)

此外，ID服务还可以替换不同的解决方案特定ID（例如，Analytics AID）。 And, through the [Customer IDs and Authentication States](../reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the [!DNL Experience Cloud]. 但是，请记住，ID服务只适用于您已订阅的解决方案。 如果您未注册其他产品，它将不提供对其他产品的访问。

今后，ID 服务将成为许多当前和将来推出的 [!DNL Experience Cloud] 功能、增强功能和服务中的必备组件。当前，ID 服务支持 [Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。另外，如果您要参与 [!DNL Adobe Experience Cloud] 设备协作，也需要使用该服务。如果您还没有实施 ID 服务，现在是时候开始考虑迁移策略了。有关 ID 服务的重要性和角色的更多信息，请参阅[为什么您应考虑使用 Experience Cloud Identity 服务](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)。

## 功能摘要 {#section-96555473455c4bf8924c2d56ff4f3255}

总而言之， ID服务：

* 创建可用于链接用户档案和身份的公用密钥或ID。
* 唯一标识跨多个解决方案的设备。
* 在客户的域中设置第一方Cookie，以确保在同一域上进行跟踪。 请参阅 [Experience Cloud](../introduction/cookies.md)。
* 接收来自 [!DNL Experience Cloud] 客户和合作伙伴的别名和 ID 映射。
* 管理 [!DNL Experience Cloud] 内的 ID 同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。
