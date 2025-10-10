---
description: 设置超时间隔（以毫秒为单位）。用于告知其他解决方案(例如Analytics、Audience Manager、Target等)需要等待ID服务响应多长时间。
keywords: ID 服务
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

设置超时间隔（以毫秒为单位）。用于告知其他解决方案(例如Analytics、Audience Manager、Target等)需要等待ID服务响应多长时间。

**语法：**`loadTimeout: *` 时间间隔（以毫秒为单位）`*`

默认值为 30,000 毫秒（30 秒）。我们强烈建议您&#x200B;*不要*&#x200B;更改默认值。

>[!NOTE]
>
>对 ID 服务的调用与页面中其他非 Adobe 代码存在异步关系。因此，增大或减小超时间隔不会更改您的页面呈现内容的速率。但是，较长的超时间隔可能会影响通过常用网络监控工具测量的页面加载速度，但呈现速度不受影响。

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
