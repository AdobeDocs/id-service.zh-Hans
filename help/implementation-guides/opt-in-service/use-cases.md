---
description: 用于管理选择加入服务的示例用例和解决方案。
title: 选择加入用例
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '424'
ht-degree: 100%

---

# 选择加入用例 {#opt-in-use-cases}

用于管理选择加入服务的示例用例和解决方案。

## 提示和故障诊断 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 访客 JS 初始化是同步的，在页面加载期间执行。如果您与 CMP 或具有高延迟的许可持久性连接，使用[选择加入设置](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)中所述的异步函数会更好。
* 选择加入是一项因域而异的实施。它不会处理跨域实施。
* 若要针对特定库禁用第三方调用，您需要在每个库中分别配置该偏好设置。

## 选择加入方案 {#section-1178053c065c430bba26f82ef383a71c}

以下用例是使用选择加入服务的示例构思。

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 要求 </th> 
   <th colname="col2" class="entry"> 解决方案 </th> 
   <th colname="col3" class="entry"> 影响 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>在同意前 Analytics 可以进行收集，但只有在征得同意后才能加载所有其他库 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics 类别 </p> </td> 
   <td colname="col3"> <p>Analytics 在同意前收集中使用 Analytics 标识符（而非 ECID）。ECID 获批后，系统将使用新标识符，并且访客将接收可用于激活和集成的 ECID。 </p> <p>访客应按同意前/同意后分段。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在同意前，第一方度量可以进行收集。在征得同意之前，禁止所有其他类型的数据使用。 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics + ECID 库。 </p> <p>将“disablethirdpartycookies”配置添加到 ECID 库以阻止在同意前发生第三方 Cookie + ID 同步 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 调用会触发 ECID 检索，但不存在任何 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>对于 Analytics，确保访客在同意前/同意后保持一致。同意前收集将与同意后数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在同意前，可以进行第一方度量和定位。在征得同意之前，禁止所有其他类型的数据使用。 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics + ECID + Target 库。 </p> <p>将 <span class="codeph">isablethirdpartycookies</span> 配置添加到 ECID 库以阻止在同意前发生第三方 Cookie + ID 同步在同意后移除标志。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 调用会触发 ECID 检索，但不存在任何 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>对于第三方解决方案，确保访客在同意前/同意后保持一致。同意前收集将与同意后数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在同意前不得设置任何 Cookie </p> </td> 
   <td colname="col2"> <p>使用选择加入阻止加载所有库，直到征得同意后才解除阻止 </p> </td> 
   <td colname="col3"> <p>实施按预期进行，所有库（包括 ECID）都将在同意后按照正确的序列加载。 </p> <p>从不同意被跟踪的客户会遇到数据丢失情况。 </p> </td> 
  </tr> 
 </tbody> 
</table>
