---
description: 将选择服务作为Experience Cloud解决方案所使用的单一参考点(称为“参与”中的类别)来确定是否在访客设备上创建cookies。
seo-description: 将选择服务作为Experience Cloud解决方案所使用的单一参考点(称为“参与”中的类别)来确定是否在访客设备上创建cookies。
seo-title: 设置参与服务
title: 设置参与服务
uuid: f1c27139-cef2-4122-af12-c839 cfc82 e6 e
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# 设置参与服务{#setting-up-opt-in-service}

将选择服务作为Experience Cloud解决方案所使用的单一参考点(称为“参与”中的类别)来确定是否在访客设备上创建cookies。

选择服务是与 [Experience Cloud ID(ECID)绑定的JavaScript库](https://marketing.adobe.com/resources/help/en_US/mcvid/) ，并作为对象存在于全局 `adobe` 对象中的访客JS `adobe.optIn` 中。安装的Opt-in服务允许您指定一个访客是否可以同时加入Adobe解决方案，或以序列形式显示解决方案以获得每个解决方案的权限。参与服务同意管理功能允许您使用各种配置实现特定隐私要求。

通过选择参与服务，您可以指定一个访客是否可以同时选择加入Adobe解决方案，或者为每个解决方案提供按顺序提供解决方案。批准流程完成并由客户记录后，所有 Adobe 解决方案均可以检索 CMP 访客的批准信息，以响应相关的同意调用。

## 先决条件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID 版本 4.0。

   [下载](https://github.com/Adobe-Marketing-Cloud/id-service/releases) ECID 的最新版本。

1. 支持的库：

   * ECID 4.0 或更高版本
   * AppMeasurement 2.11 或更高版本
   * DIL 9.0
   * AT.js 版本 1.7.0
   * AT.js Launch 扩展版本 9.0
   * 对于 Analytics，App Measurement 2.11 和扩展版本 1.6
   * 对于 Target，扩展版本 0.9.1

1. 熟悉您将与选择加入功能一起使用的同意管理框架，并了解所有其他先决条件。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 贵公司的隐私要求具体取决于您选择以何种方式遵守 GDPR 的规定。了解贵公司隐私团队允许在同意前使用哪些库。

如果使用的是 [Adobe Launch](https://docs.adobelaunch.com/)，请使用[选择扩展以](../../implementation-guides/opt-in-service/launch.md) 配置参与服务。

## 选择类别 {#section-9ab0492ab4414f0ca16dc08d3a905f47}

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

参与服务允许您根据网站上使用的每个Adobe解决方案设置访客的权限首选项。它包括一个用于按已批准的类别保存访客设置的库，并且支持顺序化的工作流程，其中批准流程每次只接收每个类别的“确认”或“拒绝”首选项。您可以将解决方案/类别设置为作为整体或作为单个解决方案选择加入。所有Adobe解决方案的客户端库取决于参与服务，除非已获得许可，否则不会生成cookies。选择加入支持为当前访客提供和更新同意设置的各种方法。本节提供了设置参与服务首选项的示例。有关函数和参数的完整列表，请参阅 [选择API参考](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) 。

选择服务配置在访客JS `getInstance()` 函数中提供，该函数实例化全局 `adobe` 对象。以下列出了用于选择加入服务的访问者JS [配置设置](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) 。

**初始化全局`Visitor`对象的选择加入配置示例**

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

在访客访问您的网站期间，可以随时对首选项进行首次设置或使用您的 CMP 更改其首选项。使用初始设置初始化访客 JS 后，可以对访客的权限进行更改。有关 [管理同意功能列表，请参阅同意](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) 更改。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## 选择工作流程 {#section-70cd243dec834c8ea096488640ae20a5}

选择服务支持一种工作流，该工作流可在多个请求周期内收集权限，同时一次提供一个请求。如果使用以下函数并将 ** 设置为 `shouldWaitForComplete`true，您的解决方案便能够收集一个解决方案或总类别子集的同意情况，然后收集下一个解决方案或类别子集的同意情况。从第一次调用开始， `adobe.optIn.status` 该属性将 *一直等待* ，直到 `adobe.optIn.complete()` 在流结束时调用。调用后，状态将设置为 *complete*。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

请参阅 [工作流配置设置](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)。

## 检查访客的选择加入权限 {#section-f136a9024e054d84881e6667fb7c94eb}

当访客对其权限进行更改时，您需要深入了解生成的权限，以便与在选择服务中所做的更改同步您的同意商店。使用[权限函数](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)检查访客的首选项，例如：

**fetchPermissions sample**

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

请参阅[API 文档](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)，以了解有关这些内容以及本文档中提到的任何函数、属性或配置的更多详细信息。

## 存储访客首选项 {#section-ef2884ae67e34879bf7c7c3372706c9f}

选择服务提供了一个选项，用于存储适用于开发环境的同意首选项或使用CRM不可行的环境。将配置属性指定 `isOptInStorageEnabled` 为 *真正* 触发器，可在您的域中的访客系统上创建一个cookie。

`adobe.optIn` 对象是无状态的，并且不提供存储机制。如果其允许存储自定义数据，则可以在现有的“同意管理平台 (CMP)”中管理 Adobe 同意设置。或者，您可以将访客首选项存储在访客浏览器的 Cookie 中。您有两个选项可用于向用户提供选择参与服务的首选项：

* 如果您的同意持久性解决方案是一个CMP或访客浏览器上的cookie，则允许及时检索访客偏好，您可以在访客初始化过程中向参与服务提供这些信息。
* 但是，如果检索可能是冗长的进程，或者作为异步进程的最佳服务，则可以在成功加载这些设置后使用服务 `approve()` 的函数提供这些设置。

