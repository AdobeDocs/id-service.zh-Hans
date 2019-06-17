---
description: getInstance 可返回指定的 Experience Cloud 组织 ID 对应的访客 ID 对象。当通过 s.visitor 初始化提供给 AppMeasurement 的访客 ID 对象时，需要使用此函数。
keywords: ID 服务
seo-description: getInstance 可返回指定的 Experience Cloud 组织 ID 对应的访客 ID 对象。当通过 s.visitor 初始化提供给 AppMeasurement 的访客 ID 对象时，需要使用此函数。
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3 d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getInstance{#getinstance}

getInstance 可返回指定的 Experience Cloud 组织 ID 对应的访客 ID 对象。当通过 s.visitor 初始化提供给 AppMeasurement 的访客 ID 对象时，需要使用此函数。

**语法**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*请勿* 实例化访客函数 `var visitor = new Visitor`。您必须使用此处介绍的正确函数调用。适用于 [!DNL VisitorAPI.js] 代码库版本 3.0 或更高版本。

**ActionScript / Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

如果 `getInstance` 未找到现有实例，则会创建并返回一个新实例。这与中的 [`s_gi()` 函数 ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html)[!DNL AppMeasurement]类似。

**常见用法**

[!DNL Experience Cloud] ID服务API维护为 [!DNL Adobe Experience Cloud] 每个组织ID创建的所有实例的列表。如果使用 ID 服务 API 的应用程序没有传递对实例的引用，它可以通过调用 `getInstance` 来查找该实例，而不是创建一个新实例。此外，该函数还可以为同一网页或应用程序中不同组织的多个实例提供支持。

这对于没有清晰 `init` 阶段的应用程序很有用，但需要在多个位置调用ID服务API。您可以在所有这些位置中调用 `getInstance`，第一次执行调用时，将创建实例。后续调用将返回现有实例。
