---
description: 设置超时间隔（以毫秒为单位）。用于告知其他解决方案（例如 Analytics、Audience Manager、Target 等）要等待多长时间才能收到 ID 服务的响应。
keywords: ID 服务
seo-description: 设置超时间隔（以毫秒为单位）。用于告知其他解决方案（例如 Analytics、Audience Manager、Target 等）要等待多长时间才能收到 ID 服务的响应。
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
exl-id: 485264f4-ee24-4042-8be3-259e70462110
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '169'
ht-degree: 100%

---

# loadTimeout{#loadtimeout}

设置超时间隔（以毫秒为单位）。用于告知其他解决方案（例如 Analytics、Audience Manager、Target 等）要等待多长时间才能收到 ID 服务的响应。

**语法：**` loadTimeout: *` 时间间隔（以毫秒为单位）`*`

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
