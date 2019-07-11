---
description: 可禁用 ID 同步的可选布尔标记。
keywords: ID 服务
seo-description: 可禁用 ID 同步的可选布尔标记。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

可禁用 ID 同步的可选布尔标记。

>[!NOTE]
>
>此配置以前名为 `idSyncDisableSyncs`，之后在 2018 年 1 月 18 日发行的版本 3.0 中被重命名为 `disableIdSyncs`。

**语法：**`disableIdSyncs: true|false`（默认值为 `false`。）

**代码示例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

