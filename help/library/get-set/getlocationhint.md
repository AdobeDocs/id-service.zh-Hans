---
description: 可返回 Experience Cloud Identity 服务的区域 ID。区域ID（或位置提示）是特定ID服务数据中心的地理位置的数字标识符。 您需要受众ID，才能对区域管理器进行服务器端API调用。
keywords: ID Service
seo-description: 可返回 Experience Cloud Identity 服务的区域 ID。区域ID（或位置提示）是特定ID服务数据中心的地理位置的数字标识符。 您需要受众ID，才能对区域管理器进行服务器端API调用。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getLocationHint{#getlocationhint}

可返回 Experience Cloud Identity 服务的区域 ID。区域ID（或位置提示）是特定ID服务数据中心的地理位置的数字标识符。 您需要受众ID，才能对区域管理器进行服务器端API调用。

**语法：**` var *`变量名称`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**代码示例**

位置提示函数从AMCV cookie中读取区域ID。 如果AMCV cookie中已设置区域ID，则会立即进行回调。 如果未设置区域ID，函数将等待服务器做出响应，然后将区域ID传递给回调。 您的代码可能与以下示例类似。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

