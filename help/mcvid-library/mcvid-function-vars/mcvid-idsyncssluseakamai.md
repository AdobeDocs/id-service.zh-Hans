---
description: 指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。
keywords: ID 服务
seo-description: 指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501cc37-c3 ab-4454-bfcf-3e3 c3 e3 b5 ca3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

指定目标发布模板是否应当使用 Akamai 进行 HTTPS 连接。

`idSyncSSLUseAkamai` 配置基于每个合作伙伴启用。

**语法: ** `idSyncSSLUseAkamai: true`

**代码示例**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

