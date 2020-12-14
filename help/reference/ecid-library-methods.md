---
title: Safari ITP 中的 ECID 库方法
seo-title: Safari ITP 中的 ECID 库方法
description: 适用于 Adobe ECID（ID 服务）库的文档。
seo-description: 适用于 Adobe ECID（ID 服务）库的文档。
translation-type: tm+mt
source-git-commit: 012bf5db473b37b17e7af957c08da71b253c718f
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 72%

---


# Safari ITP 中的 ECID 库方法

>[!NOTE]
>
>已进行更新，以反映2020年11月12日作为Big Sur OS版本的一部分发布的对ITP的最新更改。

由于 Safari 通过 ITP 加强了跨域跟踪，因此 Adobe 必须在支持客户的库以及消费者隐私和选择方面继续使用相应的最佳实践。

自2020年11月10日起，通过文档.cookie API设置的所有第一方永久Cookie（通常称为“客户端”Cookie），以及通过Safari和移动iOS浏览器中的第一方CNAME实施设置的Cookie的过期限制为七天。 如先前版本的ITP中所述，第三方cookie将继续被阻止。 有关 ITP 2.1 以及 Adobe 解决方案影响的更多详细信息，请阅读 [Safari ITP 2.1 对 Adobe Experience Cloud 和 Experience Platform 客户的影响](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)。

## ITP相关更改、方法和配置

由于已为 Safari 中的跟踪创建其他方法，因此，它们将被作为参考内容添加为此页面。

>[!NOTE]
>
>*在下面的所有文档中，ECID* = *MID* = *MCID*。

请参阅下文，了解与 ITP 和 ECID 库使用相关的事项。

## ITP和Apple WebKit的当前ECID库行为

ITP 2.1 会减弱写入客户端 Cookie 的能力，进而会削弱向客户提供准确访客跟踪信息的能力。因此，在Adobe的CNAME跟踪服务器中引入了一项更改，以将访客的Experience CloudID(ECID)存储在第一方cookie中。

此更改仅对在第一方环境中使用 Analytics CNAME 的 ECID 客户有益。即使您是当前未使用 CNAME 的 Analytics 客户或者甚至不是 Analytics 客户，您仍可以查看 CNAME 记录。请联系客户关怀团队或您的客户代表，以开始注册 [CNAME](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/ec-cookies/cookies-first-party.html) 的过程。

升级到 ECID 库版本 4.3.0 及更高版本以利用此更改。

以下概述了ECID库在ITP 2.1中的行为方式，以及Apple作为Big Sur发行版的一部分所做的最新更改

**设计**

向 demdex.net 发出 ID 请求并检索到 ECID 后，如果在您的 ECID 库中设置了跟踪服务器，则会向客户所在的域发出 ID 请求。此端点会从查询字符串中读取 ecid 参数，并设置一个新的 [Cookie](/help/introduction/cookies.md)，该 Cookie 将仅包含 ECID，并会在两年后过期。每次以这种方式调用此端点时，`s_ecid` Cookie 将进行重写，并且有效其为此调用开始后的两年。需要将 ECID 库更新到 v 4.3.0，以便可以检索此 Cookie 的值。

>[!IMPORTANT]
>
>作为Big Sur更新的一部分，通 `s_ecid` 过CNAME设置的Cookie也将持续7天。

此新 `s_ecid` Cookie 采用与 AMCV Cookie 相同的选择退出状态。如果从 `s_ecid` Cookie 读取 ecid，则系统始终会立即调用 demdex 以检索该 ID 的最新选择退出状态并将其存储在 AMCV Cookie 中。

此外，如果您的消费者已通过此[方法](https://docs.adobe.com/content/help/zh-Hans/analytics/implementation/js/opt-out.html)选择退出 Analytics 跟踪，则此 `s_ecid` Cookie 将被删除。

The tracking server name should be supplied to the VisitorJS library when initializing the library using `trackingServer` or `trackingServerSecure`. This should match the `trackingServer` config in the Analytics configs.

If you choose not to take advantage of this method, add the following config to your ECID library implementation: `discardtrackingServerECID`. 当此配置设置为true时，访客库不读取由第一方跟踪服务器设置的MID。

![](assets/itp-proposal-v1.png)

## 使用 appendVisitorIDsTo 方法进行跨域跟踪（在您自己公司的多个域中）

通过此函数，在浏览器阻止第三方 Cookie 时，您可以跨域共享访客的 ECID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。该函数可在 VisitorAPI.js 1.7.0 或更高版本中使用（但不可在 1.10.0 版本中使用）。

**设计**

* 当访客浏览您的其他域时，Visitor.appendVisitorIDsTo(url) 会返回一个 URL，其中包含作为查询参数附加的 ECID。

   使用此 URL 可以从原始域重定向到目标域。

* 目标域上的 ID 服务代码会从 URL 中提取 ECID，而不是向 Adobe 发送请求以获取该访客的 ID。

   此请求包含第三方 Cookie ID，而该 ID 在这种情况下不可用。

* 目标页面上的 ID 服务代码使用传入的 ECID 跟踪访客。

   >[!NOTE]
   >如果目标页面已经具有来自先前访问的 ECID，则此配置 overwriteCrossDomainMCIDAndAID 将控制是否覆盖现有 Cookie。有关此配置的详细信息，请参阅 [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md)。
   >
   >有关此方法的更多详细信息，请参阅 [appendVisitorIDsTo（跨域跟踪）](/help/library/get-set/appendvisitorid.md)参考页。
