---
description: 这些说明适用于希望使用Experience Cloud ID服务且不使用Dynamic Tag Management(DTM)的Target客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。
keywords: ID 服务
seo-description: 这些说明适用于希望使用Experience Cloud ID服务且不使用Dynamic Tag Management(DTM)的Target客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。
seo-title: 实施适用于 Target 的 Experience Cloud ID 服务
title: 实施适用于 Target 的 Experience Cloud ID 服务
uuid: cb3581fa-4c4b-43aa-bb8 e-8db85 a6 a1 ef2
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 实施适用于 Target 的 Experience Cloud ID 服务{#implement-the-experience-cloud-id-service-for-target}

这些说明适用于希望使用Experience Cloud ID服务且不使用Dynamic Tag Management(DTM)的Target客户。但是，我们强烈建议您使用 DTM 来实施此 ID 服务。DTM 可简化实施工作流程，并自动确保代码放置和排序的正确性。

>[!IMPORTANT]
>
>* [请在开始之前阅读相关要求。](../reference/requirements.md)
>* 请在生产环境中实施此代码之前，首先在开发环境中对它进行配置和测试。
>



## Step 1: Get the ID Service code {#section-b32ba0548aa546a79dd38be59832a53e}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. 联系[客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)，以获取此代码。

## Step 2: Add the Visitor.getInstance function to the ID Service code {#section-287ef2958e9f43858fe9d630ae519e22}

**第 1 部分：复制下面的 Visitor.getInstance 函数**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. 如果您不知道自己的组织 ID，可以在 [!DNL Experience Cloud] 管理页面上查找。另请参阅[管理 - 核心服务](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)。您编辑的函数看起来类似于下面的示例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*请勿* 更改单位ID中字符的大小写。这个 ID 是区分大小写的，因此必须严格按照所提供的形式使用。

## Step 4: Add Visitor API code to the page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Deploy the `VisitorAPI.js` file to your site in the `<head>` tags before the reference to the `mbox.js` file. [!DNL Experience Cloud] ID服务必须在生成第一个 [!DNL Target] 网络调用之前执行。在测试和验证后将此代码移入生产环境中。

## Step 5: Test and deploy ID Service code {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以按如下方式进行测试和部署。

**测试和验证**

要测试您的 ID 服务实施，请执行以下操作：

* 在托管页面的域中检查 AMCV Cookie。
* Verify `mboxMCGVID` appears in your [!DNL Target] request and that it contains the [!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**部署**

部署通过了测试的代码。
