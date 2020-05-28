---
description: 将他们的同意管理平台 (CMP) 与选择加入的适用于 IAB 透明度和同意框架 (TCF) 的 Audience Manager 插件连接起来。
seo-description: 将他们的同意管理平台 (CMP) 与适用于 IAB 透明度和同意框架 (TCF) 的 Audience Manager 插件连接起来。
seo-title: 在 IAB 框架中使用选择加入服务
title: 在 IAB 框架中使用选择加入服务
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 61%

---


# 在 IAB 框架中使用选择加入服务{#using-opt-in-services-with-iab-framework}

将同意管理平台 (CMP) 与选择加入的适用于 IAB TCF 的 Audience Manager 插件连接起来。

使用 [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Audience Manager 客户，可以将他们的同意管理平台 (CMP) 与选择加入的适用于 IAB TCF 的 Audience Manager 插件连接起来。选择加入是 (ECID) JavaScript 库中嵌入的一项功能，可根据 CMP 中设置的访客首选项来禁用单个 Adobe 解决方案库。当使用ECID库实现IAB TCF的受众管理器插件时，您的CMP中支持IAB TCF的访客首选项将自动映射到选择加入。 这些首选项将在收到同意后启用基于 Audience Manager 的库（DIL 和 ECID）以及相关联的调用。

## 实施支持 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

为了让选择加入与IAB TCF集成，您需要完成以下工作：

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. 在加载 Adobe JS 之前定义/加载 `__cmp`

有关更多详细信息，请阅读[互动广告局文档](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在 ECID Javascript 库中启用适用于 IAB TCF 的 Audience Manager 插件 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>选择加入仅在ECID 4.0+中可用。

使用 Adobe Experience Platform Launch 为您的站点同时实施选择加入和适用于 IAB TCF 的 Audience Manager 插件。手动启用IAB以加入时，请检查以确保在访客对象中将以下设置设置为true:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

正确配置设置后，将根据CMP和IAB TCF的同意标准启用／禁用ECID和DIL库。

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. 有关适用于 IAB TCF 的 Audience Manager 插件的更多信息，请阅读[此处](https://docs.adobe.com/help/zh-Hans/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)的 Audience Manager 文档。

有关如何验证选择加入和适用于 IAB TCF 的 Audience Manager 插件的更多信息，请在[此处](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)查看验证指南中的用例 4。

## 相关文档 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - 介绍了 IAB 标准的详细信息
* [Adobe 选择加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 介绍了选择加入的详细信息，它是平台解决方案中用于同意管理的所需组件
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [您的隐私选择](https://www.adobe.com/cn/privacy/opt-out.html#customeruse) -用户可选择的另一个隐私选项是能够使用选择退出其他全局选择退出工具收集所有数据。 全局退出优先于选择加入和IAB TCF验证

