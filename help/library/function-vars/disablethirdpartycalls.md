---
description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
keywords: 跨域跟踪;ID 服务
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '200'
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

由于其他 Experience Cloud 解决方案依赖于 MID，因此 ID 服务会调用 Adobe 以返回并设置此 ID。如果您需要停止 ID 服务从网站经过身份验证的部分进行调用，请首先从不需要身份验证的页面进行所需调用。您的网站访客拥有 MID 后，可以在经过身份验证的网站区域的 ID 服务代码中设置 `disableThirdPartyCalls= true`。此处假设您的大多数（如果不是全部）客户都将转到身份验证页面，然后访问您网站的安全部分。

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
