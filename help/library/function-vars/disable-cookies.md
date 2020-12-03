---
description: 可阻止 Experience Cloud Identity 服务返回第三方 demdex.net Cookie 的可选布尔标记。
keywords: ID Service
seo-description: 可阻止 Experience Cloud Identity 服务返回第三方 demdex.net Cookie 的可选布尔标记。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---


# disableThirdPartyCookies{#disablethirdpartycookies}

可阻止 Experience Cloud Identity 服务返回第三方 demdex.net Cookie 的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisable3rdPartySyncing`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableThirdPartyCookies`。

**语法：**`disableThirdPartyCookies: true|false`（默认值为 `false`。）适用于 `VisitorAPI.js` v3.0.0 或更高版本。

当 `disableThirdPartyCookies: true` 时，ID 服务不会返回第三方 demdex.net Cookie（请参阅 [Cookie 和 Experience Cloud Identity 服务](../../introduction/cookies.md)）。如果站点访客的浏览器中已包含此cookie，则ID服务将不会使用它创建新Experience CloudID(MID)或返回现有ID。 相反，ID服务会在第一方Cookie中创建新的随机MID。 启用后，您可以通过ID服务收集数据并在不同的Experience Cloud解决方案之间共享它。

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

