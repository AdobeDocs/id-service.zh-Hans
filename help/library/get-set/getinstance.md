---
description: getInstance 会返回指定 Experience Cloud 组织 ID 的访客 ID 对象。这是初始化通过 s.visitor 提供给 AppMeasurement 的访客 ID 对象所必需的。
keywords: ID 服务
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---

# getInstance{#getinstance}

getInstance 会返回指定 Experience Cloud 组织 ID 的访客 ID 对象。这是初始化通过 s.visitor 提供给 AppMeasurement 的访客 ID 对象所必需的。

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
>当 `var visitor = new Visitor` 时，*请不要*&#x200B;实例化访客功能。您必须使用此处介绍的正确函数调用。适用于 [!UICONTROL VisitorAPI.js] 代码库版本 3.0 或更高版本。

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

如果 `getInstance` 未找到现有实例，则会创建并返回一个新实例。这与 [!DNL AppMeasurement] 中的 [`s_gi()` 函数](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=zh-Hans)类似。

**常见用法**

[!DNL Experience Cloud] ID 服务 API 维护一个实例列表，其中包含为每个 [!DNL Adobe Experience Cloud] 组织 ID 创建的所有实例。如果使用 ID 服务 API 的应用程序没有传递对实例的引用，它可以通过调用 `getInstance` 来查找该实例，而不是创建一个新实例。此外，该函数还可以为同一网页或应用程序中不同组织的多个实例提供支持。

这对于不具备清晰的 `init` 阶段、但是需要在多个位置调用 ID 服务 API 的应用程序而言，非常有用。您可以在所有这些位置中调用 `getInstance`，第一次执行调用时，将创建实例。后续调用将返回现有实例。
