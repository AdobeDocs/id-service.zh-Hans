---
description: getInstance 会返回指定 Experience Cloud 组织 ID 的访客 ID 对象。 这是初始化通过 s.visitor 提供给 AppMeasurement 的访客 ID 对象所必需的。
keywords: ID 服务
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 226
ht-degree: 96%

---

# getInstance{#getinstance}

getInstance 会返回指定 Experience Cloud 组织 ID 的访客 ID 对象。 这是初始化通过 s.visitor 提供给 AppMeasurement 的访客 ID 对象所必需的。

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
>当 `var visitor = new Visitor` 时，*请不要*&#x200B;实例化访客功能。 您必须使用此处介绍的正确函数调用。 适用于 [!UICONTROL VisitorAPI.js] 代码库版本 3.0 或更高版本。

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

如果 `getInstance` 未找到现有实例，则会创建并返回一个新实例。 这类似于[!DNL AppMeasurement]中的[`s_gi()`函数](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=zh-Hans)。

**常见用法**

[!DNL Experience Cloud] ID 服务 API 维护一个实例列表，其中包含为每个 [!DNL Adobe Experience Cloud] 组织 ID 创建的所有实例。 如果使用 ID 服务 API 的应用程序没有传递对实例的引用，它可以通过调用 `getInstance` 来查找该实例，而不是创建一个新实例。 此外，该函数还可以为同一网页或应用程序中不同组织的多个实例提供支持。

这对于不具备清晰的 `init` 阶段、但是需要在多个位置调用 ID 服务 API 的应用程序而言，非常有用。 您可以在所有这些位置中调用 `getInstance`，第一次执行调用时，将创建实例。 后续调用将返回现有实例。

