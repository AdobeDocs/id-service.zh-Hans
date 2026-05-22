---
description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
keywords: 跨域跟踪;ID 服务
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
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 200
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

可阻止 ID 服务对其他域进行调用的可选布尔标记。

**语法：**` `disableThirdPartyCalls: true|false``（默认值为 `false`。）

若 `disableThirdPartyCalls: true`，则 ID 服务将不会对其他域进行调用。

**用途**

此变量专为存在以下需求的客户而设计：

* 禁止 ID 服务从其经过身份验证的安全页面发出调用。
* 网站访客具有 Experience Cloud ID (MID)。
* 使其他 Experience Cloud 解决方案正常运行。

**实施策略**

由于其他 Experience Cloud 解决方案依赖于 MID，因此 ID 服务会调用 Adobe 以返回并设置此 ID。 如果您需要停止 ID 服务从网站经过身份验证的部分进行调用，请首先从不需要身份验证的页面进行所需调用。 您的网站访客拥有 MID 后，可以在经过身份验证的网站区域的 ID 服务代码中设置 `disableThirdPartyCalls= true`。 此处假设您的大多数（如果不是全部）客户都将转到身份验证页面，然后访问您网站的安全部分。

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

