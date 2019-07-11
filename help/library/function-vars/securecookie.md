---
description: 一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。
keywords: ID 服务
seo-description: 一个可选的布尔标记，用于向 AMCV Cookie 添加“安全”属性。
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

