---
description: 可阻止 Experience Cloud Identity 服务返回第三方 demdex.net Cookie 的可选布尔标记。
keywords: ID 服务
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '139'
ht-degree: 100%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

可阻止 Experience Cloud Identity 服务返回第三方 demdex.net Cookie 的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisable3rdPartySyncing`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableThirdPartyCookies`。

**语法：**`disableThirdPartyCookies: true|false`（默认值为 `false`。）适用于 `VisitorAPI.js` v3.0.0 或更高版本。

当 `disableThirdPartyCookies: true` 时，ID 服务不会返回第三方 demdex.net Cookie（请参阅 [Cookie 和 Experience Cloud Identity 服务](../../introduction/cookies.md)）。如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 Experience Cloud ID (MID) 或返回现有的 ID。ID 服务反而会在第一方 Cookie 中创建一个新的随机 ID。启用后，您可以使用 ID 服务收集数据并在不同 Experience Cloud 解决方案中共享该数据。

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
