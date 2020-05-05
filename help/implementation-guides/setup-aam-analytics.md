---
description: 这些说明适用于那些想要使用 Experience Cloud Identity 服务而不使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客户。但是，我们强烈建议您使用DTM来实施ID服务。 DTM简化了实施工作流程，并自动确保正确的代码放置和排序。
keywords: ID Service
seo-description: 这些说明适用于那些想要使用 Experience Cloud Identity 服务而不使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客户。但是，我们强烈建议您使用DTM来实施ID服务。 DTM简化了实施工作流程，并自动确保正确的代码放置和排序。
seo-title: 实施适用于 Analytics 和 Audience Manager 的 Experience Cloud Identity 服务
title: 实施适用于 Analytics 和 Audience Manager 的 Experience Cloud Identity 服务
uuid: d46050ae-87de-46cc-911b-d6346c7fd511
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 实施适用于 Analytics 和 Audience Manager 的 Experience Cloud Identity 服务{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

这些说明适用于那些想要使用 Experience Cloud Identity 服务而不使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客户。但是，我们强烈建议您使用DTM来实施ID服务。 DTM简化了实施工作流程，并自动确保正确的代码放置和排序。

>[!IMPORTANT]
>
>* [请在开始之前阅读相关要求。](../reference/requirements.md)
>* 此过程需要AppMeasurement。 使用s_code的客户无法完成此过程。
>* 请在生产环境中实施此代码之前，首先在开发环境中对它进行配置和测试。
>



## 步骤 1：规划服务器端转发 {#section-880797cc992d4755b29cada7b831f1fc}

除了这里介绍的步骤以外，使用 [!DNL Analytics] 和 [!DNL Audience Manager] 的客户还应迁移到服务器端转发。Server-side forwarding lets you remove DIL (Audience Manager&#39;s data collection code) and replace it with the [Audience Management Module](https://docs.adobe.com/content/help/en/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html). See the [server-side forwarding documentation](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf.html) for more information.

迁移到服务器端转发需要规划和协调。 此过程涉及对您的站点代码进行外部更改以及Adobe设置您的帐户时必须执行的内部步骤。 事实上，这些迁移过程中的许多都需要并行进行并一起发布。 您的实施路径应遵循以下事件顺序：

1. 与您的 [!DNL Analytics] 和 [!DNL Audience Manager] 联系人一起计划您的 ID 服务和服务器端转发迁移。将选择跟踪服务器作为此计划的重要环节。

1. Complete the form on the [integrations and provisioning site](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) to get started.

1. 同时实施 ID 服务和 [!DNL Audience Management Module]。若要正常工作，必须为同一组页面同时发布 [!DNL Audience Management Module]（服务器端转发）和 ID 服务。

## 步骤 2：下载 ID 服务代码 {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

ID 服务 要求具备 `VisitorAPI.js` 代码库。要下载此代码库，请执行以下操作：

1. Go to **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]**.

1. 在“代码管理器”中，单击 **[!UICONTROL JavaScript（新版）]**&#x200B;或 **[!UICONTROL JavaScript（旧版）]**。此下载文件对代码库进行了压缩。

1. 解压缩代码文件，并打开 `VisitorAPI.js` 文件。

## 步骤 3：将 Visitor.getInstance 函数添加到 ID 服务代码中 {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* 先前版本的ID服务API将此函数放置在不同的位置，并需要不同的语法。 如果您是从版本1.4之前的 [版本迁移](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572)，请注意此处介绍的新位置和语法。
>* ALL CAPS中的代码是实际值的占位符。 将此文本替换为您的组织ID、跟踪服务器URL或其他命名值。
>



**第1部分： 复制下面的访客.getInstance函数**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**第2部分： 将函数代码添加到访客API.js文件**

将 `Visitor.getInstance` 函数放置在位于文件末尾的代码块后面。您编辑的文件应该类似于下面的样子：

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## 步骤 4：将您的 Experience Cloud 组织 ID 添加到 Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

在 `Visitor.getInstance` 函数中，将 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 替换为您的 Experience Cloud 组织 ID。如果您不知道您的组织ID，可以在Experience Cloud管理页面上找到它。 您编辑的函数看起来类似于下面的示例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*请不要*&#x200B;更改组织 ID 中字符的大小写。这个 ID 是区分大小写的，因此必须严格按照所提供的形式使用。

## 步骤 5：将您的跟踪服务器添加到 Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics使用跟踪服务器进行数据收集。

**第 1 部分：查找您的跟踪服务器 URL**

检查您的 `s_code.js` 或 `AppMeasurement.js` 文件，以查找跟踪服务器 URL。您将需要由以下变量指定的 URL：

* `s.trackingServer`
* `s.trackingServerSecure`

**第2部分： 设置跟踪服务器变量**

要确定要使用的跟踪服务器变量，请执行以下操作：

1. 在下面的决策矩阵中回答问题。 使用与答案对应的变量。
1. 将跟踪服务器占位符替换为跟踪服务器URL。
1. 从代码中删除未使用的跟踪服务器和Experience Cloud服务器变量。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>在使用时，请将 Experience Cloud 服务器 URL 与它们所对应的跟踪服务器 URL 相匹配，如下所示：

* Experience Cloud服务器URL =跟踪服务器URL
* Experience Cloud服务器安全URL =跟踪服务器安全URL

如果您不确定如何找到跟踪服务器，请参阅[常见问题解答](../faq-intro/faq.md)和[正确填充 trackingServer 和 trackingServerSecure 变量](https://helpx.adobe.com/cn/analytics/kb/determining-data-center.html#)。

## 步骤 6：更新您的 AppMeasurement.js 文件 {#section-5517e94a09bc44dfb492ebca14b43048}

This step requires [!UICONTROL AppMeasurement]. 如果您仍使用 s_code，则无法继续。

将如下所示的 `Visitor.getInstance` 函数添加到您的 `AppMeasurement.js` 文件中。将该函数放置在包含 `linkInternalFilters`、`charSet`、`trackDownloads` 等配置的部分中：

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>此时，您应当删除 [!DNL Audience Manager] DIL 代码，并将其替换为受众管理模块。请参 [阅实施服务器端转发](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf.html) ，以获取说明。

***（可选，但是推荐）*创建自定义 prop **

在 `AppMeasurement.js` 中设置自定义 prop 来测量范围。将此自定义 prop 添加到 `doPlugins` 文件的 `AppMeasurement.js` 函数中：

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 步骤 7：将访客 API 代码添加到页面中 {#section-c2bd096a3e484872a72967b6468d3673}

将 ` [!UICONTROL VisitorAPI.js]` 文件放置在每个页面的 `<head>` 标记之内。在将 `VisitorAPI.js` 文件放入页面之后，您可以：

* 将它放在 `<head>` 部分的开头处，使其显示在其他解决方案标记之前。
* 它必须在 AppMeasurement 以及其他 [!DNL Experience Cloud] 解决方案的代码之前执行。

## 步骤 8：（可选）配置宽限期 {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). 宽限期最长可为180天。 您可以根据需要续订宽限期。

**部分实施**

如果您有使用ID服务的某些页面和不使用ID服务的某些页面，并且这些页面都报告到同一Analytics报表包中，则需要宽限期。 如果您有一个跨域报告的全局报告套件，则这种情况很常见。

在将ID服务部署到报告到同一报表包的所有网页后，停止宽限期。

**s_vi Cookie要求**

如果您需要新访客在迁移到ID服务后具有s_vi cookie，则需要宽限期。 如果您的实现读取s_vi cookie并将其存储在变量中，则这是常见的。

在实施可捕获MID而不是读取s_vi cookie后，停止宽限期。

另请参阅 [Cookie 和 Experience Cloud Identity 服务](../introduction/cookies.md)。

**点击流数据集成**

如果您将来自点击流数据馈送和使用 `visid_high` 及 `visid_low` 列的流程中的数据发送至内部系统，则需要设置宽限期。

当您的数据获取流程可以使用 `post_visid_high` 和 `post_visid_low` 列之后，就可以中止宽限期。

另请参阅 [Clickstream Data Column Reference](https://docs.adobe.com/content/help/zh-Hans/analytics/export/analytics-data-feed/data-feed-overview.html)。

## 步骤 9：测试和部署 ID 服务代码 {#section-f857542bfc70496dbb9f318d6b3ae110}

您可以按如下方式进行测试和部署。

**测试和验证**

要测试 ID 服务的实施状况，请检查以下环节：

* [在托管页面的域中查找 AMCV Cookie](../introduction/cookies.md)。
* 使用Adobe调试器在Analytics图像请求中 [输入MID值](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html)。
* 另请参阅[测试和验证 Experience Cloud Identity 服务](../implementation-guides/test-verify.md)。

要验证服务器端转发，请参 [阅如何验证服务器端转发实施](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html)。

**部署**

通过测试后部署代码。

如果启用宽限期：

* 确保图像请求中包含Analytics ID(AID)和MID。
* 当您符合中止宽限期的条件时，请记住禁用宽限期。

