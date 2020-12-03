---
description: 在网站上启用了选择加入后，在浏览器中使用开发人员工具按照验证方法测试该服务是否正常工作。
seo-description: 在网站上启用了选择加入后，在浏览器中使用开发人员工具按照验证方法测试该服务是否正常工作。
seo-title: 验证选择加入服务
title: 验证选择加入服务
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 27%

---


# 验证选择加入服务{#validating-opt-in-service}

在网站上启用了选择加入后，在浏览器中使用开发人员工具按照验证方法测试该服务是否正常工作。

## 用例 1：启用选择加入 {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

在加载页面之前，请清除缓存和cookie。

在Chrome中，右键单击网页并选择Inspect。 如上面的屏幕截图所示，选择 *“网络* ”选项卡以视图从浏览器发出的请求。

在上面的示例中，页面上安装了以下AdobeJS标记：ECID、AAM、分析和目标。

**如何证明选择加入正常工作：**

您不应看到对Adobe服务器的任何请求：

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>您可能会看到对 `http://dpm.demdex.net/optOutStatus` 的调用，这是一个“只读”端点，用于检索访客的选择退出状态。此端点不会导致创建任何第三方Cookie，也不会从页面收集任何信息。

您不应看到由Adobe标记创建的任何Cookie:(AMCV_{{YOUR_ORG_ID}}、mbox、demdex、s_cc、s_sq、everest_g_v2、everest_session_v2)

在Chrome中，转至“应 *用程序* ”选项卡，展开“ *存储* ”下的 *“Cookies*”部分，然后选择您网站的域名：

![](assets/use_case_1_2.png)

## 用例2:启用加入和存储 {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

用例2的唯一区别是您将看到 *一个新Cookie* ，其中将包含访客提供的加入权限： **adobeujs-optin**

## 用例3:启用加入和预先批准Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

由于Adobe Analytics已预先加入，您将在“网络”选项卡中看到跟踪服务器的请求：

![](assets/use_case_3_1.png)

您将在“应用程序”选项卡中看到Analytics cookie:

![](assets/use_case_3_2.png)

## 用例4:启用加入和IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**如何在页面上视图您当前的IAB同意：**

打开开发人员工具并选择“控 *制台* ”选项卡。 粘贴以下代码片段并按Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

以下是批准用途1、2和5且批准Audience Manager供应商ID时的输出示例：

* demdex.net/id:此调用的存在证明ECID已从demdex.net请求ID
* demdex.net/event:此调用的存在证明DIL数据收集调用正按预期工作。
* demdex.net/dest5.html:此调用的存在证明ID同步正在被触发。

![](assets/use_case_4_1.png)

如果以下某项无效，您将看不到任何向Adobe服务器发出的请求，也看不到Adobecookie:

* 用途1、2或5未获得批准。
* Audience Manager供应商ID未获批准。