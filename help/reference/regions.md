---
description: AMCV Cookie包含网站访客的ECID和区域ID。 这些 ID 将以键值对形式进行存储。 mid user ID包含访客的ECID。 aamlh region ID 包含网站访客的区域 ID。 您可以通过解析 AMCV Cookie 来恢复此信息。
keywords: 访客 ID 服务
title: 从AMCV Cookie或访客ID服务获取区域ID和用户ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 42%

---

# 从AMCV Cookie或访客ID服务获取区域ID和用户ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie包含网站访客的ECID和区域ID。 这些 ID 将以键值对形式进行存储。 mid:user ID包含访客的ECID。 aamlh:region ID包含网站访客的区域ID。 您可以通过解析 AMCV Cookie 来恢复此信息。

有关详细信息，请参阅[通过访客ID服务获取用户ID和区域](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=zh-Hans)。

如果您是Audience Manager客户，则可以从数据收集服务器(DCS)发送的响应中获取区域ID。 请参阅[从 DCS 响应中获取用户 ID 和区域](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=zh-Hans)。

您还可以通过访客ID服务提供的`GET`方法获取区域ID。 请参阅[获取区域 ID（位置提示）](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。

