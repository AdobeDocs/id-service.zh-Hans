---
description: 通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。
keywords: ID 服务
seo-description: 通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。
seo-title: 通过 URL 或数据源进行 ID 同步
title: 通过 URL 或数据源进行 ID 同步
uuid: ff83d910-8375-4295-9f2a-e14 c15 eee09 a
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# 通过 URL 或数据源进行 ID 同步{#id-synchronization-by-url-or-data-source}

通过 ID 服务函数 idSyncByURL 和 idSyncByDataSource，可手动在目标发布 iFrame 中实施 ID 同步。这些函数可在 VisitorAPI.js 版本 1.10 或更高版本中使用。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> 语法、属性和宏 </a> </li> 
 <li> <a href="../../library/get-set/idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> 示例代码和输出 </a> </li> 
</ul>

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
       不同数据合作伙伴和Audience Manager之间。例如，合作伙伴x将使用此功能将用户ID与合作伙伴y同步，然后将其发送到Audience Manager。 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>当您已经知道 DPID 和 DPUUID，并想要将其以标准 ID 同步 URL 格式发送到 <span class="keyword">Audience Manager</span> 时。 </p> <p> 
     <draft-comment>
       当您知道用户ID并希望将其发送到Audience Manager时。 
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

* ** `%TIMESTAMP%`：**生成时间戳(以毫秒为单位)。用于缓存无效的情况。
* ** `%DID%`：**插入用户的Audience Manager ID。
* ** `%HTTP_PROTO%`：**设置通信协议( `http` 或 `https`)。

## 示例代码和输出 {#section-0115615c37584a19a2ab11e917c4e7e9}

如果成功，两个函数都返回 `Successfully queued` 。如果失败，则将返回错误消息字符串。

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 示例代码 </th> 
   <th colname="col2" class="entry"> 示例输出 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> 发行商
var prector= Compositor. getInstance(“Marketing-Cloud-OMG-ID-ID-HERE”，{})；

    //和amp；nbsp；火和浮雕；nbsp；url&amp; amp；nbsp；&amp; amp；nbsp；宏和amp；nbsp；replacedfolder
    . idSyncByURL({
    &amp; amp；nbsp；dpid：&amp; amp；nbsp；&#39;24&#39;和amp；nbsp；//和amp；nbsp；必须和amp；nbsp；&amp; amp；nbsp；&amp; amp；nbsp；字符串
    和amp；nbsp；url：&amp; amp；nbsp；&#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,&amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp
    ；
    })；&lt;/code&gt;&lt;/p&gt;&lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 示例代码 </th> 
   <th colname="col2" class="entry"> 示例输出 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> 发行商
var prector= Compositor. getInstance(“Marketing-Cloud-OMG-ID-ID-HERE”，{})；

    //和amp；nbsp；火和浮雕；nbsp；&#39;http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;visitor.idSyncByDataSource(
    &#39;
    和nbsp；dpid：&amp; amp；nbsp；&#39;24&#39;和amp；nbsp；//和amp；nbsp；必须和amp；nbsp；&amp; amp；nbsp；&amp; amp；nbsp；字符串
    和amp；nbsp；dpuid：&amp; amp；nbsp；&#39;98765&#39;和amp；nbsp；//和amp；nbsp；必须和amp；nbsp；&amp; amp；nbsp；&amp; amp；nbsp；字符串
    和amp；nbsp；DetailTestLive：&amp; amp；nbsp；20160和amp；nbsp；//和amp；nbsp；可选和逗点；nbsp；默认和amp；nbsp；to&amp; amp；nbsp；20160和amp；nbsp；分钟和amp；nbsp；(14和amp；nbsp；天数)和amp；nbsp；
    })；&lt;/code&gt;&lt;/p&gt;&lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ This]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

