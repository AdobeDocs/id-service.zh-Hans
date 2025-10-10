---
description: 此属性可设置要用于 ID 同步的数据源容器 ID。
keywords: ID 服务
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 94%

---

# idSyncContainerID{#idsynccontainerid}

此属性可设置要用于 ID 同步的数据源容器 ID。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 语法和代码示例 </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">什么是容器？我何时会使用它？</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> 使用 DIL 和 VisitorAPI.js 时设置容器 ID </a> </li> 
</ul>

## 语法和代码示例 {#section-b0c50732b1c84bed8616e82e8e83d58c}

**语法：**`idSyncContainerID: *`容器 ID 值`*`

**代码示例:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## 什么是容器？我何时会使用它？ {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**容器**

容器是由 [!DNL Audience Manager] 创建的对象。虽然它们无法从外部访问，但这些容器会列出满足以下条件的所有数据源：

* 可供您用于 ID 同步，但未使用。
* 正用于 ID 同步。

即使您不是 [!DNL Audience Manager] 客户，如果您正在与域中的不同页面上的不同数据源交换 ID，则您的帐户将拥有这些容器。这是因为 [!DNL Audience Manager] 提供了可启用 ID 同步的技术和后端功能。

**用例**

根据您的情形，您可能需要也可能不需要将此配置添加到您的 ID 服务代码。

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 条件 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>不需要</b> </p> </td> 
   <td colname="col2"> <p>在以下情况下，您不需要使用此配置： </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">您将 ID 服务与任何 <span class="keyword">Experience Cloud</span> 解决方案结合使用，且不执行与其他数据源的 ID 同步操作。在这种情况下，您的帐户有一个 ID 为 0 的默认容器，并且无需执行任何操作。 </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">您的所有数据源都在一个容器中。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>需要</b> </p> </td> 
   <td colname="col2"> <p>当满足以下所有条件时，您需要使用此配置： </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">您不使用 <span class="keyword">Audience Manager</span>。 </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">您需要将 ID 与由容器整理的其他数据源同步。 </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">您需要将 ID 与您域中不同页面上不同容器中的数据源同步。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 使用DIL和VisitorAPI.js时设置容器ID {#section-f283cb69c8de4348b5316cc4e02a3e9e}

如果您在同一页面上部署了 [!UICONTROL DIL ]*和* VisitorAPI.js，则：

* 对于 ID 同步，访客 ID 服务代码会优先于 DIL。
* 仅在 ID 服务代码中设置 `idSyncContainerID` 配置。
