---
description: 通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。
keywords: ID 服务
seo-description: 通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。
seo-title: 通过 URL 或数据源进行 ID 同步
title: 通过 URL 或数据源进行 ID 同步
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: cc050064465f6d94621e9f4b8879be3c2bd18a47

---


# 通过 URL 或数据源进行 ID 同步{#id-synchronization-by-url-or-data-source}

通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。

## 语法、属性和宏 {#section-90ac61617482463aaf4c57009b830332}

**语法**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 代码 </th> 
   <th colname="col2" class="entry"> 同步用户 ID </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>通过自定义 ID 同步 URL 在不同数据合作伙伴和 <span class="keyword">Audience Manager</span> 之间同步。 </p> <p> 
     <draft-comment>
       在不同的数据合作伙伴和 Audience Manager 之间同步。例如，合作伙伴 x 将使用此功能将用户 ID 与合作伙伴 y 同步，然后将其发送给 Audience Manager。 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>当您已经知道 DPID 和 DPUUID，并想要将其以标准 ID 同步 URL 格式发送到 <span class="keyword">Audience Manager</span> 时。 </p> <p> 
     <draft-comment>
       当您已经知道用户 ID 并想要将其发送给 Audience Manager 时。 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**属性**

下表列出并定义了可用于两个函数的属性。

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 名称 </th> 
   <th colname="col2" class="entry"> 类型 </th> 
   <th colname="col3" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> 字符串 </td> 
   <td colname="col3"> <p>Audience Manager 分配的数据提供程序 ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> 字符串 </td> 
   <td colname="col3"> <p>用户的唯一数据提供程序 ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 数值 </td> 
   <td colname="col3"> <p> <i>（可选）</i>设置 Cookie 过期时间。必须为整数。默认值为 20160 分钟（14 天）。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 字符串 </td> 
   <td colname="col3"> <p>目标 URL。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**宏**

这两个函数都接受以下宏：

* `%TIMESTAMP%`：生成时间戳（以毫秒为单位）。用于缓存无效的情况。
* `%DID%`：为用户插入 Audience Manager ID。
* `%HTTP_PROTO%`：设置通信协议（`http` 或 `https`）。

## 示例代码和输出 {#section-0115615c37584a19a2ab11e917c4e7e9}

如果运行成功，这两个函数都将返回 `Successfully queued`。如果失败，则将返回错误消息字符串。

### visitor.idSyncByURL

**示例代码**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**示例输出**

`http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D`

### visitor.idSyncByDataSource

**示例代码**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**示例输出**

`http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765`

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/en/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

