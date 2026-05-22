---
description: 可阻止 Experience Cloud 身份标识服务返回第三方 demdex.net Cookie 的可选布尔标记。
keywords: ID 服务
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

可阻止 Experience Cloud 身份标识服务返回第三方 demdex.net Cookie 的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisable3rdPartySyncing`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableThirdPartyCookies`。

**语法：**`disableThirdPartyCookies: true|false`（默认值为 `false`。） 适用于`VisitorAPI.js` v3.0.0或更高版本。

当 `disableThirdPartyCookies: true` 时，ID 服务不会返回第三方 demdex.net Cookie（请参阅 [Cookie 和 Experience Cloud 身份标识服务](../../introduction/cookies.md)）。 如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 Experience Cloud ID (MID) 或返回现有的 ID。 ID 服务反而会在第一方 Cookie 中创建一个新的随机 ID。 启用后，您可以使用 ID 服务收集数据并在不同 Experience Cloud 解决方案中共享该数据。

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

