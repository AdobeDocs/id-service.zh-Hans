---
description: 将他们的同意管理平台 (CMP) 与选择加入的 IAB 插件连接起来。
seo-description: 将他们的同意管理平台 (CMP) 与选择加入的 IAB 插件连接起来。
seo-title: （Beta 版）在 IAB 框架中使用选择加入服务
title: （Beta 版）在 IAB 框架中使用选择加入服务
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# （Beta 版）在 IAB 框架中使用选择加入服务{#beta-using-opt-in-services-with-iab-framework}

将他们的同意管理平台 (CMP) 与选择加入的 IAB 插件连接起来。

使用 [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Audience Manager 客户可以将他们的同意管理平台 (CMP) 与选择加入的 IAB 插件连接起来。选择加入是 (ECID) JavaScript 库中嵌入的一项功能，可根据 CMP 中设置的访客首选项来禁用单个 Adobe 解决方案库。使用 ECID 库实施 IAB 插件时，IAB 兼容 CMP 中的访客首选项会自动映射到选择加入。这些首选项将在收到同意后启用基于 Audience Manager 的库（DIL 和 ECID）以及相关联的调用。

## 实施支持 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

要将选择加入与 IAB 同意相集成，您需要完成以下操作：

1. 实施支持 IAB 并[注册为 IAB 供应商](https://vendorlist.consensu.org/vendorlist.json)的 CMP，或开发一个实施 IAB 规范的内部 CMP，并在 IAB Europe 注册为 CMP。
1. 在加载 Adobe JS 之前定义/加载 `__cmp`

有关更多详细信息，请参阅[交互式广告部文档](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在 ECID Javascript 库中启用 IAB 插件 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>选择加入仅适用于 ECID 4.0 以上版本

使用 Adobe Experience Platform Launch 为您的站点同时实施选择加入和 IAB 插件。阅读 [ECID 选择加入扩展的文档](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/)，了解如何设置 Experience Platform Launch 扩展。

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
>Audience Manager 需要获取目的 1、2 和 5 的同意，以及供应商同意&#x200B;**&#x200B;才能部署 Cookie 并启动 ID 同步或使之生效。请在[此处](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)阅读 Audience Manager 文档中有关 IAB 插件的更多信息。

有关如何验证选择加入和 IAB 插件的更多信息，请在[此处](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)查看验证指南中的用例 4。

## 相关文档 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - 介绍了 IAB 标准的更多信息
* [Adobe 选择加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 介绍了选择加入的详细信息，它是平台解决方案中用于同意管理的所需组件
* [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) 中的 IAB 透明度和同意框架 (TCF) 支持
* [您的隐私选择](https://www.adobe.com/cn/privacy/opt-out.html#customeruse) - 用户可以使用的另一个隐私选项是，可以使用其他全局选择退出工具选择退出所有数据收集。全局选择退出的优先权高于选择加入和 IAB 验证

