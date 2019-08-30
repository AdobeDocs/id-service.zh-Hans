---
description: 这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。
keywords: ID 服务
seo-description: 这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。
seo-title: 测试和验证 Experience Cloud Identity 服务
title: 测试和验证 Experience Cloud Identity 服务
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: ht
source-git-commit: ef3169f8928f337d4f2d17922b44a7421d225e51

---


# 测试和验证 Experience Cloud Identity 服务{#test-and-verify-the-experience-cloud-id-service}

这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。

## 开始之前 {#section-b1e76ad552ed4eb793b6e521a55127d4}

在开始测试和验证 ID 服务之前需要了解的重要信息。

**浏览器环境**

在普通浏览器会话中进行测试时，请在每次测试之前清除您的浏览器缓存。

或者，您也可在匿名或使用假名的浏览器会话中测试 ID 服务。在匿名会话中，您无需在每次测试之前清除浏览器 Cookie 或缓存。

**工具**

[Adobe 调试器](https://marketing.adobe.com/resources/help/zh_CN/sc/implement/debugger.html)和 [Charles HTTP 代理](https://www.charlesproxy.com/)可以帮助您确定 ID 服务是否已配置为在 Analytics 中正常工作。此部分中的信息基于 Adobe 调试器工具和 Charles 代理返回的结果。当然，您也可以随意使用最适合您的任何工具或调试器。

## 通过 Adobe 调试器工具进行测试 {#section-861365abc24b498e925b3837ea81d469}

当您在 [!DNL Adobe] 调试器响应中看到 [!DNL Experience Cloud ID] (MID) 时，即表明您的服务集成配置正确。请参阅 [Cookie 和 Experience Cloud Identity 服务](../introduction/cookies.md)，以了解有关 MID 的更多信息。

要使用 [!DNL Adobe] [调试器](https://marketing.adobe.com/resources/help/zh_CN/sc/implement/debugger.html)验证 ID 服务的状态，请执行以下操作：

1. 清除您的浏览器 Cookie，或打开匿名的浏览会话。
1. 加载包含 ID 服务代码的测试页面。
1. 打开 [!DNL Adobe] 调试器。
1. 在结果中检查 MID。

## 了解 Adobe 调试器结果 {#section-bd2caa6643d54d41a476d747b41e7e25}

MID 存储在一个键值对中，它使用以下语法：`MID= *`Experience Cloud ID`*`。调试器将显示此信息，如下所示。

**成功**

如果您看到一个类似于如下形式的响应，则表明 ID 服务已成功实施：

```
mid=20265673158980419722735089753036633573
```

如果您是 [!DNL Analytics] 客户，除 MID 以外，可能还会看到 [!DNL Analytics] ID (AID)。它发生于以下情况：

* 对于您的某些早期/长期网站访客。
* 如果您启用了宽限期。

**失败**

如果调试器出现以下问题，请联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)：

* 不返回 MID。
* 返回错误消息，指示尚未配置您的合作伙伴 ID。

## 通过 Charles HTTP 代理进行测试 {#section-d9e91f24984146b2b527fe059d7c9355}

要通过 Charles 验证 ID 服务的状态，请执行以下操作：

1. 清除您的浏览器 Cookie，或打开匿名的浏览会话。
1. 启动 Charles。
1. 加载包含 ID 服务代码的测试页面。
1. 检查下述请求和响应调用与数据。

## 了解 Charles 结果 {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

有关查看位置、搜寻对象以及何时使用 Charles 监视 HTTP 调用的信息，请参阅此部分。

**Charles 中成功的 ID 服务请求**

当 `Visitor.getInstance` 函数对 `dpm.demdex.net` 进行 JavaScript 调用时，您的 ID 服务代码工作正常。成功的请求包含您的[组织 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)。组织 ID 可作为一个使用以下语法的键值对传递：`d_orgid= *`组织 ID`*`。在“`dpm.demdex.net`结构[!UICONTROL ”选项卡下方查找 ] 和 JavaScript 调用。在“[!UICONTROL 请求]”选项卡下方查找您的组织 ID。

![](assets/charles_request.png)

**Charles 中成功的 ID 服务响应**

当[数据收集服务器](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) 响应返回 MID 时，即表示您的帐户已针对 ID 服务进行正确配置。MID 作为使用以下语法的键值对返回：`d_mid: *`访客 Experience Cloud ID`*`。在“[!UICONTROL 响应]”选项卡中查找 MID，如下所示。

![](assets/charles_response_success.png)

**Charles 中失败的 ID 服务响应**

如果 DCS 响应中缺失 MID，则表示您的帐户未正确配置。失败的响应在“[!UICONTROL 响应]”选项卡中返回一个错误代码和消息，如下所示。如果您在 DCS 响应中看到此错误消息，请联系客户关怀。

![](assets/charles_response_unsuccessful.png)

有关错误代码的更多信息，请参阅 [DCS 错误代码、消息和示例](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)。
