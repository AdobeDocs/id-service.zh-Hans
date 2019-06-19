---
description: 2018年Experience Platform Identity Service的发布、更新或更改。
keywords: ID 服务
seo-description: 2018年Experience Platform Identity Service的发布、更新或更改。
seo-title: 2018 发行说明
title: 2018 发行说明
uuid: 771b5b11-a8 e3-464c-b65 e-b1513584 ace
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 2018 版发行说明 {#release-notes}

2018年Experience Platform Identity Service的发布、更新或更改。

## 版本 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 项目描述 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>增强了 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在内部安全扫描期间，发现在使用 DTM 库时，用于会话管理的 Cookie 无法指定正确的属性。这可能会导致无意中共享 Cookie 信息。为解决此问题，我们引入了一个配置，它允许客户将 AMCV Cookie 设置为安全。请参阅 <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-securecookie.html" format="https" scope="external">secureCookie</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 项目描述 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>增强了 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在内部安全扫描期间，发现在使用 DTM 库时，用于会话管理的 Cookie 无法指定正确的属性。这可能会导致无意中共享 Cookie 信息。为解决此问题，我们引入了一个配置，它允许客户将 AMCV Cookie 设置为安全。请参阅 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>集成代码和 ID 必须是数字或非空字符串 </p> </td> 
   <td colname="col2"> <p>修复了当数据包含的集成“代码”或“ID”既不是数字也不是非空字符串时验证“setCustomerIDs”遇到的问题。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS 可在公共 Git 存储库中获取 </td> 
   <td colname="col2"> 现在，所有 Experience Cloud 客户可以通过以下网站在公共 Git 存储库中获取 ECID JS：https://github.com/Adobe-Marketing-Cloud/id-service/releases。 </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 项目描述 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>独特访客计数不切实际地增加 </p> </td> 
   <td colname="col2"> <p>随着Experience Platform Identity Service3.1.0的发布，我们发现了一个问题，该问题导致实施此版本时独特访客计数不现实。此行为仅在使用最新版本的 ECID v3.1.0，并且用户在 Safari 浏览器的隐私设置中选择了“仅允许来自当前的网站”选项时出现。版本 3.1.2 修复了此问题。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>建议您在最方便的时候从3.1.0版升级到最新版本。请参阅版本 3.1.2 描述。Adobe Launch、DTM 和 AppMeasurement 中提供了最新的软件包。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 项目描述 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>在错误的域上设置 Cookie </p> </td> 
   <td colname="col2"> <p>我们修复了以下错误：临时访客 Cookie 设置在“默认”Cookie 域中，而不是设置在配置 (initConfig) 提供的域中。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 项目描述 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>用于多个 ID 同步请求的线程让步 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>对于执行多个 ID 同步的客户，由于会发生持续的 CPU 计算，因此 UI 会在某些情况下受阻。我们引入了线程让步功能，以便分隔 ID 同步请求（每个请求 100 毫秒）。 </p> <p>对于使用 Visitor 2.3.0+ 和 DIL 6.10+ 的客户，此更改将为他们提升性能。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 添加了禁用第三方调用的功能 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe 对以下配置进行了重新命名，以允许禁用第三方同步调用。 </p> <p>将 idSyncDisableSyncs 重命名为 disableIdSyncs </p> <p>将 idSyncDisable3rdPartySyncing 重命名为 disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer 支持 </p> </td> 
   <td colname="col2"> <p>ID 服务不再支持 Internet Explorer 6、7、8 和 9。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance 文档更新 </p> </td> 
   <td colname="col2"> <p>向访客函数添加了有关不要使用 var visitor = new Visitor 实例化此函数的警告。 </p> </td> 
  </tr> 
 </tbody> 
</table>

