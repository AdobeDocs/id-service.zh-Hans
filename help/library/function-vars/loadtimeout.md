---
description: 设置超时间隔（以毫秒为单位）。 用于告知其他解决方案（例如Analytics、Audience Manager、Target等） 要等待多长时间才能收到ID服务的响应。
keywords: ID 服务
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 143
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

设置超时间隔（以毫秒为单位）。 用于告知其他解决方案（例如Analytics、Audience Manager、Target等） 要等待多长时间才能收到ID服务的响应。

**语法：**`loadTimeout: *` 时间间隔（以毫秒为单位）`*`

默认值为 30,000 毫秒（30 秒）。 我们强烈建议您&#x200B;*不要*&#x200B;更改默认值。

>[!NOTE]
>
>对 ID 服务的调用与页面中其他非 Adobe 代码存在异步关系。 因此，增大或减小超时间隔不会更改您的页面呈现内容的速率。 但是，较长的超时间隔可能会影响通过常用网络监控工具测量的页面加载速度，但呈现速度不受影响。

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

