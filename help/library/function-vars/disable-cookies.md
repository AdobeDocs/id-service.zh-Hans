---
description: 可阻止访客ID服务返回第三方demdex.net Cookie的可选布尔标记。
keywords: 访客 ID 服务
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

可阻止访客ID服务返回第三方demdex.net Cookie的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisable3rdPartySyncing`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableThirdPartyCookies`。

**语法：**`disableThirdPartyCookies: true|false`（默认值为 `false`。） 适用于`VisitorAPI.js` v3.0.0或更高版本。

当`disableThirdPartyCookies: true`时，访客ID服务不返回第三方demdex.net Cookie（请参阅[Cookie和访客ID服务](../../introduction/cookies.md) ）。 如果网站访客的浏览器中已经具有此Cookie，则访客ID服务不会使用它来创建新的ECID或返回现有的ID。 访客ID服务而是会在第一方Cookie中创建一个新的随机MID。 启用后，您可以使用访客ID服务收集数据，并在不同的CX Enterprise解决方案中共享该数据。

**代码示例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

