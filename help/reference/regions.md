---
description: AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 作为键值对存储。中间用户ID保留访客的Experience Cloud ID。aamweaver区域ID保留站点访客的区域ID。您可以通过解析 AMCV Cookie 来恢复此信息。
keywords: ID 服务
seo-description: AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 作为键值对存储。中间用户ID保留访客的Experience Cloud ID。aamweaver区域ID保留站点访客的区域ID。您可以通过解析 AMCV Cookie 来恢复此信息。
seo-title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
title: 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID
uuid: bdd9d001-f29 f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 从 AMCV Cookie 或 ID 服务获取区域 ID 和用户 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie 包含网站访客的 Experience Cloud ID (MID) 和区域 ID。这些 ID 作为键值对存储。mid:user ID 包含访客的 Experience Cloud ID。aamlh:region ID 包含网站访客的区域 ID。您可以通过解析 AMCV Cookie 来恢复此信息。

有关详细信息，请参阅 [通过Experience Platform Identity Service获取用户ID和区域](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html)。

如果您是 [!DNL Audience Manager] 客户，则可以从数据收集服务器 (DCS) 发送的响应中获取区域 ID。请参阅[从 DCS 响应中获取用户 ID 和区域](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html)。

您还可以通过 ID 服务提供的 `GET` 方法获取区域 ID。请参阅 [获取区域ID(位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。
