---
description: 对于 URL 最后两个部分中任一部分多于 2 个字符的多部分顶级域，此变量是必需的。
keywords: ID 服务
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# cookieDomain{#cookiedomain}

对于 URL 最后两个部分中任一部分多于 2 个字符的多部分顶级域，此变量是必需的。

**语法：**`cookieDomain: "*`URL`*"`（不需要 `www` 前缀。）

**用例**

* 必需：`www.example.com.uk`
* 非必需：`www.example.co.uk`

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

