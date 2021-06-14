---
description: setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。
keywords: ID 服务
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '58'
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。

**语法：**`visitor.setCustomerIDs()`

您可以设置一个或多个 ID，如下面的代码示例所示。请参阅[客户 ID 和身份验证状态](../../reference/authenticated-state.md)，以了解更多信息和示例。

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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
