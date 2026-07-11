---
description: 可阻止访客ID服务对其他域进行调用的可选布尔标记。
keywords: 跨域跟踪；访客ID服务
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

可阻止访客ID服务对其他域进行调用的可选布尔标记。

**语法：**` `disableThirdPartyCalls: true|false&grave;&grave;（默认值为 `false`。）

当`disableThirdPartyCalls: true`时，访客ID服务将不会对其他域进行调用。

**用途**

此变量专为存在以下需求的客户而设计：

* 阻止访客ID服务从其经过身份验证的安全页面进行调用。
* 网站访客拥有ECID。
* 让他们的其他CX Enterprise解决方案正常工作。

**实施策略**

由于其他CX Enterprise解决方案依赖于MID，因此访客ID服务会调用Adobe以返回并设置此ID。 如果您需要停止访客ID服务从网站经过身份验证的部分进行调用，请首先从不需要身份验证的页面进行所需调用。 在您的网站访客拥有MID后，您可以在经过身份验证的网站区域上的访客ID服务代码中设置`disableThirdPartyCalls= true`。 此处假设您的大多数（如果不是全部）客户都将转到身份验证页面，然后访问您网站的安全部分。

**代码示例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

