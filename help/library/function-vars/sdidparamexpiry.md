---
description: 通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将 Supplemental Data ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码有 30 秒时间从引荐页面发送的 URL 获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒之内检索 SDID，它会请求新的 SDID。此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。
keywords: ID 服务
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将 Supplemental Data ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码有 30 秒时间从引荐页面发送的 URL 获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒之内检索 SDID，它会请求新的 SDID。此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。

**覆盖 SDID 超时**

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

若已配置，您的 ID 服务代码可能类似于此示例。此示例将 SDID 超时设为 15 秒。此配置使用 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 帮助程序方法。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
