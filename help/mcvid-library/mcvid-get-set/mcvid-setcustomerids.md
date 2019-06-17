---
description: setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。
keywords: ID 服务
seo-description: setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128 ea2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。

**语法：**`visitor.setCustomerIDs()`

您可以设置一个或多个 ID，如下面的代码示例所示。请参阅[客户 ID 和身份验证状态](../../mcvid-reference/mcvid-authenticated-state.md)，以了解更多信息和示例。

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

