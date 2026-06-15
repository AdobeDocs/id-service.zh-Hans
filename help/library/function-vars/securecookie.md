---
description: 一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。
keywords: ID 服务
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 93
ht-degree: 100%

---

# secureCookie{#securecookie}

一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。

此配置属性在 `visitorAPI` 版本 3.3.0 中提供。

>[!NOTE]
>
>`SecureCookie` 配置不适用于不安全的域，并且可能会由于访问使用不安全的协议而无法接收 MID 值。 只有当您确定所有页面和子域始终使用安全协议时，才应将 `secureCookie` 配置设置为 `true`。

**语法：**`secureCookie: true | false`（默认值）

**代码示例**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

