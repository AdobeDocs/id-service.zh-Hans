---
description: 与使用 ID 服务相关的特性、功能和问题的常见问题解答。
keywords: ID 服务
title: ID 服务常见问题解答
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '787'
ht-degree: 100%

---

# ID 服务常见问题解答{#id-service-faqs}

与使用 ID 服务相关的特性、功能和问题的常见问题解答。

## 功能 {#section-659e89f8b9a74cb8afff35587dc96836}

**ID 服务提供哪种功能？**

请参阅[概述](../introduction/overview.md)。

**为什么 ID 服务不发出调用以检索 Experience Cloud ID？**

这可能很难诊断。一种做法是您可以检查网站上的内容安全策略标头。如果您具备严格的安全策略，这些设置可能会阻止 ID 服务发出的第三方调用。请参阅[内容安全策略和 Experience Cloud Identity 服务](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)。

**VisitorAPI.js 文件存储**

如果将 VisitorAPI.js 作为本地文件托管在移动应用程序中，您可能会遇到问题。我们建议您将文件托管在 Web 服务器上。

## 页面加载时间和滞后 {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**ID 服务 VisitorAPI.js 库的位置对页面加载时间有何影响？**

请将 VisitorAPI.js 库放置在页面顶部代码的 `<head>` 部分中。这有助于确保 ID 调用在页面主体开始加载之前发出，并最大限度地增加 ID 成功返回的可能性。

ID 服务调用是异步调用，是对 [demdex.net 域](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans)进行的唯一调用。ID 服务调用不会阻止在页面上加载其他元素。

对于 [!DNL Target] 客户，将 ID 服务代码放置在页面的 `<body>` 中，可能会增加它阻止 [!DNL Target] 调用的可能性。如果必须将 ID 服务代码放置在页面主体中，则应将其放置在 `<body>` 开始标记的后面。

**ID 服务是否在每次加载页面时都进行服务器调用？**

否，仅在首次呈现页面时调用服务器，之后每 7 天进行一次调用。在此期间，不需要服务器调用。ID 服务在客户端模式下运行，无需进行服务器调用即可返回 ID。

请参阅[概述](../introduction/overview.md)。

**使用 ID 服务时，哪些因素会导致页面加载时间变慢或影响用户体验？**

很难列出所有可能的情况。一方面，数以亿计的消费者客户连接到我们的服务，另一方面，这些客户连接的位置和方式千差万别，这都会影响服务性能。例如：

* 移动网络上的速度存在显著差异。此外，这些网络可能还会遭受信号丢失以及数据或语音包丢失。
* 在不同情况下，通过 WiFi 连接的设备可能存在连接问题。例如，在咖啡馆等公共场所或飞机客舱（数据包在到达地面网络之前必须通过卫星弹回）等其他环境下，数据包丢失和速度问题很常见。
* 配置不当的本地网络可能会对连接和速度产生负面影响。
* 客户端设备可能有其自身的问题，如内存不足、磁盘交换过度，或 CPU 功率相对于当前工作负载受限。
* 浏览器会使用不同的规则来排列和执行远程服务器调用，甚至是处理响应，具体取决于浏览器的制造商和版本。这种行为会影响速度和性能。

**能否列举 Adobe 为缩短页面加载时间所做的一些改进？**

例如，线程生成。我们引入了在存在多个 ID 同步请求时进行线程生成的功能。我们从实验室报告中发现，对于执行多个 ID 同步的客户来说，UI 可能会因为发生大量连续 CPU 计算而受阻。因此，我们引入了线程生成，将 ID 同步请求按 100 毫秒进行分离。

对于使用 Visitor 2.3.0 及更高版本和 DIL 6.10 及更高版本的客户，这项更改使性能得以改进。页面加载时间的改进如下图所示：

![](assets/id_sync_improvements_copy.png)

**使用 CORS 与使用 JSON-P 的浏览器请求是否会影响页面性能？**

通常，使用 CORS 的资源请求要优于使用 JSONP 的资源请求。使用 JSONP 时，某些浏览器会排列请求并取消其相对于页面上的其他同步调用和异步调用的优先级。CORS 有助于确保在浏览器调用堆栈中以更高的优先级来处理这些请求。

请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

## 安全性 {#section-b176b8492fbe4acfb79ebb30ec902f98}

**ID 服务是否支持 CORS？**

能。请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**什么是 CORS？**

*`Cross-Origin Resource Sharing`* 或 CORS 是浏览器用来请求资源的一种方法。在支持 CORS 的浏览器中，ID 服务始终使用 CORS 来请求资源。在不支持 CORS 的旧版浏览器中，ID 服务会使用 JSON-P 来请求资源。请参阅 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**如果我的安全要求很严格，以至于我从未想要使用 JSONP，该怎么办？**

如果您的安全要求很严格，请将 ID 服务 API 配置设置为 `useCORSOnly: true`。只有当您确信您的网站访客使用支持 CORS 的浏览器时，才应该启用此模式。

请参阅 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) 和 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

>[!MORELIKETHIS]
>
>* [客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)

