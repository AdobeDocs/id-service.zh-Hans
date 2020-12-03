---
description: 可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是用于标识特定 ID 服务数据中心的地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，您需要具有区域 ID。
keywords: ID Service
seo-description: 可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是用于标识特定 ID 服务数据中心的地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，您需要具有区域 ID。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 100%

---


# getLocationHint{#getlocationhint}

可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是用于标识特定 ID 服务数据中心的地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，您需要具有区域 ID。

**语法：**` var *`变量名称`* = visitor.getLocationHint()`

有关区域 ID 和相应位置的列表，请参阅 [DCS 区域 ID、位置和主机名](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html)。

**代码示例**

位置提示函数可从 AMCV Cookie 中读取区域 ID。如果已在 AMCV Cookie 中设置区域 ID，则会立即进行回调。如果未设置区域 ID，该函数将等待服务器做出响应，然后再将区域 ID 传递给回调。您的代码可能与以下示例类似。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

