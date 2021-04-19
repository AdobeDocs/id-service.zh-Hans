---
description: AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 将以键值对形式进行存储。mid user ID 包含访客的 Experience Cloud ID。aamlh region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。
keywords: ID 服务
seo-description: AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 将以键值对形式进行存储。mid user ID 包含访客的 Experience Cloud ID。aamlh region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。
seo-title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 将以键值对形式进行存储。mid:user ID 包含访客的 Experience Cloud ID。aamlh:region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。

有关更多信息，请参阅[通过 Experience Cloud Identity 服务获取用户 ID 和区域](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html)。

如果您是 [!DNL Audience Manager] 客户，则可以从数据收集服务器 (DCS) 发送的响应中获取区域 ID。请参阅[从 DCS 响应中获取用户 ID 和区域](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html)。

您还可以通过 ID 服务提供的 `GET` 方法获取区域 ID。请参阅[获取区域 ID（位置提示）](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。
