---
description: 以毫秒为单位设置超时间隔。用于告知其他解决方案（如 Analytics、Audience Manager、Target 等）要等待多长时间来获取来自 ID 服务的响应。
keywords: ID 服务
seo-description: 以毫秒为单位设置超时间隔。用于告知其他解决方案（如 Analytics、Audience Manager、Target 等）要等待多长时间来获取来自 ID 服务的响应。
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

以毫秒为单位设置超时间隔。用于告知其他解决方案（如 Analytics、Audience Manager、Target 等）要等待多长时间来获取来自 ID 服务的响应。

**语法：**` loadTimeout: *` 时间间隔（以毫秒为单位）`*`

默认值为 30,000 毫秒（30 秒）。我们强烈建议您*不要*更改默认值。

>[!NOTE]
>
>对 ID 服务的调用与页面中其他非 Adobe 代码存在异步关系。因此，增加或减少超时间隔并不会更改页面渲染内容的速率。但是，较长的超时间隔可能会影响常见网络监控工具测量的页面加载时间，不过，渲染时间不受影响。

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

