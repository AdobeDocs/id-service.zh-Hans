---
description: ID请求和响应过程的概述。 下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
keywords: ID Service
seo-description: ID请求和响应过程的概述。 下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。
seo-title: Experience Cloud Identity 服务如何请求和设置 ID
title: Experience Cloud Identity 服务如何请求和设置 ID
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity 服务如何请求和设置 ID{#how-the-experience-cloud-id-service-requests-and-sets-ids}

ID请求和响应过程的概述。 下面的示例涵盖了各种网站类型中的 ID 分配情况：单独的网站上、不同的网站之间，以及由 Experience Cloud 不同客户使用其各自组织 ID 管理的网站。

>[!NOTE]
>
>如果您不熟悉 Experience Cloud Identity 服务如何创建访客 ID，请花些时间查阅 [Experience Cloud](../introduction/cookies.md)。

**提示：** 另请观看我 [们的跨域跟踪ID服务视频](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)。

## 请求 Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

下面的示例演示了 ID 服务如何请求和接收 Experience Cloud 访客 ID。这些示例使用了两个虚构的公司（食品公司和体育公司）来演示 ID 请求和响应的数据流。每个公司都有一个唯一的Experience Cloud组织ID，并已在其所有网站上实施了ID服务代码。 这些用例体现了通用 ID 服务（在“没有 Analytics、旧版 ID 或阻止第三方 Cookie 的浏览器”的情况下）实施的数据流。

![](assets/sample_sites.png)

**第一次请求**

在此示例中，新访客来到由“食品”公司管理的比萨饼站点。 食品公司在比萨饼网站上有ID服务代码。 加载比萨饼站点时，ID服务代码会检查比萨饼域中的AMCV cookie。

* 如果设置了AMCV cookie，则站点访客具有Experience Cloud ID。 在这种情况下，Cookie 会跟踪访客并与其他 Experience Cloud 解决方案共享数据。
* If the AMCV cookie is not set, the ID service code calls a regional [data collection server](https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html) (DCS) at `dpm.demdex.net/id` (see also, [Understanding Calls to the Demdex Domain](https://docs.adobe.com/content/help/zh-Hans/audience-manager/user-guide/reference/demdex-calls.html)). 此调用包括食品公司的组织 ID。组织 ID 是在 ID 服务代码的 `Visitor.getInstance` 函数中设置的。

![](assets/request1.png)

**第一次响应**

在响应过程中，DCS 会返回 [!DNL Experience Cloud] ID (MID) 和 Demdex Cookie。ID服务代码将MID值写入AMCV cookie。 例如，假设DCS返回MID值1234。 它就会在 AMCV Cookie 中存储为 `mid|1234`，并且将在第一方比萨饼域中设置。demdex cookie还包含一个唯一ID（我们称之为5678）。 此Cookie在第三方demdex.net域中设置，该域与Pizza域分开。

![](assets/response1.png)

正如您在下一个示例中所看到的，当我们的访客移动到属于食品公司的其他站点时，demdex ID和组织ID允许ID服务创建并返回正确的MID。

## 跨站点请求和响应 {#section-15ea880453af467abd2874b8b4ed6ee9}

在此示例中，我们的食品公司访客导航到比萨饼站点中的玉米饼站点。 食品公司在玉米卷网站上有ID服务代码。 访客从来没去过玉米卷网站。

鉴于这些条件，玉米卷站点上没有AMCV cookie。 而且，ID服务无法使用在比萨饼站点上设置的AMCV cookie，因为它特定于比萨饼域。 因此，ID服务必须调用DCS来检查并请求访客ID。 在这种情况下，DCS调用包括食品公司的组织 *ID* 和demdex ID。 请记住，demdex ID是从比萨饼站点上提取的，并作为第三方cookie存储在demdex.net域下。

![](assets/request2.png)

在DCS收到组织ID和demdex ID后，它会为我们的站点访客创建并返回正确的MID。 因为 是根据组织 ID 和 Demdex ID 通过数学方法计算得到的，因此 AMCV Cookie 包含的 MID 值为 `mid = 1234`mid = 。

![](assets/response2.png)

## 来自其他网站的 ID 请求 {#section-ba9a929e50d64b0aba080630fd83b6f1}

在此示例中，我们的访客离开食品公司站点并导航到体育公司拥有的足球站点。 当访客到达足球场时，ID检查和请求过程的工作方式与前面示例中所述相同。 但是，由于体育公司有其自己的组织ID，因此ID服务返回不同的MID。 新 MID 在由体育公司控制的域中是唯一的，它允许该公司在不同的 [!DNL Experience Cloud] 解决方案中跟踪和共享访客数据。此访客的 Demdex ID 保持不变，因为它包含在第三方 Cookie 中，在其他域中仍然有效。

![](assets/req_resp.png)

