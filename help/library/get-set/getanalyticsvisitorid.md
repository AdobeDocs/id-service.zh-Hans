---
description: 可返回在实施 Experience Cloud Identity 服务之前存储在 s_vi Cookie 中的旧版 Analytics ID（如果存在）。如果从未为访客分配 Analytics ID，则返回空符串。
keywords: ID 服务
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 100%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

可返回在实施 Experience Cloud Identity 服务之前存储在 s_vi Cookie 中的旧版 Analytics ID（如果存在）。如果从未为访客分配 Analytics ID，则返回空符串。

**语法** `var analyticsID = visitor.getAnalyticsVisitorID()`

通常，此函数与需要读取访客 ID 的自定义解决方案一起使用。标准实施不使用该函数。`getAnalyticsVisitorID` 还可以与回调函数结合使用，以读取 [!DNL Analytics] ID，并将它们添加到您的系统或应用程序中。

**示例代码**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>如果您是 [!DNL Analytics] 客户，那么还可以检查您的 [!DNL Analytics] ID，并将其发送给您的函数。例如，当您将隐藏表单元素中的访客 ID 传递至使用数据插入 API 的服务器端应用程序时，会用到这两个标识符。在这种情况下，您应该收集并返回 [!DNL Experience Cloud] 和 [!DNL Analytics] 访客 ID。请参阅 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md)。

**“aid”参数是一个旧版值**

当满足以下 2 组不同的条件时，`aid` 参数会出现在查询字符串中。

**用例 1**

对于下面的情况，您会在查询字符串中看到 `aid` 参数：

* [!DNL Experience Cloud] ID 服务已正确部署。
* 访问站点的用户在其 [s_vi Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hans#section-5d50a078de444d12b7d927d68ff3b679) 中存储了预先存在的 [!DNL Analytics] ID。

**用例 2**

当您的组织在完全实施 ID 服务之前使用[宽限期](../../reference/analytics-reference/grace-period.md)，您将在查询字符串中看到 `aid` 参数。如果访问您网站的是新用户，而且您没有使用宽限期，则访客将会获取 `mid` ([!DNL Experience Cloud] ID) 参数。

>[!MORELIKETHIS]
>
>* [Analytics Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=zh-Hans)
