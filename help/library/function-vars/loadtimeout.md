---
description: 设置超时时间间隔（以毫秒为单位）。 用于告诉其他解决方案(如分析、Audience Manager、目标等) 等待ID服务响应的时间。
keywords: ID Service
seo-description: 设置超时时间间隔（以毫秒为单位）。 用于告诉其他解决方案(如分析、Audience Manager、目标等) 等待ID服务响应的时间。
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 14%

---


# loadTimeout{#loadtimeout}

设置超时时间间隔（以毫秒为单位）。 用于告诉其他解决方案(如分析、Audience Manager、目标等) 等待ID服务响应的时间。

**语法：**` loadTimeout: *` 时间间隔（以毫秒为单位）`*`

默认值为30,000毫秒（30秒）。 我们强烈建议您 *不要* 更改默认值。

>[!NOTE]
>
>对 ID 服务的调用与页面中其他非 Adobe 代码存在异步关系。因此，增加或减少超时间隔不会更改页面呈现内容的速率。 但是，长超时时间间隔可能影响常用网络监视工具测量的页面加载时间，但渲染时间不受影响。

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

