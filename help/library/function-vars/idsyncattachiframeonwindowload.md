---
description: 可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。
keywords: ID Service
seo-description: 可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 79%

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。

**语法：**` `idSyncAttachIframeOnWindowLoad= true|false``（默认值为 `false`。）

当 `idSyncAttachIframeOnWindowLoad: true` 时，ID 服务在窗口加载上加载 ID 同步 iFrame。默认情况下，ID服务以尽可能快的速度加载ID同步iFrame，而不是在加载窗口时加载。

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

