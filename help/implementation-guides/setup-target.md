---
description: 这些说明适用于那些想要使用访客ID服务而不使用标记的Target客户。 但是，我们强烈建议您使用标记来实施访客ID服务。 标记可简化实施工作流程，并自动确保代码放置和排序正确无误。
keywords: 访客 ID 服务
title: 实施适用于Target的Adobe访客ID服务
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# 实施适用于Target的Adobe访客ID服务{#implement-the-experience-cloud-id-service-for-target}

这些说明适用于那些想要使用访客ID服务而不使用[标记](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)的Target客户。 但是，我们强烈建议您使用标记来实施访客ID服务。 标记可简化实施工作流程，并自动确保代码放置和排序正确无误。

>[!IMPORTANT]
>
>* 请在开始之前[阅读相关要求](../reference/requirements.md)。
>* 请在生产环境中实施此代码之前，首先在开发环境中对它进行配置和测试。

## 步骤1：获取访客ID服务代码 {#section-b32ba0548aa546a79dd38be59832a53e}

访客ID服务需要`VisitorAPI.js`代码库。 请联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)，以获取此代码。

## 步骤2：将Visitor.getInstance函数添加到访客ID服务代码中 {#section-287ef2958e9f43858fe9d630ae519e22}

**第 1 部分：复制下面的 Visitor.getInstance 函数**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**第2部分：将函数代码添加到`VisitorAPI.js`文件**

将 `Visitor.getInstance` 函数放置在位于文件末尾的代码块后面。 您编辑的文件应该类似于下面的样子：

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## 步骤3：将您的IMS组织ID添加到Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

在`Visitor.getInstance`函数中，将`INSERT-IMS-ORG-ID-HERE`替换为您的IMS组织ID。 如果您不知道您的IMS组织ID，可以在CX企业管理页面上找到它。 另请参阅[管理 - 核心服务](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=zh-Hans)。 您编辑的函数看起来类似于下面的示例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*不要*&#x200B;更改IMS组织ID中字符的大小写。 这个 ID 是区分大小写的，因此必须严格按照所提供的形式使用。

## 步骤 4：将访客 API 代码添加到页面 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

先将 `VisitorAPI.js` 文件部署到网站上的 `<head>` 标签中，然后再引用 `mbox.js` 文件。 访客ID服务必须在生成首个Target网络调用之前执行。 在测试和验证后将此代码移入生产环境中。

## 步骤5：测试和部署访客ID服务代码 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以按如下方式进行测试和部署。

**测试和验证**

要测试访客ID服务实施，请执行以下操作：

* 检查托管页面的域中的 AMCV Cookie。
* 验证`mboxMCGVID`是否显示在您的Target请求中，以及它是否包含ECID。

有关AMCV Cookie和MID的信息，请参阅[Cookie和访客ID服务](../introduction/cookies.md)。

**部署**

在代码通过测试后，部署代码。

