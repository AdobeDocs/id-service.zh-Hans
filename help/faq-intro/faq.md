---
description: 与使用 ID 服务相关的特性、功能和问题的常见问题解答。
keywords: ID Service
seo-description: 与使用 ID 服务相关的特性、功能和问题的常见问题解答。
seo-title: ID 服务常见问题解答
title: ID 服务常见问题解答
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# ID 服务常见问题解答{#id-service-faqs}

与使用 ID 服务相关的特性、功能和问题的常见问题解答。

## 功能 {#section-659e89f8b9a74cb8afff35587dc96836}

**ID服务提供哪些功能或功能？**

请参阅 [概述](../introduction/overview.md)。

**为什么ID服务不发出调用以检索Experience Cloud ID?**

这可能很难诊断。 您可以检查站点上的内容安全策略标头。 如果您有严格的安全策略，这些设置可以阻止ID服务发出的第三方调用。 See [Content Security Policies and the Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**VisitorAPI.js文件存储**

如果将VisitorAPI.js作为移动应用程序中的本地文件托管，您可能会遇到问题。 我们建议您将文件托管在Web服务器上。

## 页面加载时间和滞后 {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**ID 服务 VisitorAPI.js 库的位置对页面加载时间有何影响？**

请将 VisitorAPI.js 库放置在页面顶部代码的 `<head>` 部分中。这有助于确保 ID 调用在页面主体开始加载之前发出，并最大限度地增加 ID 成功返回的可能性。

The ID service call is asynchronous and is the only call to the [demdex.net domain](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/reference/demdex-calls.html). ID 服务调用不会阻止在页面上加载其他元素。

对于 [!DNL Target] 客户，将 ID 服务代码放置在页面的 `<body>` 中，可能会增加它阻止 [!DNL Target] 调用的可能性。如果必须将 ID 服务代码放置在页面主体中，则应将其放置在 `<body>` 开始标记的后面。

**ID服务是否在每次加载页面时进行服务器调用？**

否，此呼叫将仅在页面首次呈现时进行，之后每7天进行一次。 同时，不需要服务器调用。 ID服务在客户端模式下运行，无需进行服务器调用即可返回ID。

See [Overview](../introduction/overview.md).

**使用ID服务时，哪些因素会导致页面加载时间变慢或影响用户体验？**

很难对所有可能的条件进行分类。 数以亿计的消费者客户连接到我们的服务，以及它们连接到何处以及如何影响性能的巨大多样性。 例如：

* 移动网络上的速度差异很大。 这些网络还遭受信号和数据或语音包丢失。
* 在多种情况下，通过WiFi连接的设备上存在连接问题。 例如，数据包丢失和速度问题在咖啡馆等公共场所或飞机等其他环境很常见，在这些地方，数据包在到达地面网络之前必须通过卫星弹回。
* 配置不当的本地网络可能会对连接和速度产生负面影响。
* 客户端设备可能有其自身的问题，如内存不足、磁盘交换过多或与当前工作负载相比CPU功率有限。
* 浏览器根据浏览器制造商和版本排队和执行远程服务器调用，甚至使用不同的规则处理响应。 此行为影响速度和性能。

**能否列举您为缩短页面加载时间而做的一些改进？**

例如，线程生成。 我们引入了在多个ID同步请求时进行线程转换。 我们从实验室报告中发现，对于执行多个ID同步的客户，UI将因为发生大量连续CPU计算而被阻止。 因此，我们引入了线程屈服，将ID同步请求分离100毫秒。

此更改为使用访客2.3.0+和DIL 6.10+的客户改进了性能。 页面加载时间的改进显示在下图中：

![](assets/id_sync_improvements_copy.png)

**使用CORS与JSON-P的浏览器请求是否会影响页面性能？**

通常，使用CORS的资源请求比使用JSONP的资源请求更好。 使用JSONP，某些浏览器会排队请求，并取消优先级，使其相对于页面上的其他同步和异步调用。 CORS有助于确保在浏览器调用堆栈中以更高的优先级处理这些请求。

请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

## 安全性 {#section-b176b8492fbe4acfb79ebb30ec902f98}

**ID服务是否支持CORS?**

能。请参阅 [Experience Cloud Identity 服务中的 CORS 支持](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**什么是 CORS？**

*`Cross-Origin Resource Sharing`*&#x200B;或 CORS 是浏览器用来请求资源的一种方法。在支持ID的浏览器中，ID服务始终使用CORS请求资源。 ID服务在不支持CORS的旧版浏览器中使用JSON-P请求资源。 请参阅 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**如果我的安全要求很严格，以至于我从未想要使用 JSONP，该怎么办？**

如果您的安全要求很严格，请将 ID 服务 API 配置设置为 `useCORSOnly: true`。只有在您确信您的站点访客使用支持CORS的浏览器时，才应启用此模式。

See [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) and [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)

