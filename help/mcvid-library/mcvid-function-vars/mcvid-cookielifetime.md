---
description: 您可以使用此变量替代 AMCV Cookie 的默认生存时间间隔。
keywords: ID 服务
seo-description: 您可以使用此变量替代 AMCV Cookie 的默认生存时间间隔。
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3 f-69ac259377 a3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieLifetime{#cookielifetime}

您可以使用此变量替代 AMCV Cookie 的默认生存时间间隔。

默认情况下 [!DNL Experience Cloud] ，ID服务cookie在24个月后过期。时间间隔按秒进行设置。

**语法：**` cookieLifetime: *`生命周期(以秒为单位)`*`

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

