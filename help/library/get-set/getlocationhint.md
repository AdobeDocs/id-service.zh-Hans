---
description: 可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是特定 ID 服务数据中心地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，需要区域 ID。
keywords: ID 服务
seo-description: 可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是特定 ID 服务数据中心地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，需要区域 ID。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

可返回 Experience Cloud Identity 服务的区域 ID。区域 ID（或位置提示）是特定 ID 服务数据中心地理位置的数字标识符。要对 Audience Manager 进行服务器端 API 调用，需要区域 ID。

**语法：**` var *`变量名称`* = visitor.getLocationHint()`

有关区域 ID 及对应位置的列表，请参阅 [DCS 区域 ID、位置和主机名](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html)。

**代码示例**

位置提示函数可从 AMCV Cookie 读取区域 ID。如果 AMCV Cookie 中已经设置了区域 ID，则立即执行回调。如果没有设置区域 ID，则该函数将等待服务器响应，然后再将区域 ID 传递到回调。您的代码可能与以下示例类似。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

