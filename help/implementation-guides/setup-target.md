---
description: 这些说明适用于要使用 Experience Cloud 身份标识服务但不使用数据收集标记的 Target 客户。 但是，我们强烈建议您使用标记实施 ID 服务。 标记可简化实施工作流程，并自动确保代码放置和排序正确无误。
keywords: ID 服务
title: 实施适用于 Target 的 Experience Cloud 身份标识服务
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 422
ht-degree: 100%

---

# 实施适用于 Target 的 Experience Cloud 身份标识服务{#implement-the-experience-cloud-id-service-for-target}

这些说明适用于要使用 Experience Cloud 身份标识服务但不使用[数据收集标记](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)的 Target 客户。 但是，我们强烈建议您使用标记实施 ID 服务。 标记可简化实施工作流程，并自动确保代码放置和排序正确无误。

>[!IMPORTANT]
>
>* 请在开始之前[阅读相关要求](../reference/requirements.md)。
>* 请在生产环境中实施此代码之前，首先在开发环境中对它进行配置和测试。

## 步骤 1：获取 ID 服务代码 {#section-b32ba0548aa546a79dd38be59832a53e}

[!UICONTROL ID Service] 需要使用 `VisitorAPI.js` 代码库。 请联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)，以获取此代码。

## 步骤 2：将 Visitor.getInstance 函数添加到 ID 服务代码 {#section-287ef2958e9f43858fe9d630ae519e22}

**第 1 部分：复制下面的 Visitor.getInstance 函数**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**第 2 部分：将函数代码添加到 VisitorAPI.js 文件**

将 `Visitor.getInstance` 函数放置在位于文件末尾的代码块后面。 您编辑的文件应该类似于下面的样子：

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## 步骤 3：将您的 Experience Cloud 组织 ID 添加到 Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

在 `Visitor.getInstance` 函数中，将 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 替换为您的 [!DNL Experience Cloud] 组织 ID。 如果您不知道自己的组织 ID，可以在 [!DNL Experience Cloud] 管理页面上查找。 另请参阅[管理 - 核心服务](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=zh-Hans)。 您编辑的函数看起来类似于下面的示例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*请不要*&#x200B;更改组织 ID 中字符的大小写。 这个 ID 是区分大小写的，因此必须严格按照所提供的形式使用。

## 步骤 4：将访客 API 代码添加到页面 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

先将 `VisitorAPI.js` 文件部署到网站上的 `<head>` 标签中，然后再引用 `mbox.js` 文件。 [!DNL Experience Cloud] ID 服务必须在生成首个 [!DNL Target] 网络调用之前执行。 在测试和验证后将此代码移入生产环境中。

## 步骤 5：测试和部署 ID 服务代码 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以按如下方式进行测试和部署。

**测试和验证**

要测试 ID 服务实施，请执行以下操作：

* 检查托管页面的域中的 AMCV Cookie。
* 验证 `mboxMCGVID` 是否显示在您的 [!DNL Target] 请求中，以及它是否包含 [!DNL Experience Cloud] ID (MID)。

请参阅 [Cookie 和 Experience Cloud 身份标识服务](../introduction/cookies.md)，以了解有关 AMCV Cookie 和 MID 的信息。

**部署**

在代码通过测试后，部署代码。

