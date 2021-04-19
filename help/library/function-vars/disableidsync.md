---
description: 可禁用 ID 同步的可选布尔标记。
keywords: ID 服务
seo-description: 可禁用 ID 同步的可选布尔标记。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '46'
ht-degree: 100%

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
