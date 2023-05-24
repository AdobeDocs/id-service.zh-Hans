---
description: 将他们的同意管理平台 (CMP) 与选择加入的适用于 IAB 透明度和同意框架 (TCF) 的 Audience Manager 插件连接起来。
title: 在 IAB 框架中使用选择加入服务
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 100%

---

# 在 IAB 框架中使用选择加入服务{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>以下文档仅适用于 IAB 2.0。用户需要使用 Visitor.js 版本 5.0 才能与 IAB 2.0 一起使用。

将同意管理平台 (CMP) 与选择加入的 IAB 透明度和同意框架 (TCF) 插件相连接。

使用 [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Adobe Audience Manager 客户可以将其同意管理平台 (CMP) 与选择加入的 IAB TCF 插件相连接。选择加入是 (ECID) JavaScript 库中嵌入的一项功能，可根据 CMP 中设置的访客首选项来禁用单个 Adobe 解决方案库。使用 ECID 库实施选择加入的 IAB TCF 插件时，支持 IAB TCF 的 CMP 中的访客首选项会自动映射到选择加入。这些首选项将在收到同意后启用基于 Audience Manager 的库（DIL 和 ECID）以及相关联的调用。

## 实施支持 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

要将选择加入与 IAB TCF 相集成，您需要完成以下操作：

1. 实施支持 IAB 并注册为 IAB 供应商的 CMP，或开发一个实施 IAB TCF 规范的内部 CMP，并在 IAB TCF 注册为 CMP。
1. 在加载 Adobe JS 之前定义/加载 `__tcfapi`

有关更多详细信息，请阅读[互动广告局文档](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)。

## 在 ECID Javascript 库中启用选择加入的 IAB TCF 插件 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>选择加入仅适用于 ECID 4.0 以上版本。

使用 Adobe Experience Platform Launch 为您的站点实施选择加入的 IAB TCF 插件。为选择加入手动启用 IAB 时，检查以确保在访客对象中将以下设置设置为 true：

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

正确配置设置后，将根据 CMP 和 IAB TCF 中的同意标准启用/禁用 ECID 和 DIL 库。

>[!IMPORTANT]
>
>Audience Manager 需要获取&#x200B;*目的 1、和目的 10 的同意，以及供应商同意*&#x200B;才能部署 Cookie 并启动 ID 同步或使之生效。可在[此处](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=zh-Hans)阅读 Audience Manager 文档中有关选择加入的 IAB TCF 插件的更多信息。

有关如何验证选择加入的 IAB TCF 插件的更多信息，请在[此处](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)查看验证指南中的用例 4。

## 相关文档 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明度和同意框架 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - 介绍了 IAB 标准的详细信息
* [Adobe 选择加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 介绍了选择加入的详细信息，它是平台解决方案中用于同意管理的所需组件
* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=zh-Hans) 中的 IAB 透明度和同意框架 (TCF) 支持
* [您的隐私选择](https://www.adobe.com/cn/privacy/opt-out.html#customeruse) - 用户可以使用的另一个隐私选项是，可以使用其他全局选择退出工具选择退出所有数据收集。全局选择退出的优先权高于选择加入和 IAB TCF 验证
