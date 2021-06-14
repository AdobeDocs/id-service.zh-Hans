---
description: getMarketingCloudVisitorID 可返回 Experience Cloud 访客 ID。
keywords: ID 服务
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '117'
ht-degree: 100%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID 可返回 Experience Cloud 访客 ID。

**语法：**` var *`变量名称`* = visitor.getMarketingCloudVisitorID()`

通常，此方法与需要读取访客 ID 的自定义解决方案一起使用。标准实施不使用该函数。`getMarketingCloudVisitorID` 还可以与回调函数结合使用，以读取 [!DNL Analytics] ID，并将它们添加到您的系统或应用程序中。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>如果您是 [!DNL Analytics] 客户，那么还可以检查您的 [!DNL Analytics] ID，并将其发送给您的函数。例如，当您将隐藏表单元素中的访客 ID 传递至使用数据插入 API 的服务器端应用程序时，会用到这两个标识符。在这种情况下，您应该收集并返回 [!DNL Experience Cloud] 和 [!DNL Analytics] 访客 ID。请参阅[获取 Analytics 访客 ID](../../library/get-set/getanalyticsvisitorid.md)。
