---
description: 访客ID服务在Adobe CX Enterprise中的角色。
keywords: 访客 ID 服务
title: 概述
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 25%

---

# 关于访客ID服务{#aboutidservice}

访客ID服务在Adobe CX Enterprise中的角色。

<!--
mcvid-functionality.xml
-->

## 访客ID服务：核心服务的基本元素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

访客ID服务允许将通用识别框架用于CX Enterprise核心服务、解决方案以及客户属性和受众。 它的工作方式是为网站访客分配一个唯一的永久ID。 当您的组织实施访客ID服务时，此ID允许您在不同的CX企业解决方案中识别同一站点访客及其数据。

![](assets/ecid-new.png)

此外，访客ID服务可以替换不同的解决方案专属ID（例如Analytics AID）。 而且，通过[客户ID和身份验证状态](../reference/authenticated-state.md)功能，访客ID服务允许您将自己的客户ID传递到CX Enterprise。 但是，请记住，访客ID服务仅适用于您已经订阅的解决方案。 它不会提供对您未注册的其他产品的访问权限。

今后，访客ID服务将成为许多当前和将来推出的CX Enterprise功能、增强功能和服务中的必备组件。 目前，访客ID服务支持[Analytics](http://www.adobe.com/cn/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/cn/marketing-cloud/data-management-platform.html)和[Target](http://www.adobe.com/cn/marketing-cloud/testing-targeting.html)。 另外，如果您要参与Adobe设备协作，也需要使用该服务。 如果您尚未实施访客ID服务，现在是时候开始考虑迁移策略了。

## 功能摘要 {#section-96555473455c4bf8924c2d56ff4f3255}

总之，访客ID服务：

* 创建可用于关联轮廓和身份标识的公共键或 ID。
* 跨多种解决方案唯一标识设备。
* 在客户的域中设置第一方 Cookie 以确保在同一域上跟踪。 查看[Cookie和访客ID服务](../introduction/cookies.md)。
* 接收来自CX企业客户和合作伙伴的别名和ID映射。
* 管理CX Enterprise中的ID同步。
* 支持与广告技术生态系统中的不同第三方进行 ID 同步。

