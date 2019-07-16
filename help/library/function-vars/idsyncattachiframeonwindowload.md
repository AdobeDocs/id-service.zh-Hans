---
description: 可选的布尔标志，用于控制Experience Platform Identity Service如何加载ID同步iFrame。
keywords: ID 服务
seo-description: 可选的布尔标志，用于控制Experience Platform Identity Service如何加载ID同步iFrame。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

可选的布尔标志，用于控制Experience Platform Identity Service如何加载ID同步iFrame。

**语法：**` `idSyncAttachIframeOnWindowLoad= true|false``（默认值为 `false`。）

当 `idSyncAttachIframeOnWindowLoad: true` 时，ID 服务在窗口加载上加载 ID 同步 iFrame。默认情况下，ID 服务将尽快加载 ID 同步 iFrame，而不是在加载窗口时加载。

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

