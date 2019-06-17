---
description: getMarketingCloudVisitorID 可返回 Experience Cloud 访客 ID。
keywords: ID 服务
seo-description: getMarketingCloudVisitorID 可返回 Experience Cloud 访客 ID。
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5 b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID 可返回 Experience Cloud 访客 ID。

**语法：**` var *`变量名称`* = visitor.getMarketingCloudVisitorID()`

这种方法通常用在要求读取访客 ID 的自定义解决方案中。标准实施中并不使用此方法。`getMarketingCloudVisitorID` 还可以与回调函数结合使用，以读取 [!DNL Analytics] ID，并将它们添加到您的系统或应用程序中。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>如果您是 [!DNL Analytics] 客户，还可以检查并将 [!DNL Analytics] ID发送到您的函数。例如，当您将隐藏表单元素中的访客 ID 传递至使用数据插入 API 的服务器端应用程序时，会用到这两个标识符。在这种情况下，您应收集和返回 [!DNL Experience Cloud][!DNL Analytics] 访客ID。请参阅 [获取Analytics访问者ID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)。
