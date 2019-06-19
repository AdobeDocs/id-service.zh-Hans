---
description: 可选的布尔标志，可防止Experience Platform Identity Service返回第三方、demdex. net cookie。
keywords: ID 服务
seo-description: 可选的布尔标志，可防止Experience Platform Identity Service返回第三方、demdex. net cookie。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# disableThirdPartyCookies{#disablethirdpartycookies}

可选的布尔标志，可防止Experience Platform Identity Service返回第三方、demdex. net cookie。

>[!NOTE]
>
>此配置在 `idSyncDisable3rdPartySyncing` 2018年月18日 `disableThirdPartyCookies` 版本的v3.0中被重新命名。

**语法：**`disableThirdPartyCookies: true|false` (默认 `false`为。)`VisitorAPI.js` 对于v1.5.3或更高版本。

当 `disableThirdPartyCookies: true`ID服务时，ID服务不会返回第三方、demdex. net cookie(请参阅 [Cookies和Experience Platform Identity Service](../../introduction/cookies.md) )。如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 Experience Cloud ID (MID) 或返回现有的 ID。作为替代，ID 服务会在第一方 Cookie 中新建一个随机 MID。启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 Experience Cloud 解决方案之间共享该数据。

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

