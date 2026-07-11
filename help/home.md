---
description: Adobe访客ID服务允许将通用识别框架用于CX Enterprise应用程序和服务。 它的工作方式是，为网站访客分配一个称为ECID的唯一的永久ID。
keywords: 访客ID服务；ECID
title: Adobe访客ID服务
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 26%

---

# Adobe访客ID服务 {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

访客ID服务是&#x200B;**而不是** [Experience Platform Identity服务](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hans)。 访客ID服务是本指南中介绍的`VisitorAPI.js` JavaScript库，用于为Adobe Analytics、Audience Manager和Target设置ECID。 如果您正在寻找可将跨设备和系统的身份解析为统一客户配置文件的Adobe Experience Platform服务，请改为参阅[Experience Platform Identity Service概述](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hans)。

>[!ENDSHADEBOX]

Adobe访客ID服务允许将通用识别框架用于CX Enterprise应用程序和服务。 它的工作方式是，为网站访客分配一个称为ECID的唯一的永久ID。

## 了解身份标识的主要实体

要更好地了解Adobe如何帮助唯一地识别访客并解析身份信息，请阅读以下细目：

* **访客ID服务**：访客ID服务&#x200B;**负责设置ECID**。 有关详细信息，请阅读[访客ID服务概述](./introduction/overview.md)。
* **ECID**： ECID是跨Adobe Experience Platform和Adobe CX Enterprise应用程序使用的共享身份命名空间，用于识别人员和设备。 有关 ECID 的更多信息，请阅读 [ECID 概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/ecid)。
* **Experience Platform 身份标识服务**：Experience Platform 身份标识服务通过跨设备和系统桥接身份，为您提供有关客户及其行为的全面视图。 有关详细信息，请参阅 [Experience Platform 身份标识服务概述](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hans)。

## 快速入门

* [访客ID服务概述](introduction/overview.md)：了解访客ID服务的功能以及它如何适应CX Enterprise。
* [访客ID服务的要求](reference/requirements.md)：在实施访客ID服务之前，请确认您的解决方案和代码库满足先决条件。
* [实施方法](implementation-guides/implementation-methods.md)：将使用[标记](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)的标准实施与非标准的直接集成方法进行比较。

## 浏览文档

**实施**

* [实施指南](implementation-guides/implementation-guides.md)
* [与访客ID服务的直接集成](implementation-guides/direct-integration.md)
* [选择加入服务概述](implementation-guides/opt-in-service/optin-overview.md)
* [测试和验证访客ID服务](implementation-guides/test-verify.md)

**API 参考**

* [访客ID服务API概述](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**常见问题解答**

* [访客ID服务常见问题解答](faq-intro/faq.md)
* [其他CX企业解决方案的常见问题解答](faq-intro/other-faq.md)

## 其他资源

* GitHub上的[ECID JavaScript库版本](https://github.com/Adobe-Marketing-Cloud/id-service/releases)
* [访客ID服务的发行说明](release-notes/notes-2022.md)
* [Adobe隐私中心](http://www.adobe.com/cn/privacy.html)
* [Adobe CX Enterprise文档](https://experienceleague.adobe.com/docs/home.html?lang=zh-Hans)

