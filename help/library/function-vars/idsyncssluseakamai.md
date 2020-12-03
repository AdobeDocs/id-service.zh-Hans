---
description: 指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。
keywords: ID Service
seo-description: 指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '50'
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

