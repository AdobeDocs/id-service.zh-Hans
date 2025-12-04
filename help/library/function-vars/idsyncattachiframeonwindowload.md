---
description: 可控制 Experience Cloud 身份标识服务如何加载 ID 同步 iFrame 的可选布尔标记。
keywords: ID 服务
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

可控制 Experience Cloud 身份标识服务如何加载 ID 同步 iFrame 的可选布尔标记。

**语法：**` `idSyncAttachIframeOnWindowLoad= true|false``（默认值为 `false`。）

当 `idSyncAttachIframeOnWindowLoad: true` 时，ID 服务在窗口加载上加载 ID 同步 iFrame。默认情况下，ID 服务会尽快加载 ID 同步 iFrame，而不是在窗口加载时才加载。

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

