---
description: 用于管理参与服务的示例用例和解决方案。
seo-description: 用于管理参与服务的示例用例和解决方案。
seo-title: 选择加入用例
title: 选择加入用例
uuid: d75a44d4-b713-43d1-b5 b6-95d1 d0 d213 a7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 选择加入用例 {#opt-in-use-cases}

用于管理参与服务的示例用例和解决方案。

## 提示和故障诊断 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 访客 JS 初始化是同步过程，并会在页面加载期间执行。如果您使用的 CMP 或权限持久性具有较高的延迟，则最好使用[选择加入设置](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)中所述的异步功能。
* 选择加入按域进行实施。它不会处理跨域实施。
* 要禁用特定库的第三方调用，您将需要在每个库中分别配置该首选项。

## 选择加入方案 {#section-1178053c065c430bba26f82ef383a71c}

这些用例是使用选择服务的示例。

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
   <td colname="col1"> <p>可以在同意前收集 Analytics，但只有在收到同意后才能加载所有其他库 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics 类别 </p> </td> 
   <td colname="col3"> <p>在同意前的收集中，Analytics 使用 Analytics 标识符而不是 ECID。一旦 ECID 获得批准，将会使用新的标识符，且访客将会收到可用于激活和集成的 ECID。 </p> <p>需要在同意前/后对访客进行分段。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>可以在同意前收集第一方测量。在收到同意之前，阻止使用所有其他类型的数据。 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics 和 ECID 库 </p> <p>将“disablethirdpartycookies”配置添加到 ECID 库以阻止在同意前发生第三方 Cookie 和 ID 同步 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 调用将会触发 ECID 检索，但不发生 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>使 Analytics 的访客在同意前/后保持一致。同意前的收集将与同意后的数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>同意前可接受第一方测量和定位。在收到同意之前，阻止使用所有其他类型的数据。 </p> </td> 
   <td colname="col2"> <p>使用选择加入在同意前启用 Analytics、ECID 和 Target 库 </p> <p>将 <span class="codeph">isablethirdpartycookies</span> 配置添加到 ECID 库以阻止在同意前发生第三方 Cookie + ID 同步同意后删除标志。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 调用将会触发 ECID 检索，但不会发生 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>使第一方解决方案的访客在同意前/后保持一致。同意前的收集将与同意后的数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>不允许在同意前设置 Cookie </p> </td> 
   <td colname="col2"> <p>使用选择加入阻止所有库加载，直到收到同意为止 </p> </td> 
   <td colname="col3"> <p>在同意后，实施会正常执行，并且所有库（包括 ECID）将按正确顺序加载。 </p> <p>从未同意跟踪的客户的数据会丢失。 </p> </td> 
  </tr> 
 </tbody> 
</table>

