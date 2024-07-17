---
description: 这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于 ID 服务与 Experience Cloud 解决方案的各种组合。
keywords: ID 服务
title: 测试和验证 Experience Cloud Identity 服务
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 100%

---

# 测试和验证 Experience Cloud Identity 服务{#test-and-verify-the-experience-cloud-id-service}

这些说明、工具和过程可帮助您确定 ID 服务是否正常运行。这些测试通常适用于 ID 服务，也适用于 ID 服务与 Experience Cloud 解决方案的各种组合。

## 开始之前 {#section-b1e76ad552ed4eb793b6e521a55127d4}

在开始测试和验证 ID 服务之前需要了解的重要信息。

**浏览器环境**

在正常的浏览器会话中进行测试时，请在每次测试前清除浏览器缓存。

或者，您也可以在匿名或私密浏览器会话中测试 ID 服务。在匿名会话中，您无需在每次测试前都清除浏览器 Cookie 或缓存。

**工具**

[Adobe 调试器](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=zh-Hans)和 [Charles HTTP 代理](https://www.charlesproxy.com/)可帮助您确定 ID 服务是否已配置为可在 Analytics 中正常使用。此部分中的信息基于 Adobe 调试器和 Charles 返回的结果。当然，您也可以随意使用最适合您的任何工具或调试器。

## 使用 Adobe 调试器进行测试 {#section-861365abc24b498e925b3837ea81d469}

当您在 [!DNL Adobe] 调试器响应中看到 [!DNL Experience Cloud ID] (MID) 时，即表明您的服务集成配置正确。请参阅 [Cookie 和 Experience Cloud Identity 服务](../introduction/cookies.md)，以了解有关 MID 的更多信息。

要通过 [!DNL Adobe] [调试器](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=zh-Hans)验证 ID 服务的状态，请执行以下操作：

1. 清除您的浏览器 Cookie 或打开匿名浏览会话。
1. 加载包含 ID 服务代码的测试页面。
1. 打开 [!DNL Adobe] 调试器。
1. 在结果中检查 MID。

## 了解 Adobe 调试器结果 {#section-bd2caa6643d54d41a476d747b41e7e25}

MID 存储在一个键值对中，它使用以下语法：`MID= *`Experience Cloud ID`*`。调试器将显示此信息，如下所示。

**成功**

如果您看到类似于下面的响应，则表示 ID 服务已正确实施：

```
mid=20265673158980419722735089753036633573
```

如果您是 [!DNL Analytics] 客户，除 MID 以外，可能还会看到 [!DNL Analytics] ID (AID)。这种情况发生于：

* 您的一些早期/长期网站访客。
* 您已启用宽限期时。

**失败**

如果调试器出现以下情况，请联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)：

* 不返回 MID。
* 返回一条错误消息，指示您的合作伙伴 ID 尚未配置。

## 通过 Charles HTTP 代理进行测试 {#section-d9e91f24984146b2b527fe059d7c9355}

要通过 Charles 验证 ID 服务的状态，请执行以下操作：

1. 清除您的浏览器 Cookie 或打开匿名浏览会话。
1. 启动 Charles。
1. 加载包含 ID 服务代码的测试页面。
1. 查看下述请求和响应调用以及数据。

## 了解 Charles 结果 {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

有关查看位置、搜寻对象以及何时使用 Charles 监视 HTTP 调用的信息，请参阅此部分。

**Charles 中成功的 ID 服务请求**

当 `Visitor.getInstance` 函数对 `dpm.demdex.net` 进行 JavaScript 调用时，您的 ID 服务代码工作正常。成功的请求包含您的[组织 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)。组织 ID 可作为一个使用以下语法的键值对传递：`d_orgid= *`组织 ID`*`。在“`dpm.demdex.net`结构[!UICONTROL ”选项卡下方查找 ] 和 JavaScript 调用。在“[!UICONTROL 请求]”选项卡下方查找您的组织 ID。

![](assets/charles_request.png)

**Charles 中成功的 ID 服务响应**

当来自[数据收集服务器](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html?lang=zh-Hans) (DCS) 的响应返回 MID 时，您的帐户已正确配置。MID 作为使用以下语法的键值对返回：`d_mid: *`访客 Experience Cloud ID`*`。在“[!UICONTROL 响应]”选项卡中查找 MID，如下所示。

![](assets/charles_response_success.png)

**Charles 中失败的 ID 服务响应**

如果 DCS 响应中缺失 MID，则表示您的帐户未正确配置。失败的响应会在“[!UICONTROL 响应]”选项卡中返回一个错误代码和一条消息，如下所示。如果您在 DCS 响应中看到此错误消息，请联系客户关怀。

![](assets/charles_response_unsuccessful.png)

有关错误代码的更多信息，请参阅 [DCS 错误代码、消息和示例](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html?lang=zh-Hans)。
