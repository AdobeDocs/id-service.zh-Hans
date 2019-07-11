---
description: 可控制浏览器如何从 Experience Cloud ID 服务请求资源的可选布尔标记。
keywords: ID 服务
seo-description: 可控制浏览器如何从 Experience Cloud ID 服务请求资源的可选布尔标记。
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# useCORSOnly{#usecorsonly}

可控制浏览器如何从 Experience Cloud ID 服务请求资源的可选布尔标记。

**语法：**`useCORSOnly: true|false`（默认值为 `false`。）

**概述**

在设置为 `false` 时，浏览器通过 CORS 或 JSONP 执行资源检查。但是，ID 服务会始终尝试首先通过 CORS 请求资源。它会在不支持 CORS 的早期浏览器中还原为 JSONP。如果您需要强制浏览器仅使用 CORS，请在 `useCORSOnly:true` 函数调用中设置 `Visitor.getInstance`。

>[!IMPORTANT]
>
>如果您具有严格的安全要求，则 `Set useCORSOnly: true`。只有在您确信所有访客都使用支持 CORS 的浏览器时，才应启用此模式。不支持 CORS 的浏览器不会影响用户体验。但是，不支持 CORS 的浏览器无法从 [!DNL Adobe Experience Cloud] 请求资源或与之交换数据。

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

