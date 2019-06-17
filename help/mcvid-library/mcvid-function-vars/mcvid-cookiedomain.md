---
description: 对于 URL 最后两个部分中任一部分多于 2 个字符的多部分顶级域，此变量是必需的。
keywords: ID 服务
seo-description: 对于 URL 最后两个部分中任一部分多于 2 个字符的多部分顶级域，此变量是必需的。
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07 b-4d 548-aea-8e8 b152 f1423 f1423
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieDomain{#cookiedomain}

对于 URL 最后两个部分中任一部分多于 2 个字符的多部分顶级域，此变量是必需的。

**语法：**` cookieDomain: " *`URL`*"` ( `www` 不需要前缀。)

**用例**

* 必需: `www.example.com.uk`
* 不需要： `www.example.co.uk`

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

