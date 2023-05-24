---
description: 可控制浏览器如何从 Experience Cloud Identity 服务请求资源的可选布尔标记。
keywords: ID 服务
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# useCORSOnly{#usecorsonly}

可控制浏览器如何从 Experience Cloud Identity 服务请求资源的可选布尔标记。

**语法：**`useCORSOnly: true|false`（默认值为 `false`。）

**概述**

在设置为 `false` 时，浏览器通过 CORS 或 JSONP 执行资源检查。但是，ID 服务始终会尝试先通过 CORS 请求资源。它会在不支持 CORS 的旧版浏览器上恢复为 JSONP。如果您需要强制浏览器仅使用 CORS，请在 `useCORSOnly:true` 函数调用中设置 `Visitor.getInstance`。

>[!IMPORTANT]
>
>如果您具有严格的安全要求，则 `Set useCORSOnly: true`。只有当您确信您的所有访客都使用支持 CORS 的浏览器时，才应该启用此模式。不支持 CORS 的浏览器不会影响用户体验。但是，不支持 CORS 的浏览器无法从 [!DNL Adobe Experience Cloud] 请求资源或与之交换数据。

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```
