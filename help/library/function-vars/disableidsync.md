---
description: 可禁用 ID 同步的可选布尔标记。
keywords: ID 服务
seo-description: 可禁用 ID 同步的可选布尔标记。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea de8-53c8-4a15-bcf5-f0869763 a32 e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

可禁用 ID 同步的可选布尔标记。

>[!NOTE]
>
>此配置在 `idSyncDisableSyncs` 2018年月18日 `disableIdSyncs` 版本的v3.0中被重新命名。

**语法：**`disableIdSyncs: true|false` (默认 `false`为。)

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

