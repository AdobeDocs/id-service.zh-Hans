---
description: 您可以使用此变量替代 AMCV Cookie 的默认生存时间间隔。
keywords: ID 服务
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

您可以使用此变量替代 AMCV Cookie 的默认生存时间间隔。

默认情况下，[!DNL Experience Cloud] ID 服务 Cookie 会在 24 个月后过期。时间间隔按秒进行设置。

**语法：**` cookieLifetime: *`存留期（以秒为单位）`*`

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
