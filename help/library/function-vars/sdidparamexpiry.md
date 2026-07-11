---
description: 通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将 Supplemental Data ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。 默认情况下，接收页面上的访客ID服务代码有30秒时间从引荐页面发送的URL获取SDID。 如果接收页面上的访客ID服务代码无法在30秒内检索SDID，它会请求新的SDID。 此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。
keywords: 访客 ID 服务
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
TQID: https://experienceleague.adobe.com/PUHy-KpWKY0BQSMkKidwpLYES6FvME2EtKCbCpfMFrw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 57%

---

# sdidParamExpiry{#sdidparamexpiry}

通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将 Supplemental Data ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。 默认情况下，接收页面上的访客ID服务代码有30秒时间从引荐页面发送的URL获取SDID。 如果接收页面上的访客ID服务代码无法在30秒内检索SDID，它会请求新的SDID。 此功能主要适用于需要将 SDID 从一个页面传递到另一个页面并希望控制此超时间隔的 A4T 客户。

**覆盖 SDID 超时**

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**`sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

在配置后，您的访客ID服务代码可能与以下示例类似。 此示例将 SDID 超时设为 15 秒。 此配置使用 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 帮助程序方法。

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

