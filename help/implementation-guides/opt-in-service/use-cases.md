---
description: 用于管理选择加入服务的示例用例和解决方案。
seo-description: 用于管理选择加入服务的示例用例和解决方案。
seo-title: 选择加入用例
title: 选择加入用例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 16%

---


# 选择加入用例 {#opt-in-use-cases}

用于管理选择加入服务的示例用例和解决方案。

## 提示和故障诊断 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 访客JS初始化是同步的，在页面加载期间执行。 如果您与CMP或具有高延迟的权限持久性进行接口，则最好使用“选择加入设置”中所述 [的异步功能](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)。
* 选择加入是按域实现。 它将不处理跨域实现。
* 要禁用特定库的第三方调用，您需要在每个库中单独配置该首选项。

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
   <td colname="col1"> <p>分析可以在事先同意状态下进行收集，但只有在收到同意后才能加载所有其他库 </p> </td> 
   <td colname="col2"> <p>使用选择加入功能，使Analytics类别处于预先同意状态 </p> </td> 
   <td colname="col3"> <p>Analytics在预先同意的集合中使用Analytics标识符而非ECID。 ECID获得批准后，将使用新标识符，访客将收到可用于激活和集成的ECID。 </p> <p>预期在同意前／同意后状态访客碎片。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>第一方测量在预先同意状态下可以收集。 在收到同意之前，禁止所有其他类型的数据使用。 </p> </td> 
   <td colname="col2"> <p>使用选择加入功能，使Analytics + ECID库处于预先同意状态。 </p> <p>将“disablethirdpartycookies”配置添加到ECID库以阻止处于预先同意状态的第三方cookie + ID同步 </p> </td> 
   <td colname="col3"> <p>AdobeDemdex调用将触发ECID检索，但不存在Demdex cookie、其他第三方cookie或ID同步。 </p> <p>在Analytics的同意前／同意后状态中保持一致的访客。 在预先同意状态下进行收集将与事后同意数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在预先同意状态下，第一方衡量和定位是可以接受的。 在收到同意之前，禁止所有其他类型的数据使用。 </p> </td> 
   <td colname="col2"> <p>使用选择加入功能，使Analytics + ECID +目标库处于预先同意状态。 </p> <p>将 <span class="codeph">isablethirdpartycookies</span> 配置添加到 ECID 库以阻止在同意前发生第三方 Cookie + ID 同步在“同意后”状态中删除标志。 </p> </td> 
   <td colname="col3"> <p>AdobeDemdex调用将触发ECID检索，但不存在Demdex cookie、其他第三方cookie或ID同步。 </p> <p>在第一方解决方案的同意前／同意后状态中保持一致的访客。 在预先同意状态下进行收集将与事后同意数据收集相关联。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>不允许在预先同意状态中设置Cookie </p> </td> 
   <td colname="col2"> <p>使用选择加入功能阻止所有库在收到同意之前加载 </p> </td> 
   <td colname="col3"> <p>实施符合预期，所有库（包括ECID）在同意后状态将以正确的顺序加载。 </p> <p>从未同意跟踪的客户的数据丢失。 </p> </td> 
  </tr> 
 </tbody> 
</table>

