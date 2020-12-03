---
description: 将选择加入服务作为 Experience Cloud 解决方案（在选择加入中称为类别）使用单个引用点实施，以确定是否在访客的设备上创建 Cookie。
seo-description: 将选择加入服务作为 Experience Cloud 解决方案（在选择加入中称为类别）使用单个引用点实施，以确定是否在访客的设备上创建 Cookie。
seo-title: 设置选择加入服务
title: 设置选择加入服务
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 78%

---


# 设置选择加入服务{#setting-up-opt-in-service}

将选择加入服务作为 Experience Cloud 解决方案（在选择加入中称为类别）使用单个引用点实施，以确定是否在访客的设备上创建 Cookie。

选择加入服务是一个与 Experience Cloud ID (ECID) 捆绑在一起的 JavaScript 库，并且在全局 `adobe` 对象的访客 JS 中作为 `adobe.optIn` 对象存在。您可以通过已安装的选择加入服务，指定让访客立即选择加入 Adobe 解决方案，还是按照顺序显示解决方案，让访客逐个授予权限。借助选择加入服务同意管理功能，您可以根据特定的隐私要求使用各种配置来进行实施。

您可以通过选择加入服务，指定让访客立即选择加入 Adobe 解决方案，还是按照顺序显示解决方案，让访客逐个授予权限。批准流程完成并由客户记录后，所有 Adobe 解决方案均可以检索 CMP 访客的批准信息，以响应相关的同意调用。

## 先决条件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID 版本 4.0。

   [下载](https://github.com/Adobe-Marketing-Cloud/id-service/releases) 最新ECID版本。

1. 支持库：

   * ECID 4.0或更高版本
   * AppMeasurement 2.11或更高版本
   * DIL 9.0
   * AT.js版本1.7.0
   * AT.js启动扩展9.0版
   * 对于Analytics,App Measurement 2.11（扩展为1.6）
   * 对于目标，扩展0.9.1

1. 精通同意管理框架（随选择加入而使用）并了解任何其他先决条件。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 您的公司的隐私要求将特定于您选择如何遵守GDPR。 了解您的公司隐私团队在事先同意状态下可以使用的库。

If using [Adobe Launch](https://docs.adobelaunch.com/), take advantage of the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md) to configure Opt-in service.

## 选择加入类别 {#section-9ab0492ab4414f0ca16dc08d3a905f47}

访客的选择加入首选项与 Adobe Experience Cloud 解决方案相关，其中每个解决方案都表示为一个类别。类别由 `adobe.OptInCategories` 对象提供，例如，其中 ECID 组件称为 `adobe.OptInCategories`. `ECID`。以下是 `adobe.OptInCategories` 的定义：

选择加入设置按类别都进行维护，其中每个 Experience Cloud 解决方案都由一个类别表示：

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

选择加入服务允许您根据网站上使用的每个 Adobe 解决方案来设置访客的权限首选项。它包括一个用于按已批准的类别保存访客设置的库，并且支持顺序化的工作流程，其中批准流程每次只接收每个类别的“确认”或“拒绝”首选项。您可以将解决方案/类别设置为作为整体或作为单个解决方案选择加入。所有 Adobe 解决方案客户端库都依赖于选择加入服务，除非该解决方案已被授予权限，否则不会生成 Cookie。选择加入支持为当前访客提供和更新同意设置的各种方法。本节提供了设置选择加入服务首选项的示例。请参阅[选择加入 API 引用](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)，以获取函数和参数的完整列表。

选择加入服务配置在访客 JS `getInstance()` 函数中提供，该函数可实例化全局 `adobe` 对象。下面列出了选择加入服务的访客 JS [配置设置](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf)。

**初始化全局 `Visitor` 对象的选择加入配置示例**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**处理对同意的更改**

在访客在您网站上的体验中，他们可随时首次设置首选项，也可使用您的CMP更改其首选项。 使用初始设置初始化访客JS后，访客的权限即可更改。 请参阅[对同意的更改](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc)，以获取管理同意函数的列表。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## 选择加入工作流程 {#section-70cd243dec834c8ea096488640ae20a5}

选择加入服务支持可以通过多个请求周期收集权限的工作流程，并且一次提供一个首选项。如果使用以下函数并将 ** 设置为 `shouldWaitForComplete`true，您的解决方案便能够收集一个解决方案或总类别子集的同意情况，然后收集下一个解决方案或类别子集的同意情况。从第一次调用开始，`adobe.optIn.status` 属性将处于 *pending* 状态，直到在工作流程结束时调用 `adobe.optIn.complete()` 为止。调用后，状态将设置为 *complete*。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

请参阅[工作流程配置设置](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)。

## 检查访客的选择加入权限 {#section-f136a9024e054d84881e6667fb7c94eb}

当访客对其权限进行更改时，您需要洞悉由此产生的权限，以便将您的同意存储与选择加入服务中所做的更改同步。Inspect访客使用权限 [功能](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)，例如：

**fetchPermissions示例**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

See [API documentation](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) for more details on these and any functions, properties, or configurations mentioned in this document.

## 存储访客首选项 {#section-ef2884ae67e34879bf7c7c3372706c9f}

选择加入服务提供了一个选项，可用于存储适合开发人员环境或无法使用 CRM 的环境的同意首选项。将配置属性 `isOptInStorageEnabled` 指定为 *true* 会触发选择加入服务，以在域中访客系统上创建 Cookie。

`adobe.optIn` 对象是无状态的，并且不提供存储机制。相反，如果允许存储自定义Adobe，您应管理现有同意管理平台(CMP)中的同意设置。 或者，您可以在访客浏览器的Cookie中存储访客首选项。 您有两个选项可用于将用户首选项提供给选择加入服务：

* 无论您的同意持久性解决方案是 CMP 还是访客浏览器上的 Cookie，如果允许及时检索访客首选项，则可以在访客初始化期间将这些首选项提供给选择加入服务。
* 但是，如果检索是一个非常漫长的过程，或者最好作为异步流程进行，您可以在成功加载设置后，使用服务的 `approve()` 函数来提供这些设置。

