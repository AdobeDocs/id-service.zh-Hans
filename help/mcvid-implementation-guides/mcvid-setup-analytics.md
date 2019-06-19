---
description: 这些说明适用于那些希望使用 Experience Cloud ID 服务而不使用动态标签管理 (DTM) 的 Analytics 客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。
keywords: ID 服务
seo-description: 这些说明适用于那些希望使用 Experience Cloud ID 服务而不使用动态标签管理 (DTM) 的 Analytics 客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。
seo-title: 实施适用于 Analytics 的 Experience Cloud ID 服务
title: 实施适用于 Analytics 的 Experience Cloud ID 服务
uuid: fbd6fa0-1713-4232-8600-500fd6fd62709d5
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# 实施适用于 Analytics 的 Experience Cloud ID 服务 {#implement-the-experience-cloud-id-service-for-analytics}

这些说明适用于那些希望使用 Experience Cloud ID 服务而不使用动态标签管理 (DTM) 的 Analytics 客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。

>[!IMPORTANT]
>
>* [请在开始之前阅读相关要求。](../mcvid-reference/mcvid-requirements.md)
>* 请在生产环境中实施此代码之前，首先在开发环境中对它进行配置和测试。
>



按照以下步骤执行Adobe Analytics的ID服务：

1. [下载ID服务代码](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [将Compositor. getInstance函数添加到ID服务代码](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [将Experience Cloud组织ID添加到Compositor. getInstance](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [将跟踪服务器添加到Compositor. getInstance](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [更新AppMeasurement. js或s_ code. js文件](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [将访问者API代码添加到页面](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(可选)配置宽限期](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [测试和部署ID服务代码](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## 步骤1：下载ID服务代码 {#section-ead9403a6b7e45b887f9ac959ef89f7f}

它 [!DNL ID Service] 需要 `VisitorAPI.js` 代码库。要下载此代码库，请执行以下操作：

1. 转至 **[!UICONTROL 管理员]** &gt; **[!UICONTROL 代码管理器]**。
1. 在中 [!DNL Code Manager]，单击 **[!UICONTROL JavaScript(New)]** 或 **[!UICONTROL JavaScript(传统)]**。

   此下载文件对代码库进行了压缩。

1. 解压缩代码文件，并打开 `VisitorAPI.js` 文件。

## 步骤 2. 将Compositor. getInstance函数添加到ID服务代码 {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* ID 服务 API 的早期版本将此函数放置在其他位置，并且需要使用不同的语法。如果您要从[版本 1.4](../mcvid-release-notes/mcvid-notes-2015.md#section-f5c596f355b14da28f45c798df513572) 之前的版本迁移，请注意此处记录的新放置位置和语法。
>* 全部大写的代码是一个对应实际值的占位符。将此文本替换为您的组织 ID、跟踪服务器 URL 或其他指定值。
>



**第 1 部分：复制下面的 Visitor.getInstance 函数**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**第 2 部分：将函数代码添加到 VisitorAPI.js 文件中**

将 `Visitor.getInstance` 函数放置在位于文件末尾的代码块后面。您编辑的文件应该类似于下面的样子：

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## 步骤3：将Experience Cloud组织ID添加到Compositor. getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

在 `Visitor.getInstance` 函数中，替换 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 为 [!DNL Experience Cloud] 您的单位ID。如果您不知道自己的组织 ID，可以在 [!DNL Experience Cloud] 管理页面上查找。另请参阅[管理 - 核心服务](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)。您编辑的函数看起来类似于下面的示例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*请勿* 更改单位ID中字符的大小写。这个 ID 是区分大小写的，因此必须严格按照所提供的形式使用。

## 第步：将跟踪服务器添加到Compositor. getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

跟踪服务器可用于 [!DNL Analytics] 数据收集。

**第 1 部分：查找您的跟踪服务器 URL**

检查您 `s_code.js` 或 `AppMeasurement.js` 文件以查找跟踪服务器URL。您将需要由以下变量指定的 URL：

* `s.trackingServer`
* `s.trackingServerSecure`

**第 2 部分：设置跟踪服务器变量**

要确定需要使用哪些跟踪服务器变量，请执行以下操作：

1. 回答以下决策矩阵中的问题。使用与您的回答相对应的变量。
1. 将跟踪服务器占位符替换为您的跟踪服务器 URL。
1. 从代码中删除未使用的跟踪服务器和 [!DNL Experience Cloud] 服务器变量。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>使用时，将 [!DNL Experience Cloud] 服务器URL与其相应的跟踪服务器URL匹配，如下所示：&gt;
>* [!DNL Experience Cloud] 服务器URL=跟踪服务器URL
>* [!DNL Experience Cloud] 服务器安全URL=跟踪服务器安全URL
>



如果您不确定如何找到跟踪服务器，请参阅 [常见问题解答](../mcvid-faq-intro/ecid-faq.md) 并 [正确填充trackingServer和trackingServerSecure变量](https://helpx.adobe.com/analytics/kb/determining-data-center.html#)。

## 第步：更新AppMeasurement. js或s_ code. js文件 {#section-b53113aea1bd4de896e0e4e9a7edee19}

将此函数添加到您 `AppMeasurement.js` 的 `s_code.js` 或文件：

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

将代码放在包含配置等配置的同一部分 `linkInternalFilters``charSet`中 `trackDownloads`。

***（可选，但是推荐）*创建自定义 prop**

在其中设置自定义 `AppMeasurement.js` prop `s_code.js` 或测量覆盖范围。将此自定义prop添加 `doPlugins` 到您 `AppMeasurement.js` 或 `s_code.js` 文件的函数：

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 步骤6：将访问者API代码添加到页面 {#section-d46d6aa324c842f2931d901e38d6db1d}

将文件 `VisitorAPI.js` 放在每个页面 `<head>` 上的标记内。在将 `VisitorAPI.js` 文件放入页面之后，您可以：

* 将它放在 `<head>` 部分的开头，在其他解决方案标签之前显示。
* 它必须在 AppMeasurement 以及其他 [!DNL Experience Cloud] 解决方案的代码之前执行。

在测试和验证后将此代码移入生产环境中。

## 第步：(可选)配置宽限期 {#section-7bbb2f72c26e4abeb8881e18366797a3}

如果这些使用案例适用于您的情况，请要求 [客户服务部门](https://helpx.adobe.com/marketing-cloud/contact-support.html) 设置临时 [宽限期](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)。宽限期可长达 180 天。您可以在必要时延长宽限期。

**部分实施**

如果您的某些页面使用 ID 服务而某些页面没有使用，并且它们全部报告到同一个 [!DNL Analytics] 报表包中，那么就需要设置宽限期。这对于一个跨域报告的全局报表包来说，设置宽限期是很常见的。

当报告到同一报表包中的所有网页都部署了 ID 服务后，就可以中止宽限期。

**s_vi Cookie 要求**

如果在迁移到 ID 服务后，您要求新访客具有 s_vi Cookie，则需要设置宽限期。当您的实施需要读取 s_vi Cookie 并将其存储在变量中时，设置宽限期是很常见的。

在您的实施可以捕获 MID 而不是读取 s_vi Cookie 时，就可以中止宽限期。

请参阅 [Cookie 和 Experience Cloud ID 服务](../mcvid-introduction/mcvid-cookies.md).

如果您将来自点击流数据馈送和使用 `visid_high` 及 `visid_low` 列的流程中的数据发送至内部系统，则需要设置宽限期。

数据摄取流程可使用和 `post_visid_high``post_visid_low` 列后停止宽限期。

请参阅[点击流数据列引用](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html)。

**点击流数据获取**

## 步骤8：测试和部署ID服务代码 {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

您可以按如下方式进行测试和部署。

**测试和验证**

要测试 ID 服务的实施状况，请检查以下环节：

* 在托管页面的域中查找 [AMCV Cookie](../mcvid-introduction/mcvid-cookies.md)。
* 使用 [!DNL Analytics]Adobe 调试器工具[在 ](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) 图像请求中查找 MID 值。

请参阅 [测试和验证Experience Cloud ID服务](../mcvid-implementation-guides/mcvid-test-verify.md)。

**部署代码**

部署通过了测试的代码。

如果您在 [步骤 7](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) 中启用了宽限期：

* 请确保 [!DNL Analytics] ID (AID) 和 MID 都在图像请求中。
* 当您符合中止宽限期的条件时，请记住禁用宽限期。
