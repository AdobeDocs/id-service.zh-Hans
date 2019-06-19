---
description: 在网站上启用了选择加入后，使用验证方法测试服务是否按浏览器中的开发人员工具正常工作。
seo-description: 在网站上启用了选择加入后，使用验证方法测试服务是否按浏览器中的开发人员工具正常工作。
seo-title: 验证参与服务
title: 验证参与服务
uuid: 1743360a-d757-4e50-8697-0fa92 b302 cBC
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# 验证参与服务{#validating-opt-in-service}

在网站上启用了选择加入后，使用验证方法测试服务是否按浏览器中的开发人员工具正常工作。

## 使用案例1：启用选择加入 {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

在加载页面之前，请清除缓存和 Cookie。

在 Chrome 中，右键单击网页并选择“检查”。如上面的屏幕截图所示，选择 *Network* 选项卡以查看从浏览器中发出的请求。

在上面的示例中，我们在页面上安装了以下 Adobe JS 标签：ECID、AAM、Analytics 和 Target。

**如何证明选择加入的工作方式符合预期：**

您不应看到向 Adobe 服务器发出的任何请求：

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>您可能会看到一 `http://dpm.demdex.net/optOutStatus`个调用，它是一个只读端点，用于检索访客的退出状态。此端点既不会创建任何第三方 Cookie，也不会从页面收集任何信息。

您不应看到 Adobe 标签创建的任何 Cookie：(AMCV_{{YOUR_ORG_ID}}、mbox、demdex、s_cc、s_sq、everest_g_v2、everest_session_v2)

在 Chrome 中，转到 *Application* 选项卡，展开 *Storage* 下的 *Cookies* 部分，然后选择您网站的域名：

![](assets/use_case_1_2.png)

## 用例 2：启用选择加入和存储 {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

用例 2 的唯一区别在于，您将会看到一个新 Cookie**，其中将包含访客提供的选择加入权限：**adobeujs-optin**

## 用例 3：启用选择加入并预先批准 Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

由于 Adobe Analytics 已预先批准选择加入，因此您会在“Network”选项卡中看到向跟踪服务器发出的请求：

![](assets/use_case_3_1.png)

并且将在“Application”选项卡中看到以下 Analytics Cookie：

![](assets/use_case_3_2.png)

## 用例 4：启用选择加入和 IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**如何在页面上查看您当前的 IAB 同意：**

打开开发人员工具，然后选择 *Console* 选项卡。粘贴以下代码段并按 Enter 键：

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

以下是当目的 1、2 和 5 以及 Audience Manager 供应商 ID 已获批准时的示例输出：

* demdex.net/id：存在此调用表明 ECID 已从 demdex.net 申请了一个 ID
* demdex.net/event：存在此调用表明 DIL 数据收集调用正按预期工作。
* demdex.net/dest5.html：存在此调用表明“ID 同步”正被触发。

![](assets/use_case_4_1.png)

如果以下某项无效，您将不会看到向 Adobe 服务器发出的任何请求，也不会看到任何 Adobe Cookie：

* 目的 1、2 或 5 未获批准。
* Audience Manager 供应商 ID 未获批准。