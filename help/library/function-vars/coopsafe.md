---
description: 这是一个可选的布尔型配置，用于确定 ID 服务是否会将数据发送到 Adobe Experience Cloud 设备协作。
keywords: ID Service
seo-description: 这是一个可选的布尔型配置，用于确定 ID 服务是否会将数据发送到 Adobe Experience Cloud 设备协作。
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 100%

---


# isCoopSafe{#iscoopsafe}

这是一个可选的布尔型配置，用于确定 ID 服务是否会将数据发送到 Adobe Experience Cloud 设备协作。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> 要求 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> 用例 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> 事件调用 POST 参数 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> 实例化后 API </a> </li> 
</ul>

## 要求 {#section-4883eda6beb8437182bcc82bb58fae41}

要使用 `isCoopSafe`，您必须满足以下条件：

* 使用 ID 服务代码版本 2.4 或更高版本。
* 参与 [Experience Cloud 设备协作](https://docs.adobe.com/content/help/zh-Hans/device-co-op/using/about/overview.html)。潜在的协作成员也应查阅此文档，以确定 `isCoopSafe` 是否可以解决可能与如何使用数据来创建设备图有关的问题。

* 与您的 [!DNL Adobe] 顾问合作，在您的设备协作帐户中设置一个白名单或黑名单标记。不存在启用这些标记的自助途径。

## 用例 {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` 可帮助解决以下 2 个与设备协作的当前成员或潜在成员进行的收集数据有关的用例。这两个用例与如何将网站访客数据传递到设备协作以帮助构建设备图有关。下表描述了 `isCoopSafe` 如何在这两个用例中使用，以阻止数据发送至设备图或将数据发送至设备图。

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已通过身份验证的访客</b> </p> </td> 
   <td colname="col2"> <p>将 <span class="codeph">isCoopSafe</span> 添加到您的 ID 服务代码，以控制设备协作如何使用经过身份验证的访客（已接受或未接受使用条款协议）的数据来构建设备图。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第三方网站上的 DIL</b> </p> </td> 
   <td colname="col2"> <p>将 <span class="codeph">isCoopSafe</span> 添加到您的 ID 服务代码以供在第三方网站上使用，在这些网站中： </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">无法确保已通过身份验证的访客是否接受了使用条款协议。 </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">需要控制设备协作如何使用该数据来构建设备图。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 语法和代码示例 {#section-952f56724a2b4d349340e26fbaf33ddd}

**语法：**`isCoopSafe: true | false`

布尔选项可确定设备协作是否可以使用客户数据。

* `isCoopSafe: true`：通过 Mobile SDK 或网站收集的访客数据&#x200B;*可以*&#x200B;用来帮助构建设备图。

* `isCoopSafe: false`：通过 Mobile SDK 或网站收集的访客数据&#x200B;*不能*&#x200B;用来帮助构建设备图。

**代码示例**

在 ID 服务代码实例化时进行此设置：

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## 事件调用 POST 参数 {#section-fcd441933506493faefaa6b51f194a17}

根据您设置的标记（`true` 或 `false`），ID 服务会将 `isCoopSafe` 转换为以下 POST 参数，并在事件调用中将它们发送至 [!DNL Adobe]：

* `d_coop_safe=1`
* `d_coop_unsafe=1`

这两个 POST 参数告知 [!DNL Experience Cloud] 设备协作是否可以在设备图中包含用户数据。下表定义了 `isCoopSafe` 布尔标记与在事件调用中传入的 POST 参数之间的关系。如果您没有使用 `isCoopSafe`，则无法在事件调用中传递这两个参数。

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 配置状态 </th> 
   <th colname="col2" class="entry"> POST 参数 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>设备协作可以使用访客数据来帮助构建设备图。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>设备协作不能使用访客数据来帮助构建设备图。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 实例化后 API {#section-9281c39c8b6249d7864100b5cbca7dc6}

这些 API 允许您覆盖 `isCoopSafe` 状态。这些 API 是必需的，因为它们允许您在网站或页面不刷新的单页应用程序中更改访客的实例化后/登录后状态。例如，如果用户在您的网站或应用程序中进行身份验证，并且稍后接受允许设备协作使用其数据的使用条款策略，则您需要调用这些 API。

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>在所有后续事件调用中设置 POST 参数 <span class="codeph">d_coop_safe=1</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>在所有后续事件调用中设置 POST 参数 <span class="codeph">d_coop_unsafe=1</span>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

