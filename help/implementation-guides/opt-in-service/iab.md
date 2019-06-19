---
description: 使用选择加入的IAB插件连接他们的同意管理平台(CMP)。
seo-description: 使用选择加入的IAB插件连接他们的同意管理平台(CMP)。
seo-title: (测试版)使用IAB Framework中的选择服务
title: (测试版)使用IAB Framework中的选择服务
uuid: df39d9c-c016-490e-b4 db-d02 e4044 b480
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# (测试版)使用IAB Framework中的选择服务{#beta-using-opt-in-services-with-iab-framework}

使用选择加入的IAB插件连接他们的同意管理平台(CMP)。

使用 [IAB透明度和同意框架(TCF)的Audience Manager客户](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 可以将他们的同意管理平台(CMP)与选择加入IAB插件连接。选择加入是嵌入到ECID JavaScript库中的一项功能，该功能可根据在CMP中设置的访客首选项禁用单个Adobe解决方案库。当IAB插件通过ECID库实现时，您的IAB兼容型CMP中的访客首选项会自动映射到选择加入。在收到同意后，这些首选项将启用基于Audience Manager的库(DIL和ECID)和关联的呼叫。

## 实施支持 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

要将选择加入与 IAB 同意相集成，您需要完成以下操作：

1. 实施支持 IAB 并[注册为 IAB 供应商](https://vendorlist.consensu.org/vendorlist.json)的 CMP，或开发一个实施 IAB 规范的内部 CMP，并在 IAB Europe 注释为 CMP。
1. 定义/加载Adobe JS `__cmp` 之前的加载。

有关更多详细信息，请阅读[互动广告局文档](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在 ECID Javascript 库中启用 IAB 插件 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>选择加入仅在EID4.0+中可用

使用 Adobe Launch 为您的站点同时实施选择加入和 IAB 插件。请阅读[有关 ECID 选择加入扩展的文档](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/)，了解如何设置 Launch 扩展。

为选择加入手动启用 IAB 时，请检查以确保在访客对象中将以下设置设为 true：

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

正确配置设置后，系统将根据 CMP 和 IAB 框架中的同意标准启用/禁用 ECID 和 DIL 库。

>[!IMPORTANT]
>
>Audience Manager 需要获取目的 1、2 和 5 的同意，以及供应商同意**才能部署 Cookie 并启动 ID 同步或使之生效。请阅读AAB Manager文档中的IAB插件**** [此处](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**。

有关如何验证选择加入和 IAB 插件的更多信息，请在[**此处**](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)查看验证指南中的用例 4。

## 相关文档 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - 介绍了 IAB 标准的详细信息
* [Adobe 选择加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 介绍了选择加入的详细信息，它是平台解决方案中用于同意管理的所需组件
* [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) 中的 IAB 透明度和同意框架 (TCF) 支持
* [您的隐私选择](https://www.adobe.com/privacy/opt-out.html#customeruse) - 用户可以使用的另一个隐私选项是，可以使用其他全局选择退出工具选择退出所有数据收集。全局选择退出的优先权高于选择加入和 IAB 验证

