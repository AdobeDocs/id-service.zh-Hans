---
description: AMCV cookie包含Experience Cloud ID(MID)和站点访客的区域ID。 这些ID作为键值对存储。 mid user ID 包含访客的 Experience Cloud ID。aamlh region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。
keywords: ID Service
seo-description: AMCV cookie包含Experience Cloud ID(MID)和站点访客的区域ID。 这些ID作为键值对存储。 mid user ID 包含访客的 Experience Cloud ID。aamlh region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。
seo-title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV cookie包含Experience Cloud ID(MID)和站点访客的区域ID。 这些ID作为键值对存储。 mid:user ID包含访客的Experience Cloud ID。 aamlh:region ID包含站点访客的区域ID。 您可以通过解析 AMCV Cookie 来恢复此信息。

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

如果您是 [!DNL Audience Manager] 客户，则可以从数据收集服务器 (DCS) 发送的响应中获取区域 ID。See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

您还可以通过 ID 服务提供的 `GET` 方法获取区域 ID。请参阅[获取区域 ID（位置提示）](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。
