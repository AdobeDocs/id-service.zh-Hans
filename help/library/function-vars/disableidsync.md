---
description: 可禁用 ID 同步的可选布尔标记。
keywords: ID 服务
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
TQID: https://experienceleague.adobe.com/ltW03vCXP9-8G7kJ8KwKOwAOgrsxkTxSoGzImR7dax0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 39
ht-degree: 100%

---

# disableIdSyncs{#disableidsyncs}

可禁用 ID 同步的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisableSyncs`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableIdSyncs`。

**语法：**`disableIdSyncs: true|false`（默认值为 `false`。）

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

