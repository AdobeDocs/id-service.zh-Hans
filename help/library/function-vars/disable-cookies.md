---
description: 可选的布尔标志，可防止Experience Cloud ID服务返回第三方、demdex. net cookie。
keywords: ID 服务
seo-description: 可选的布尔标志，可防止Experience Cloud ID服务返回第三方、demdex. net cookie。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

可选的布尔标志，可防止Experience Cloud ID服务返回第三方、demdex. net cookie。

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**语法：**`disableThirdPartyCookies: true|false` (默认 `false`为。)`VisitorAPI.js` 对于v1.5.3或更高版本。

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). 如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 Experience Cloud ID (MID) 或返回现有的 ID。作为替代，ID 服务会在第一方 Cookie 中新建一个随机 MID。启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 Experience Cloud 解决方案之间共享该数据。

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

