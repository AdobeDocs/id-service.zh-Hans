---
description: 2016年Experience Platform Identity Service的发布、更新或更改。
keywords: ID 服务
seo-description: 2016年Experience Platform Identity Service的发布、更新或更改。
seo-title: 2016 版发行说明
title: 2016 版发行说明
uuid: 7a5a314a-3ff8-4561-9c64-6c10d2223887
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# 2016 发行说明 {#release-notes}

2016年Experience Platform Identity Service的发布、更新或更改。

您也可以在 [Experience Cloud 发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)中找到这些更改。关于早期公告，请参阅[以前的发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html)。[!DNL Experience Cloud]

## 版本 1.10 {#section-7d719b3213344a46858835042e0214ed}

2016 年 11 月

>[!IMPORTANT]
>
>* 版本 1.10 需要使用 [!DNL AppMeasurement] 1.8.0。
>* 使用Experience Platform Identity Service Library2.0.0+，默认情况下，Adobe Media Optimizer将开始同步ID。请参阅[了解 ID 同步和匹配率](/help/introduction/match-rates.md)


**修复和改进功能**

* 添加了有关如何在服务器端环境中实施 ID 服务的说明。
* 添加了 `Visitor.overwriteCrossDomainMCIDAndAID` 布尔函数，此函数允许覆盖您所拥有的其他域中的 Experience Cloud ID 和 Analytics ID。请参阅[覆盖访客 ID](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde)。

* 添加了 `TS = UTC` =  时间戳 作为 `visitor.appendVisitorIDsTo` 函数的属性。ID 服务使用该时间戳按 5 分钟的时间间隔来确定是否应在重定向 URL 中使用 ID。请参阅 [附加访客 ID 函数](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* 添加了返回区域 ID 的新函数 `Visitor.getLocationHint,`。请参阅[获取区域 ID（位置提示）](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。

* 添加了 `idSyncByURL` 和 `idSyncByDataSource`，这两个函数允许您在“目标发布 iFrame” 中手动实施 ID 同步。请参阅[通过 URL 或数据源进行 ID 同步](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48)。

* 修复了当 `disableThirdPartyCalls:true` 时，阻止 AppMeasurement 跟踪调用的错误。
* 修复了阻止 ID 服务跨不同域传递 Experience Cloud ID (MID) 的错误。

## 版本 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

2016 年 10 月

**修复和改进功能**

* 修复了将 Audience Manager 独特用户 ID (AAMUUID) 作为 Experience Cloud ID 传递到 ID 服务的错误。
* 如果 AMCV Cookie 的生存时间 (TTL) 到期，则只要此 Cookie 包含 Experience Cloud ID，ID 服务便仍会将该信息返回到服务器。执行此调用之后，ID 服务发起异步调用以更新 Cookie。这有助于提高性能，因为 ID 服务无需等待服务器响应。它可以使用现有的 AMCV Cookie 值，然后请求更新。
* ID 服务在页面上直接与 Adobe Media Optimizer 和其他内部 Adobe 域自动同步 Experience Cloud ID (MID)。已为所有现有帐户和新帐户启用自动同步。这有助于提高 Media Optimizer 的匹配率。适用于 VisitorAPI.js 版本 1.8 或更高版本。另请参阅[了解 ID 同步和匹配率](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)。

**新文档和修订的文档**

**新文档：**[从 AMCV Cookie 获取区域 ID 和用户 ID](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## 版本 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

2016 年 9 月

**修复和改进功能**

添加了 `disableThirdPartyCalls` 作为可选布尔标记，您可以在 `Visitor.getInstance` 函数中设置此标记。若 `disableThirdPartyCalls= true`，则 ID 服务将不会对其他域进行调用。默认情况下，`disableThirdPartyCalls= false`请参阅 [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b)。

## 版本 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

2016 年 8 月

**修复和改进功能**

* 添加了 `idSyncAttachIframeOnWindowLoad` 作为可选布尔标记，您可以在 `Visitor.getInstance` 函数中设置此标记。当 `idSyncAttachIframeOnWindowLoad= true` 时，ID 服务在窗口加载上加载 ID 同步 iFrame。默认情况下，ID 服务会尽快加载 iFrame。此标记*取代*了已弃用的 `idSyncAttachIframeASAP`。请参阅 [Visitor.getInstance 函数变量](../library/function-vars/function-vars.md)。

* 添加了支持跨域跟踪 [!DNL Experience Cloud] ID 以及本机应用程序和混合应用程序向 Web 转换的功能。请参阅[附加访客 ID 辅助函数](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)。

* 向 visitorAPI.js 代码中添加了一些函数，这些函数可确定 ID 服务是否已在客户端或服务器端生成访客的 [!DNL Experience Cloud] ID，或 ID 调用是否已超时。请参阅[超时跟踪函数](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23)和[跟踪客户端访客 ID 生成](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6)。

**新文档和修订的文档**

Revised: [Requirements for the Experience Platform Identity Service](../reference/requirements.md)

**已知问题**

在同一页面上使用 [!DNL Audience Manager] DIL 代码和 visitorAPI.js 代码的客户应将 DIL 变量设置为 `secureDataCollection= false`。请参阅 [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html)。

## 版本 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

2016 年 7 月

>[!IMPORTANT]
>
>[!DNL Experience Cloud] ID 服务版本 1.6.0 *需要* AppMeasurement for JavaScript 版本 1.6.2。如果您升级到 ID 服务版本 1.6.0，请确保您使用了正确的 AppMeasurement 代码版本。

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>跨域资源共享 (CORS) </p> </td> 
   <td colname="col2"> <p>CORS 允许浏览器从某个域而非当前域请求资源。Experience Platform Identity Service支持CORS标准以启用客户端、跨源资源请求。ID 服务会在不支持 CORS 的浏览器上还原为 JSONP 请求。 </p> <p>请参阅： </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Experience Platform Identity Service中的CORS支持 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**修复和改进功能**

* 向 `d_fieldgroup` 的 ID 同步调用添加了 `dpm.demdex.net` 参数。此新参数可用于内部故障排除和调试目的。

* 向 ID 服务 iFrame 添加了 title 属性。iFrame title 可帮助屏幕阅读器向与在线内容交互时寻求帮助的用户提供页面信息。iFrame title 属性设置为 `Adobe ID Syncing iFrame`。
* 添加了 `idSyncAttachIframeASAP: true` 作为可选标记，您可以在 `Visitor.getInstance` 函数中设置此标记。设置为 `true` 时，ID 服务会尽可能快地加载 ID 同步 iFrame。此更改旨在帮助提高 ID 同步匹配率。默认情况下，ID 服务在加载窗口时加载 iFrame。请参阅 [Visitor.getInstance 函数变量](../library/function-vars/function-vars.md)。

* 修复了一个回调函数导致 AppMeasurement 陷入无限循环的错误。
* 已将 `loadTimeout` 的默认间隔值从 500 毫秒更改为 30,000 毫秒。请参阅 [Visitor.getInstance 函数变量](../library/function-vars/function-vars.md)。

**新文档和修订的文档**

**新建**

* [实施Experience Platform Identity Service for Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [为Analytics、Audience Manager和Target实施Experience Platform Identity Service](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**已修订**

* [Experience Platform Identity Service的要求](../reference/requirements.md)
* [测试和验证体验平台标识服务](../implementation-guides/test-verify.md)

## 版本 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

2016 年 6 月

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>对 <span class="codeph">iframe.sandbox</span> 属性的更改 </p> </td> 
   <td colname="col2"> <p>iFrame 现在已设置为 <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span>。 </p> <p>仅允许使用这 2 个令牌可帮助提高安全性，还可为 ID 服务提供 ID 同步所需的基本功能。 </p> <p>Internet Explorer 版本 9 或更早版本中不支持 sandbox 属性。有关详细信息，请参阅此 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame 文档</a>中的“属性”部分。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud ID (MID) 编码 </p> </td> 
   <td colname="col2"> <p>ID 服务会对从服务器返回的 MID 值进行编码，或者当 MID 值由 <span class="codeph">visitor.setMarketingCloudVisitorID()</span> 函数设置时，也会进行编码。有关 MID 的更多信息，请参阅 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 和 Experience Cloud ID</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**修复**

当不存在旧版 Analytics 访客 ID 时，访客 API 不再强制通过 Audience Manager 执行额外的重新同步调用。

## 版本 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

2016 年 5 月

**文档更新**

* [Android 和 iOS 的 SDK 要求](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench和Experience Platform Identity Service](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [测试和验证体验平台标识服务](../implementation-guides/test-verify.md)

## 版本 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

2016 年 4 月

**文档更新**

[为Target实施Experience Platform Identity Service](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## 版本 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

2016 年 3 月

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>选择退出支持 </p> </td> 
   <td colname="col2"> <p><span class="keyword">Experience Cloud</span> ID 服务支持访客的选择退出请求。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> 更改 ID 同步时间间隔 </p> </td> 
   <td colname="col2"> <p>现在，每当调用数据收集服务器时，<span class="keyword">Experience Cloud ID</span> 服务都会执行 ID 同步调用。以前，ID 服务只在首次调用中提出一次请求来获取 <span class="keyword">Experience Cloud</span> ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**文档更新**

* [实施Experience Platform Identity Service for Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) ：描述如何设置ID服务的新过程 [!DNL Analytics]。

* [体验平台标识服务迁移决策点](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) ：修改文本以实现清晰性。使用单个域意味着当您不再希望管理它时，可以从使用 CNAME 的数据收集中迁移出来然而，如果您的 CNAME 可以正常使用，则无需进行更改。

## 版本 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2016 年 1 月

**文档更新**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主题 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> 客户 ID 和身份验证状态 </a> </p> </td> 
   <td colname="col2"> <p>修订文本。客户 ID 只能作为一个未编码的值进行传递。编码 ID 后将创建双重编码的标识符。 </p> </td> 
  </tr> 
 </tbody> 
</table>

