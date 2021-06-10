---
description: 指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。
keywords: ID 服务
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 100%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。

`idSyncSSLUseAkamai` 配置基于每个合作伙伴启用。

**语法：**`idSyncSSLUseAkamai: true`

**代码示例**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
