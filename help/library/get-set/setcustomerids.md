---
description: setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。
keywords: ID 服务
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
TQID: https://experienceleague.adobe.com/PY-2KQSxqIV1xygQwSduPuq-YeYt5tY-UMGh4sRSZNM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 62
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs 可设置一个或多个定义客户 ID 及其身份验证状态的键值对。

**语法：**`visitor.setCustomerIDs()`

您可以设置一个或多个 ID，如下面的代码示例所示。 请参阅[客户 ID 和身份验证状态](../../reference/authenticated-state.md)，以了解更多信息和示例。

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

