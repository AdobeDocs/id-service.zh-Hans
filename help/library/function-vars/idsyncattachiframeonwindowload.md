---
description: 可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。
keywords: ID 服务
seo-description: 可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

可控制 Experience Cloud Identity 服务如何加载 ID 同步 iFrame 的可选布尔标记。

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
