---
description: 与使用 ID 服务相关的特性、功能和问题的常见问题解答。
keywords: ID 服务
seo-description: 与使用 ID 服务相关的特性、功能和问题的常见问题解答。
seo-title: ID 服务常见问题解答
title: ID 服务常见问题解答
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# ID 服务常见问题解答{#id-service-faqs}

与使用 ID 服务相关的特性、功能和问题的常见问题解答。

## 功能 {#section-659e89f8b9a74cb8afff35587dc96836}

**ID 服务提供了哪种功能或哪些功能？**

请参阅[概述](../introduction/overview.md)。

**ID 服务为何不进行调用来检索 Experience Cloud ID？**

此问题的原因可能很难诊断。不过，您可以检查一下您网站上的内容安全策略标头。如果您具有严格的安全策略，这些设置可能会阻止 ID 服务进行的第三方调用。请参阅[内容安全策略和 Experience Cloud Identity 服务](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)。

**VisitorAPI.js 文件存储**

如果您将 VisitorAPI.js 作为本地文件托管在移动应用程序中，则可能会遇到问题。我们建议您在 Web 服务器上托管该文件。

## 页面加载时间和滞后 {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**ID 服务 VisitorAPI.js 库的位置对页面加载时间有何影响？**

请将 VisitorAPI.js 库放置在页面顶部代码的 `<head>` 部分中。这有助于确保 ID 调用在页面主体开始加载之前发出，并最大限度地增加 ID 成功返回的可能性。

ID 服务调用是异步的，它是仅对 [demdex.net 域](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)进行的调用。ID 服务调用不会阻止在页面上加载其他元素。

对于 [!DNL Target] 客户，将 ID 服务代码放置在页面的 `<body>` 中，可能会增加它阻止 [!DNL Target] 调用的可能性。如果必须将 ID 服务代码放置在页面主体中，则应将其放置在 `<body>` 开始标记的后面。

**ID 服务是否会在每次页面加载时都进行服务器调用？**

不会。仅在页面首次渲染时才进行此调用，之后每 7 天进行一次。同时，服务器调用并不是必需的。ID 服务在客户端模式下运行，因此不需要进行服务器调用即可返回 ID。

请参阅[概述](../introduction/overview.md)。

**使用 ID 服务时，什么原因可能会导致页面加载时间缓慢或影响用户体验？**

我们很难将所有可能的情况都列举出来。数以亿计的用户客户端连接到我们的服务，他们的连接位置以及连接方式千差万别，都会对服务的性能造成影响。例如：

* 移动网络的速度存在很大的差异。这些网络也会出现信号以及数据包或语音包丢失等问题。
* 通过 WiFi 连接的设备在多种情况下都会出现连接问题。例如，在咖啡厅等公共场所或飞机客舱（数据包必须通过卫星传输才能抵达地面网络）等其他环境下，数据包丢失和速度缓慢问题很常见。
* 配置较差的本地网络也会对连接和速度产生不良影响。
* 客户设备自身可能存在问题，例如内存较低、磁盘过量交换，或者 CPU 功率有限而无法支撑当前的工作量。
* 浏览器会根据不同的规则将远程服务器调用排入队列并加以执行，甚至还会处理响应，具体取决于浏览器制造商和版本。这一行为也会影响速度和性能。

**可以列举一些为缩短页面加载时间而采取的改善措施吗？**

例如，线程让步。我们引入了线程让步功能，以应对出现多个 ID 同步请求的情况。我们从实验室报告中观察到，对于执行多个 ID 同步的客户，UI 会因为发生大量连续的 CPU 计算而受阻。因此，我们引入了线程让步功能，以将 ID 同步请求分隔开（每个请求 100 毫秒）。

对于使用 Visitor 2.3.0 及更高版本和 DIL 6.10 及更高版本的客户，此更改可为他们提升性能。下图显示了在页面加载时间方面做出的改进。

![](assets/id_sync_improvements_copy.png)

**使用 CORS 与使用 JSON-P 的浏览器请求是否会影响页面性能？**

一般而言，与使用 JSONP 相比，使用 CORS 的资源请求更为有益。使用 JSONP 时，某些浏览器会在将请求排入队列后降低其优先级，而优先考虑页面上的其他同步和异步调用。CORS 则有助于确保这些请求在浏览器调用堆栈中得到优先处理。

请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

## 安全性 {#section-b176b8492fbe4acfb79ebb30ec902f98}

**ID 服务是否支持 CORS？**

能。请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**什么是 CORS？**

*`Cross-Origin Resource Sharing`*&#x200B;或 CORS 是浏览器用来请求资源的一种方法。在支持 CORS 的浏览器中，ID 服务将始终使用 CORS 来请求资源。在不支持 CORS 的旧版浏览器中，ID 服务将使用 JSON-P 来请求资源。请参阅 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**如果我的安全要求很严格，以至于我从未想要使用 JSONP，该怎么办？**

如果您的安全要求很严格，请将 ID 服务 API 配置设置为 `useCORSOnly: true`。只有在您确信网站访客使用的是支持 CORS 的浏览器时，才应启用此模式。

请参阅 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) 和 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

>[!MORELIKETHIS]
>
>* [客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)

