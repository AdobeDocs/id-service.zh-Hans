---
description: 返回在实施Experience Cloud ID服务之前存储在s_ vi cookie中的旧版Analytics ID(如果有)。如果从未为访客分配 Analytics ID，则返回空符串。
keywords: ID 服务
seo-description: 返回在实施Experience Cloud ID服务之前存储在s_ vi cookie中的旧版Analytics ID(如果有)。如果从未为访客分配 Analytics ID，则返回空符串。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8dfc-9fc1-4105-b377-d9 b4 d247 a0 f8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

返回在实施Experience Cloud ID服务之前存储在s_ vi cookie中的旧版Analytics ID(如果有)。如果从未为访客分配 Analytics ID，则返回空符串。

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
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. 例如，当您将隐藏表单元素中的访客 ID 传递至使用数据插入 API 的服务器端应用程序时，会用到这两个标识符。In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**“aid”参数是一个旧版值**

当满足以下 2 组不同的条件时，`aid` 参数会出现在查询字符串中。

**用例 1**

对于下面的情况，您会在查询字符串中看到 `aid` 参数：

* [!DNL Experience Cloud] ID服务部署正确。
* 访问站点的用户在其 [!DNL Analytics]s_vi Cookie[ 中存储了预先存在的 ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) ID。

**用例 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ This]
>
>* [Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

