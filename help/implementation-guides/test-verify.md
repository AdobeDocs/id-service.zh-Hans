---
description: 这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。
keywords: ID 服务
seo-description: 这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。
seo-title: 测试和验证Experience Platform Identity Service
title: 测试和验证Experience Platform Identity Service
uuid: 442de9c3-c265-4412-89bd-aaa286 dwad6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 测试和验证Experience Platform Identity Service{#test-and-verify-the-experience-cloud-id-service}

这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于不同的 ID 服务和 Experience Cloud 解决方案组合。

## 开始之前 {#section-b1e76ad552ed4eb793b6e521a55127d4}

在开始测试和验证ID服务之前需要了解的重要信息。

**浏览器环境**

在普通浏览器会话中进行测试时，请在每次测试之前清除您的浏览器缓存。

或者，您也可在匿名或使用假名的浏览器会话中测试 ID 服务。在匿名会话中，您无需在每次测试之前清除浏览器 Cookie 或缓存。

**工具**

[Adobe 调试器](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)和 [Charles HTTP 代理](https://www.charlesproxy.com/)可帮助您确定 ID 服务是否已配置为可在 Analytics 中正常使用。此部分中的信息基于 Adobe 调试器工具和 Charles 代理返回的结果。当然，您也可以随意使用最适合您的任何工具或调试器。

## 通过 Adobe 调试器工具进行测试 {#section-861365abc24b498e925b3837ea81d469}

当您在调试器响应中看到(MID)时 [!DNL Experience Cloud ID] ，您的服务集成将 [!DNL Adobe] 正确配置。有关MID的更多信息，请参阅 [Cookie和体验平台标识服务](../introduction/cookies.md) 。

要使用 [!DNL Adobe][调试器验证ID服务的状态](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)，请执行以下操作：

1. 清除您的浏览器 Cookie，或打开匿名的浏览会话。
1. 加载包含 ID 服务代码的测试页面。
1. 打开 [!DNL Adobe] 调试器。
1. 在结果中检查 MID。

## 了解Adobe调试器结果 {#section-bd2caa6643d54d41a476d747b41e7e25}

MID存储在使用此语法的键值对中： `MID= *`Experience Cloud ID`*`。调试器将显示此信息，如下所示。

**成功**

如果您看到一个类似于如下形式的响应，则表明 ID 服务已成功实施：

```
mid=20265673158980419722735089753036633573
```

如果您是 [!DNL Analytics] 客户，除 MID 以外，可能还会看到 [!DNL Analytics] ID (AID)。它发生于以下情况：

* 对于您的某些早期/长期网站访客。
* 如果您启用了宽限期。

**失败**

如果调试器出现以下问题，请联系[客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)：

* 不返回 MID。
* 返回错误消息，指示尚未配置您的合作伙伴 ID。

## 使用Charles HTTP代理进行测试 {#section-d9e91f24984146b2b527fe059d7c9355}

要通过 Charles 验证 ID 服务的状态，请执行以下操作：

1. 清除您的浏览器 Cookie，或打开匿名的浏览会话。
1. 启动 Charles。
1. 加载包含 ID 服务代码的测试页面。
1. 检查下述请求和响应调用与数据。

## 了解Charles结果 {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

有关查看位置、搜寻对象以及何时使用 Charles 监视 HTTP 调用的信息，请参阅此部分。

**Charles中的成功ID服务请求**

当 `Visitor.getInstance` 函数对 `dpm.demdex.net` 进行 JavaScript 调用时，您的 ID 服务代码工作正常。成功的请求包含您的[组织 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)。组织ID作为使用此语法的键值对进行传递： `d_orgid= *`organization ID`*`。在 `dpm.demdex.net`[!DNL Structure] 选项卡下查找JavaScript调用。在 [!DNL Request] 选项卡下查找您的组织ID。

![](assets/charles_request.png)

**Charles中成功的ID服务响应**

当来自[数据收集服务器](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) 的响应返回 MID 时，您的帐户已正确配置。MID将作为使用此语法的键值对返回： `d_mid: *`访客Experience Cloud ID`*`。在 [!DNL Response] 选项卡中查找MID，如下所示。

![](assets/charles_response_success.png)

**Charles中的失败ID服务响应**

如果 DCS 响应中缺失 MID，则表示您的帐户未正确配置。失败的响应会在 [!DNL Response] 选项卡中返回错误代码和消息，如下所示。如果您在 DCS 响应中看到此错误消息，请联系客户关怀。

![](assets/charles_response_unsuccessful.png)

有关错误代码的更多信息，请参阅 [DCS 错误代码、消息和示例](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)。
