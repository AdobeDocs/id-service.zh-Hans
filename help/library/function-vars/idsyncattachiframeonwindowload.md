---
description: 可控制 Experience Cloud 身份标识服务如何加载 ID 同步 iFrame 的可选布尔标记。
keywords: ID 服务
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
TQID: https://experienceleague.adobe.com/fEqtHlUaNadgatKX-V-7FuZn-WTZOFg-YtBOD7yKg0k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 77
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

可控制 Experience Cloud 身份标识服务如何加载 ID 同步 iFrame 的可选布尔标记。

**语法：**` `idSyncAttachIframeOnWindowLoad= true|false``（默认值为 `false`。）

当 `idSyncAttachIframeOnWindowLoad: true` 时，ID 服务在窗口加载上加载 ID 同步 iFrame。 默认情况下，ID 服务会尽快加载 ID 同步 iFrame，而不是在窗口加载时才加载。

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

