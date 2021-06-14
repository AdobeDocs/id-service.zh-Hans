---
description: 选择加入 API 库和配置设置参考。
title: 选择加入参考
exl-id: aa61aed7-695b-47e4-a922-9841e00aa09d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '886'
ht-degree: 100%

---

# 选择加入参考{#opt-in-reference}

选择加入 API 库和配置设置参考。

同意设置会作为类别提供给选择加入函数：

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## 选择加入配置参数 {#section-d66018342baf401389f248bb381becbf}

本节讨论如何使用 API 来配置选择加入。大部分配置和实施都可以使用 Experience Platform Launch 扩展来完成。

选择加入配置在访客 JavaScript `getInstance()` 函数中提供，该函数可实例化全局 `adobe` 对象。下面列出了与选择加入服务相关的访客 JS 配置。

**`doesOptInApply (boolean or function that evaluates to a boolean)`**：

如果为 false，则指示访客不需要选择加入。无论是否选择加入类别，Experience Cloud 中的结果都会创建 Cookie。此配置会整体启用或禁用选择加入。

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

定义在访客尚未设置首选项时批准或拒绝的类别，称为组织默认值。

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

访客明确设置了首选项。此配置中的权限将覆盖组织默认值（`previousPermissions` 覆盖 `preOptInApprovals`）。

**`isOptInStorageEnabled (boolean)`**

启用选择加入功能以在第一方 Cookie 中存储权限（在当前客户的域中）

（可选）**`optInCookiesDomain (string)`**

用于选择加入 Cookie 的第一方域或子域（如果 `isOptInStorageEnabled` 为 true）

（可选）**`optInStorageExpiry (integer)`**

用于覆盖默认过期时间（13 个月）的秒数

## Consent 参数的更改 {#section-c3d85403ff0d4394bd775c39f3d001fc}

在访问您网站期间的任意时刻，访客可以首次设置偏好设置，也可以使用您的 CMP 更改其偏好设置。使用初始设置初始化访客 JS 后，可以使用以下函数更改访客的权限：

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

可批准或将访客选择加入到列表中所有类别的函数。有关 shouldWaitForComplete 参数的更多信息，请参阅[选择加入工作流程](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5)。

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

可拒绝或从所有指定类别中选择退出访客的函数。

**`adobe.optIn.approveAll()`**：

如果您请求允许网站创建 Cookie，以便访客完全同意或拒绝授予网站创建 Cookie 的权限，则请根据访客的回答，对应使用 `approveAll()` 或 `denyAll()`。

**`adobe.optIn.denyAll()`**：

如果您请求允许网站创建 Cookie，以便访客完全同意或拒绝授予网站创建 Cookie 的权限，则请根据访客的回答，对应使用 `approveAll()` 或 `denyAll()`。

## 选择加入工作流程参数 {#section-2c5adfa5459c4e72b96d2693123a53c2}

选择加入支持可以通过多个请求周期收集权限的工作流程，例如一次提供一个首选项。如果使用以下函数并将 *设置为* true`shouldWaitForComplete`，您的解决方案便能够收集一个解决方案或总类别子集的同意情况，然后收集下一个解决方案或类别子集的同意情况。从第一次调用开始，`adobe.optIn.status` 属性将处于 pending 状态，直到在工作流程结束时调用 `adobe.optIn.complete()` 为止。调用后，状态将设置为 *Complete*。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

可批准或将访客选择加入到列表中所有类别的函数。

`adobe.optIn.deny(categories, shouldWaitForComplete)`

可拒绝或从所有指定类别中选择退出访客的函数。

`adobe.optIn.complete()`

此函数将正在进行的 approve() 和 deny() 调用聚合到一个请求中，以设置访客的首选项。当订阅下面的选择加入更改时（请参阅 `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`），只有在调用此函数时才会触发回调。

## 访客选择加入权限参数 {#section-7fe57279b5b44b4f8fe47e336df60155}

使用以下任一权限函数可随时收集访客的选择加入权限：

`adobe.optIn.permissions`

以类别形式列出访客已同意或拒绝的所有 Experience Cloud 解决方案的对象。

`adobe.optIn.isApproved(categories)`

如果所有类别都已被批准，则此函数将返回 true。

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

以异步方式检索权限列表。权限批准/拒绝流程完成后，使用权限列表调用回调。若将 *设置为值* true`shouldAutoSubscribe`，则可为将来的任何选择加入更改注册回调。以下是 `adobe.OptIn` 的属性：

**`permissions`**

以类别形式列出访客已同意或拒绝的所有 Experience Cloud 解决方案的对象。示例：`{ aa: true, ecid: false, aam: true... }`

**`status`**

* 待处理
* 已更改
* 完成

**`doesOptInApply`**

True 或 False，表示您在初始化时提供的配置

**`isPending`**

True 或 False，具体视状态值而定。对于尚未明确接受或拒绝权限的访客，选择加入会为此属性返回 true

**`isComplete`**

True 或 False，具体视状态值而定。当工作流程式同意已开始但未完成时，选择加入可能会为此属性返回 false。

## 选择加入对象的方法 {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**：要批准的一个或多个类别。例如：`adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**：（可选）布尔参数，默认为 false。如果传递 true，则在调用 `adobe.optIn.complete()` 之前，选择加入将不会完成批准流程。此流程类似于工作流程。

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* 传递 1 个或多个类别以检查它们是否获得批准。
* 如果未传入任何类别，则会检查所有可用的类别。

**`isApproved(categories)`**

检查客户是否批准了一个或多个类别。

**`isPreApproved(categories)`**

检查客户是否预先批准了一个或多个类别。（它们是否在 `preOptInApprovals` 配置中传递）。

**`fetchPermissions(callback, shouldAutoSubscribe)`**

同步 API 以检索权限列表。权限批准/拒绝流程完成后，使用权限列表调用回调。**`shouldAutoSubscribe`:** 一个助手实用程序，将自动订阅所有未来事件的回调。这意味着，每当批准或拒绝触发选择加入时，系统都会调用回调。这样，您始终都能了解最新动态，而不用亲自订阅这些事件。

**示例**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>仅在传递 `shouldWaitForComplete` 参数以批准或拒绝时使用。此 API 可完成批准流程。示例：`adobe.optIn.complete()`。

**`approveAll()`:**

批准所有现有类别。

**`denyAll()`**

拒绝所有现有类别。

## 选择加入对象的事件 {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

complete 事件在批准流程完成时触发。如果在没有传递 `shouldWaitForComplete` 的情况下调用 approve/deny，或者调用 `approveAll`/`denyAll`，则会触发此事件。或者，如果传递了 `shouldWaitForComplete`，则在调用 `complete` 时会触发此事件。

**示例**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
