---
description: 以下示例介绍了 2 个与直接集成和 Experience Cloud ID (MID) 有关的常见用例。MID 是您的网站访客的唯一永久性 ID。
keywords: ID 服务
seo-description: 以下示例介绍了 2 个与直接集成和 Experience Cloud ID (MID) 有关的常见用例。MID 是您的网站访客的唯一永久性 ID。
seo-title: 直接集成用例
title: 直接集成用例
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# 直接集成用例 {#direct-integration-use-cases}

以下示例介绍了 2 个与直接集成和 Experience Cloud ID (MID) 有关的常见用例。MID 是您的网站访客的唯一永久性 ID。

>[!TIP]
>
>* 在深入研究用例之前，请查看并了解[代码语法和变量](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)。
>* 有关 MID 的更多信息，请参阅 [Cookie 和 Experience Cloud Identity 服务](../introduction/cookies.md)。
>



## Use case 1: I have an Experience Cloud ID (MID) but want to pass my visitor IDs and set an authentication state {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例元素 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>此用例假设您： </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">拥有网站访客的 MID。假设此 ID 为 1234。 </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">通过您自己的唯一 ID 来识别此访客。假设此 ID 为 9876。 </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">想要将 MID (1234) 关联到您自己的唯一 ID (9876)。 </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>（可选）</i>想要对此访客设置身份验证状态。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>操作</b> </p> </td> 
   <td colname="col2"> <p>根据以上条件，对 ID 服务进行调用，其中应包含： </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID (1234)。 </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">您的数据提供程序 ID。这是为您的公司分配的唯一 ID。假设此 ID 为 4444。 </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">您的访客 ID (9876)。 </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>（可选）</i>用于定义此访客的身份验证状态的状态 ID。 </li> 
    </ul> <p>此外，如果您正好拥有<a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">直接集成指南</a>中所列的任何其他参数（如 <span class="codeph">d_blob</span> 或 <span class="codeph">dcs_region</span> 等），也可以传递这些参数。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案和代码示例</b> </p> </td> 
   <td colname="col2"> <p>将对 ID 服务的调用设置为如下格式： </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>请注意示例调用是如何包含以下内容的： </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID：<span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID 与您的唯一访客 ID 连接在一起：<span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">身份验证状态 ID：<span class="codeph">...d_cid=4444%019876%011</span>（提示：这是最后一位数字）。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 用例 2：我没有 MID，需要生成一个 MID {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 用例元素 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>此用例假设您： </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">没有网站访客的 MID。 </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">需要从 ID 服务请求 MID。 </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">知道您的<a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">组织 ID</a>。假设此 ID 为 5555。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>操作</b> </p> </td> 
   <td colname="col2"> <p>根据以上条件，对 ID 服务进行调用，其中应包含您的组织 ID。 </p> <p>此外，如果您正好拥有<a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">直接集成指南</a>中所列的任何其他参数（如 <span class="codeph">d_blob</span> 或 <span class="codeph">dcs_region</span> 等），也可以传递这些参数。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解决方案和代码示例</b> </p> </td> 
   <td colname="col2"> <p>将对 ID 服务的调用设置为如下格式： </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>请注意示例调用是如何包含您的组织 ID 的：<span class="codeph">d_orgid=5555</span>。该调用将返回此访客的 <span class="keyword">Experience Cloud</span> ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

