---
description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
keywords: 跨域跟踪；ID服务
seo-description: 可阻止 ID 服务对其他域进行调用的可选布尔标记。
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableThirdPartyCalls{#disablethirdpartycalls}

可阻止 ID 服务对其他域进行调用的可选布尔标记。

**语法：**` `disabletthirdParty调用：true| false“(默认为 `false`)”

若 `disableThirdPartyCalls: true`，则 ID 服务将不会对其他域进行调用。

**用途**

此变量专为拥有以下需求的用户设计：

* 阻止 ID 服务从其经过身份验证的安全页面进行调用。
* 网站访客拥有 Experience Cloud ID (MID)。
* 其他 Experience Cloud 解决方案可正常使用。

**实施策略**

由于其他 Experience Cloud 解决方案依赖于 MID，因此 ID 服务将调用 Adobe 以返回并设置此 ID。如果您需要停止 ID 服务从网站经过身份验证的部分进行调用，请首先从不需要身份验证的页面进行所需调用。您的网站访客拥有 MID 后，可以在经过身份验证的网站区域的 ID 服务代码中设置 `disableThirdPartyCalls= true`。在此假设大部分（如果不是全部）客户在获得网站中安全部分的访问权限之前，都会导航到身份验证页面。

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

