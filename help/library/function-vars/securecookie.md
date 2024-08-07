---
description: 一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。
keywords: ID 服务
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 100%

---

# secureCookie{#securecookie}

一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。

此配置属性在 `visitorAPI` 版本 3.3.0 中提供。

>[!NOTE]
>
>`SecureCookie` 配置不适用于不安全的域，并且可能会由于访问使用不安全的协议而无法接收 MID 值。只有当您确定所有页面和子域始终使用安全协议时，才应将 `secureCookie` 配置设置为 `true`。

**语法：**`secureCookie: true | false`（默认值）

**代码示例**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
