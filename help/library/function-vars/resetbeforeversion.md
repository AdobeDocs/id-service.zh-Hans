---
description: 此配置允许您根据要更新的 ID 服务版本清除孤立或过时的 Experience Cloud ID (ECID)。
keywords: ID 服务
seo-description: 此配置允许您根据要更新的 ID 服务版本清除孤立或过时的 Experience Cloud ID (ECID)。
seo-title: 'resetBeforeVersion '
title: 'resetBeforeVersion '
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion {#resetbeforeversion}

此配置允许您根据要更新的 ID 服务版本清除孤立或过时的 Experience Cloud ID (ECID)。

如果将您的 ID 服务版本作为 `resetBeforeVersion` 变量的值提供，则将会导致从客户端 ID 清除过时的 ECID。

某些条件（例如会话超时）有时可能会导致生成客户端 ID，但 ID 服务未能成功获取服务器端 ID。出现这种情况时，ID 服务会跟踪孤立的客户端 ID，而无法跨域跟踪或与其他解决方案正确同步。该行为会将当前 AMCV Cookie 中的版本与 `resetBeforeVersion` 的值进行比较。如果 Cookie 不存在或者 Cookie 的版本比 `resetBeforeVersion` 的最新发布版本低（旧），系统则会删除 AMCV Cookie 并且 ID 服务会请求新的 ECID。

对于在浏览器上拥有第三方 Demdex Cookie 的访客，系统将会检查 ECID 以确定它是否是使用 Demdex Cookie 中的 UUID 正确生成的。如果该检查证明事实如此，则新的 ECID 将仍为该 ECID，而访客将被视为新访客。如果出于某种原因清除的 ECID 不是使用 Demdex Cookie 生成的，或者如果没有 Demdex Cookie，则访客将收到新的 ECID 并将被视为新访客。

**语法：**`resetBeforeVersion = "3.3"`

**代码示例**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

