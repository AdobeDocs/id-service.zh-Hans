---
description: 关于 2018 版 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID Service
seo-description: 关于 2018 版 Experience Cloud Identity 服务的功能发布、更新或更改。
seo-title: 2018 版发行说明
title: 2018 版发行说明
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 35%

---


# 2018 版发行说明 {#release-notes}

关于 2018 版 Experience Cloud Identity 服务的功能发布、更新或更改。

## 版本 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 物料说明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>提高了AMCV cookies的安全性 </p> </td> 
   <td colname="col2"> <p>在内部安全扫描过程中，发现在使用DTM库时，用于会话管理的cookies无法指定正确的属性。 这可能导致Cookie信息在不经意间共享。 为此，我们引入了一种允许客户将AMCV cookie设置为安全的配置。 请参阅 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 物料说明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>提高了AMCV cookies的安全性 </p> </td> 
   <td colname="col2"> <p>在内部安全扫描过程中，发现在使用DTM库时，用于会话管理的cookies无法指定正确的属性。 这可能导致Cookie信息在不经意间共享。 为此，我们引入了一种允许客户将AMCV cookie设置为安全的配置。 请参阅 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>集成代码和id必须是数字或非空字符串 </p> </td> 
   <td colname="col2"> <p>修复了当数据包含非数字或非空字符串的集成“代码”或“id”时验证“setCustomerID”的问题。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS在Public Git回购中可用 </td> 
   <td colname="col2"> ECID JS现已在公共Git回购中提供，适用于所有Experience Cloud客户：https://github.com/Adobe-Marketing-Cloud/id-service/releases。 </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 物料说明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>独特访客计数不切实际地增加 </p> </td> 
   <td colname="col2"> <p>在 Experience Cloud Identity 服务 3.1.0 中，我们发现了一个问题，即，在实施此版本后，独特访客计数会不切实际地增加。此行为仅在ECID的最新版本v3.1.0中显示，如果用户在Safari浏览器的隐私设置中选择了“仅从当前网站允许”选项。 3.1.2版修复了此问题。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>建议您尽早从版本 3.1.0 升级到最新版本。请参阅版本 3.1.2 描述。Adobe Experience Platform Launch、DTM 和 AppMeasurement 中提供了最新的软件包。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 物料说明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>在不正确的域上设置Cookie </p> </td> 
   <td colname="col2"> <p>我们修复了临时访客cookie在“默认”cookie域中设置cookie而不是在配置(initConfig)中提供的域中设置cookie的错误。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 物料说明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>用于多个 ID 同步请求的线程让步 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>对于执行多个ID同步的客户，由于CPU计算不断进行，UI在某些情况下会被阻止。 我们引入了线程屈服，以将ID同步请求分隔100毫秒。 </p> <p>此更改将提高使用访客2.3.0+和DIL6.10+的客户的性能。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 添加了禁用第三方调用的功能 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe 对以下配置进行了重新命名，以允许禁用第三方同步调用。 </p> <p>将 idSyncDisableSyncs 重命名为 disableIdSyncs </p> <p>将 idSyncDisable3rdPartySyncing 重命名为 disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer支持 </p> </td> 
   <td colname="col2"> <p>ID服务不再支持Internet Explorer 6、7、8和9。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance 文档更新 </p> </td> 
   <td colname="col2"> <p>向访客函数添加了有关不要使用 var visitor = new Visitor 实例化此函数的警告。 </p> </td> 
  </tr> 
 </tbody> 
</table>

