---
description: 可阻止 Experience Cloud ID 服务返回第三方 demdex.net Cookie 的可选布尔标记。
keywords: ID 服务
seo-description: 可阻止 Experience Cloud ID 服务返回第三方 demdex.net Cookie 的可选布尔标记。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

可阻止 Experience Cloud ID 服务返回第三方 demdex.net Cookie 的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisable3rdPartySyncing`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableThirdPartyCookies`。

**语法：**`disableThirdPartyCookies: true|false`（默认值为 `false`。）适用于 `VisitorAPI.js` v1.5.3 或更高版本。

当 `disableThirdPartyCookies: true` 时，ID 服务不会返回第三方 demdex.net Cookie（请参阅 [Cookie 和 Experience Cloud ID 服务](../../introduction/cookies.md)）。如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 Experience Cloud ID (MID) 或返回现有的 ID。作为替代，ID 服务会在第一方 Cookie 中新建一个随机 MID。启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 Experience Cloud 解决方案之间共享该数据。

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

