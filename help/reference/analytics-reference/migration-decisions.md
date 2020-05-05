---
description: 在部署 Experience Cloud Identity 服务之前，您应当了解此服务对多个域上的访客跟踪有何影响，以及在您通过不同方法或 JavaScript 文件收集数据时可能会出现哪些问题。
keywords: ID Service
seo-description: 在部署 Experience Cloud Identity 服务之前，您应当了解此服务对多个域上的访客跟踪有何影响，以及在您通过不同方法或 JavaScript 文件收集数据时可能会出现哪些问题。
seo-title: Experience Cloud Identity 服务迁移决策点
title: Experience Cloud Identity 服务迁移决策点
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity 服务迁移决策点

在部署 Experience Cloud Identity 服务之前，您应当了解此服务对多个域上的访客跟踪有何影响，以及在您通过不同方法或 JavaScript 文件收集数据时可能会出现哪些问题。

此部分中的问题解答可帮助您确定是否应当执行一些额外的迁移步骤。

## 您有数据收集CNAME吗？

许多客户可以作为ID服务迁移的一部分从数据收集CNAME迁移出来。

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 数据收集方法 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>使用CNAME </p> </td> 
   <td colname="col2"> <p>请参阅下一个问题，确定是否应从数据收集CNAME迁移出去。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>没有CNAME </p> </td> 
   <td colname="col2"> <p>跳转至<a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">如果您不具备数据收集 CNAME，那么您的数据收集服务器是 *.2o7.net 还是 *.sc.omtrdc.net？</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 如果您有数据收集CNAME，您是否有多个域？

如果您有多个域将数据发送到同 *一报表包*，则我们建议使用CNAME进行数据收集。 这有助于您跨域跟踪访客。 如果您在单个域上收集数据，则维护数据收集CNAME没有任何优势。

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 从 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>多个域 </p> </td> 
   <td colname="col2"> <p>如果您正在跨多个域跟踪访客，并且您还有一个主入口站点，在客户访问其他域之前可以在该站点中识别客户，那么您应继续使用您的数据收集CNAME。 请参阅<a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">数据收集 CNAME 和跨域跟踪</a>，以了解详细说明。 </p> <p>请注意，您需要指定两个额外的跟踪服务器参数，即 <span class="codeph">visitor.marketingCloudServer</span> 和 <span class="codeph">visitor.marketingCloudServerSecure</span>，以便通过 ID 服务配置 CNAME。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>单个域 </p> </td> 
   <td colname="col2"> <p>使用单个域意味着，如果您不再希望管理数据收集CNAME，您可以从该CNAME迁移出来。 但是，如果您的CNAME正在工作，则无需进行更改。 </p> <p>如果确实删除了CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">确保您的新跟踪服务器<a href="https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external">符合 RDC</a>。 </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">要迁移到 <span class="keyword">Experience Cloud</span> ID 服务，请提前几个月从 CNAME 移至 RDC 跟踪服务器。 </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>请不要</i>使用 <span class="codeph">*.2o7.net</span> 跟踪服务器。 </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">请联系<a href="https://helpx.adobe.com/cn/marketing-cloud/contact-support.html" format="https" scope="external">客户关怀</a>，以设置访客迁移。这有助于确保访客计数的一致性。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 您是否拥有多个 Analytics JavaScript 文件，或者您是否跟踪 Flash 应用程序或视频？

如果您在网站上拥有多个 Analytics JavaScript 文件、Flash 应用程序或视频，且它们要将数据发送至&#x200B;*同一报表包*，则您应当配置一个宽限期，以便在您使用 [!DNL Experience Cloud] ID 服务时，访客可以继续由 Analytics ID 识别。

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 数据收集 </th> 
   <th colname="col2" class="entry"> 必需操作 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">多个分析Javascript文件 </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">其他数据收集方法 </li> 
    </ul> </td> 
   <td colname="col2"> <p>您应配置访客ID服务宽限期，以便将访客ID服务推出到每个JavaScript文件和其他数据收集库。 See <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID Service Grace Period</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>单个Analytics JavaScript文件 </p> </td> 
   <td colname="col2"> <p>您可以更新单个JavaScript文件以使用访客ID服务，而无需宽限期。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 您使用的数据收集方法是否不受支持？

您可能需要更新跟踪链接或从Sliverlight迁移的方式。

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 数据收集方法 </th> 
   <th colname="col2" class="entry"> 必需操作 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript和／或Flash </p> </td> 
   <td colname="col2"> <p>无. <span class="keyword">Experience Cloud</span> ID 服务支持这些数据收集方法。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>如果访客可以访问 Silverlight 内容及您的网站上使用 <span class="keyword">Experience Cloud</span> ID 服务的其他部分，则您需要从 Silverlight 中迁移出来。ID服务不支持Silverlight。 </p> <p> 如果您正在跟踪基于Silverlight的视频播放器，供应商可能会提供您可以改用的JavaScript API。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>硬编码图像标签 </p> </td> 
   <td colname="col2"> <p>更新硬编码链接以使用JavaScript。 </p> </td> 
  </tr> 
 </tbody> 
</table>

