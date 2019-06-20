---
description: 概述 ID 请求和响应过程。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
keywords: ID 服务
seo-description: 概述 ID 请求和响应过程。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
seo-title: Experience Cloud ID服务请求的请求和设置ID
title: Experience Cloud ID服务请求的请求和设置ID
uuid: ff7f5b7e-e959-4391-b75 c-b7 a36286 e0 ea
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# How the Experience Cloud ID Service requests and sets IDs{#how-the-experience-cloud-id-service-requests-and-sets-ids}

概述 ID 请求和响应过程。下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。

>[!NOTE]
>
>If you&#39;re not familiar with how the Experience Cloud ID Service creates the visitor ID, take a moment to review [Experience Cloud](../introduction/cookies.md).

**提示：** 另请参阅我们的[关于跨域跟踪的 ID 服务视频](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)。

## 请求 Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

下面的示例演示了 ID 服务如何请求和接收 Experience Cloud 访客 ID。这些示例使用两家虚构公司、食品公司和体育公司展示ID请求和响应的数据流。这两个公司各有一个唯一的 Experience Cloud 组织 ID，并且都已经在其所有网站上实施了 ID 服务代码。这些用例体现了通用 ID 服务（在“没有 Analytics、旧版 ID 或阻止第三方 Cookie 的浏览器”的情况下）实施的数据流。

![](assets/sample_sites.png)

**第一个请求**

在这个示例中，一位新访客来到了由食品公司管理的比萨饼网站。此食品公司在比萨饼网站实施了 ID 服务代码。当加载比萨饼网站时，ID 服务代码将会在比萨饼域中检查 AMCV Cookie。

* 如果设置了 AMCV Cookie，则表明该网站访客拥有 Experience Cloud ID。在这种情况下，Cookie会跟踪访客并与其他Experience Cloud解决方案共享数据。
* 如果未设置 AMCV Cookie，则 ID 服务代码会调用 [ 中的区域](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html)数据收集服务器`dpm.demdex.net/id` (DCS)（另请参阅[了解 Demdex 域调用](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)）。此调用包括食品公司的组织 ID。组织 ID 是在 ID 服务代码的 `Visitor.getInstance` 函数中设置的。

![](assets/request1.png)

**第一个响应**

在响应过程中，DCS 会返回 [!DNL Experience Cloud] ID (MID) 和 Demdex Cookie。ID 服务代码会将 MID 值写入 AMCV Cookie。例如，假定 DCS 返回的 MID 值为 1234。它就会在 AMCV Cookie 中存储为 `mid|1234`，并且将在第一方比萨饼域中设置。Demdex Cookie 还包含一个唯一 ID（我们称之为 5678）。此 Cookie 在第三方 demdex.net 域中设置，该域是与比萨饼域分离的。

![](assets/response1.png)

在下一个示例中您会看到，当我们的访客转至食品公司下属的其他网站时，Demdex ID 和组织 ID 允许 ID 服务创建并返回正确的 MID。

## Cross-site request and response {#section-15ea880453af467abd2874b8b4ed6ee9}

在本示例中，我们的食品公司访客从比萨饼站点导航至炸玉米饼站点。该食品公司在炸玉米饼站点也实施了 ID 服务代码。这位访客从未访问过炸玉米饼网站。

根据这些条件，炸玉米饼站点上没有 AMCV Cookie。而且 ID 服务也不能使用比萨饼站点上设置的 AMCV Cookie，因为该 Cookie 专门用于比萨饼域。因此，ID 服务必须调用 DCS 来检查并请求访客 ID。在这种情况下，DCS 调用包括食品公司的组织 ID *和* Demdex ID。请记住，Demdex ID 取自比萨饼站点，并作为第三方 Cookie 存储在 demdex.net 域中。

![](assets/request2.png)

DCS 收到组织 ID 和 Demdex ID 后，它会为我们的访客创建正确的 MID，并返回其值。因为 是根据组织 ID 和 Demdex ID 通过数学方法计算得到的，因此 AMCV Cookie 包含的 MID 值为 `mid = 1234`mid = 。

![](assets/response2.png)

## ID requests from other sites {#section-ba9a929e50d64b0aba080630fd83b6f1}

在下面的示例中，我们的访客离开食品公司站点，前往体育公司下设的足球站点。当访客来到足球站点时，ID 检查和请求流程会按照上面示例中描述的相同方式运作。然而，因为体育公司有自己的组织 ID，因此 ID 服务会返回一个不同的 MID。新 MID 在由体育公司控制的域中是唯一的，它允许该公司在不同的 [!DNL Experience Cloud] 解决方案中跟踪和共享访客数据。此访客的 Demdex ID 保持不变，因为它包含在第三方 Cookie 中，在其他域中仍然有效。

![](assets/req_resp.png)

