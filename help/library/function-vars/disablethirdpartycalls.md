---
description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
keywords: cross domain tracking;ID Service
seo-description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 58%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

可阻止 ID 服务对其他域进行调用的可选布尔标记。

**语法：**` `disableThirdPartyCalls: true|false``（默认值为 `false`。）

若 `disableThirdPartyCalls: true`，则 ID 服务将不会对其他域进行调用。

**用途**

此变量针对需要：

* 防止ID服务从其安全、经过身份验证的页面发出调用。
* 站点访客具有Experience CloudID(MID)。
* 其他Experience Cloud解决方案可正常工作。

**实施战略**

由于其他Experience Cloud解决方案依赖于MID，因此ID服务会调用Adobe返回并设置此ID。 如果您需要停止 ID 服务从网站经过身份验证的部分进行调用，请首先从不需要身份验证的页面进行所需调用。您的网站访客拥有 MID 后，可以在经过身份验证的网站区域的 ID 服务代码中设置 `disableThirdPartyCalls= true`。这里的假设是，大多数客户在访问网站的安全部分之前都会导航到身份验证页面。

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

