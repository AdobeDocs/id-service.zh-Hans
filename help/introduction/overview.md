---
description: 访客ID服务在Adobe CX Enterprise中的角色。
title: Adobe访客ID服务概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Adobe访客ID服务概述

Adobe访客ID服务允许将通用识别框架用于CX企业应用程序服务。 您可以使用访客ID服务来设置[ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=zh-Hans)。

ECID是一个跨Adobe Experience Platform和CX Enterprise应用程序使用的共享身份命名空间，可用于跟踪访客行为并确保每个设备都有一个唯一标识符（该标识符可以跨多个会话持续存在）。

>[!TIP]
>
>访客ID服务、Experience Platform Identity服务和ECID是三个&#x200B;**不同的**&#x200B;实体。

访客ID服务可以替换不同的应用程序特定ID，并使用[客户ID和身份验证状态](/help/reference/authenticated-state.md)功能让您将自己的客户ID传递到CX Enterprise。

>[!NOTE]
>
>访客ID服务仅适用于您订阅的CX Enterprise应用程序服务，如果您未订阅其他应用程序服务，则不会提供对这些服务的访问权限。

访客ID服务支持以下应用程序：

* [Adobe Analytics](https://business.adobe.com/cn/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/cn/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/cn/products/target/adobe-target.html)

今后，访客ID服务将成为许多当前和将来推出的CX Enterprise功能、增强功能和服务中的必备组件。 目前，访客ID服务支持[Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html)和[Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。 如果您尚未实施访客ID服务，现在是时候开始考虑迁移策略了。

## 功能摘要

总之，访客ID服务有助于：

* 跨多个应用程序在设备上唯一地标识访客。
* 在客户的域中设置第一方 Cookie 以确保在同一域上跟踪。 有关详细信息，请参阅有关[Cookie和访客ID服务](./cookies.md)的文档。
* 接收来自CX企业客户和合作伙伴的别名和ID映射。
* 管理CX Enterprise中的ID同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

## 访客ID服务要求

您的解决方案和其他Adobe代码库必须符合[某些要求](/help/reference/requirements.md)，您才能使用访客ID服务。

* [Cookie和访客ID服务](cookies.md)：访客ID服务使用您的IMS组织ID、CX Enterprise AMCV Cookie和Demdex Cookie为网站访客创建并存储唯一的永久标识符。 这些Cookie允许访客ID服务跨不同的域跟踪访客，并允许在不同的CX Enterprise解决方案之间共享数据。
* [访客ID服务如何请求和设置ID](id-request.md)： ID请求和响应过程的概述。 这些示例涵盖了以下站点ID分配情况：单个站点上、不同站点之间，以及由具有自己IMS组织ID的不同CX Enterprise客户管理的站点。
* [了解ID同步和匹配率](match-rates.md)：关于访客ID服务（包括Adobe Media Optimizer和访客ID服务）中ID同步流程和匹配率的概述。

