---
description: 可返回在实施 Experience Cloud ID 服务之前存储在 s_vi Cookie 中的旧版 Analytics ID（如果存在）。如果从未为访客分配 Analytics ID，则返回空符串。
keywords: ID 服务
seo-description: 可返回在实施 Experience Cloud ID 服务之前存储在 s_vi Cookie 中的旧版 Analytics ID（如果存在）。如果从未为访客分配 Analytics ID，则返回空符串。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8dfc-9fc1-4105-b377-d9 b4 d247 a0 f8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

可返回在实施 Experience Cloud ID 服务之前存储在 s_vi Cookie 中的旧版 Analytics ID（如果存在）。如果从未为访客分配 Analytics ID，则返回空符串。

**语法** `var analyticsID = visitor.getAnalyticsVisitorID()`

通常，此函数用在要求读取访客 ID 的自定义解决方案中。标准实施中并不使用此方法。`getAnalyticsVisitorID` 还可以与回调函数结合使用，以读取 [!DNL Analytics] ID，并将它们添加到您的系统或应用程序中。

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
>如果您是 [!DNL Analytics] 客户，还可以检查并将 [!DNL Analytics] ID发送到您的函数。例如，当您将隐藏表单元素中的访客 ID 传递至使用数据插入 API 的服务器端应用程序时，会用到这两个标识符。在这种情况下，您应收集和返回 [!DNL Experience Cloud][!DNL Analytics] 访客ID。请参阅 [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md)。

**“aid”参数是一个旧版值**

当满足以下 2 组不同的条件时，`aid` 参数会出现在查询字符串中。

**用例 1**

对于下面的情况，您会在查询字符串中看到 `aid` 参数：

* [!DNL Experience Cloud] ID服务部署正确。
* 访问站点的用户在其 [!DNL Analytics]s_vi Cookie[ 中存储了预先存在的 ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) ID。

**用例 2**

您的单位 `aid` 在完全实施ID服务前使用 [宽限期](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) ，您将在查询字符串中看到该参数。如果访问您的站点的用户是新的，并且您没有使用宽限期，则访客将获得 `mid` ( [!DNL Experience Cloud] ID)参数。

>[!MORE_ LIKE_ This]
>
>* [Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

