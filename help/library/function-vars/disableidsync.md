---
description: 可禁用 ID 同步的可选布尔标记。
keywords: ID 服务
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '37'
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
