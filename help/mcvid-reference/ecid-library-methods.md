---
title: Safari ITP世界中的EID库方法
seo-title: Safari ITP世界中的EID库方法
description: Adobe EID(ID服务)库的文档。
seo-description: Adobe EID(ID服务)库的文档。
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Safari ITP世界中的EID库方法

Safari通过IDP加强跨域跟踪，Adobe必须维护支持客户以及消费者隐私和选择的库最佳做法。

在2019年月21日，Apple宣布了其最新的ITP更新(智能跟踪预防)。与侧重于第三方cookie的早期版本不同，此版本详细描述了第一方cookie的新跟踪预防措施。通过document. cookie API设置的所有第一方永久性cookie通常称为“客户端”cookies，其过期时间在天内。第三方cookie将继续被阻止，如早期版本的ITP中所述。有关IPP2.1和Adobe解决方案影响的更多详细信息，请阅读 [Safari INP2.1对Adobe Experience Cloud和Experience Platform客户](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)的影响。

## Safari ITP常见问题解答的Adobe EID

**为什么客户的第一方域中由Experience Cloud ID库(EID)设置的AMCV cookie受ITP2.1影响？**

AMCV cookie当前依赖document. cookie API并通过“客户端”设置。Safari偏爱从客户服务器设置的cookie。

**为什么通过CNAME跟踪服务器设置Cookie更好地跟踪Safari？**

ITP的规则是将控制权交给开发人员。通过CNAME证书实现的操作无法通过JavaScript完成。Adobe的CNAME认证计划(服务器端跟踪)与ITP保持一致，多年来一直是Adobe战略的一部分。ECID库正在释放将EID库功能移至CNAME实施的方法。

**当其他Analytics访客跟踪方法目前与CNAME一起使用时，Adobe为何会关注EID库？**

EID库、AMCV cookie和EID(aka MID)开始作为将所有Adobe解决方案集成到一个ID下的方法。此ID将继续是Adobe产品路线图中的优先级Cookie级别ID，是Adobe Experience Platform的默认cookie ID。

**CNAME是否有助于客户启用多域跟踪？**

以前使用CNAME存在的相同规则和警告仍然存在。在某些情况下，CNAME可以在多域场景中帮助。如果您有主要条目站点，在访问其他域之前可以识别用户，则CNAME可以在不接受第三方cookie的浏览器中启用多域跟踪。但是，虽然CNAME可以在某些情况下帮助多个域，但将ECID转换为CNAME的原因是永久性访客识别，而非多域跟踪。有关CNAME和多域的详细信息，请参阅 [数据收集Cames和跨域跟踪](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)。

在发布额外的ITP更改时，将在此处添加更多常见问题解答。有关更多信息，请访问 [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics)。

## 与ITP相关的更改、方法和配置

由于在Safari中创建了其他的跟踪方法，因此它们将添加为对此页面的引用。

>[!NOTE]*EID* = *MID* = *MID=以下* 所有文档中的MID= MID。

请参阅以下与ITP和ECID库使用相关的工作。

## 使用ECID库和CNAME跟踪扩展访客ID过期

ITP2.1阻碍了编写客户端Cookie的能力，这削弱了为客户提供准确访客跟踪信息的能力。因此，在Adobe的CNAME跟踪服务器中引入了一项更改，以将访客的Experience Cloud ID(ECID)存储在第一方cookie中。

此更改仅对在第一方上下文中使用Analytics CNAME的EID客户有用。如果您目前是未使用CNAME的Analytics客户，或者甚至非Analytics客户，您仍有资格获得CNAME记录。请联系客户关怀或您的客户代表，开始注册 [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html)。

升级到ECID库v4.3.0+以利用此更改。

**设计**

对demdex. net发出ID请求并检索一个ECID后，如果在您的ECID库中设置了跟踪服务器，则会对客户的域发出ID请求。此端点从查询字符串读取ecid param，并设置一个新 [cookie，该cookie](/help/mcvid-introduction/mcvid-cookies.md) 只包含EID和将来两年的过期日期。每次以这种方式调用此端点时， `s_ecid` cookie将在调用时的两年有效期内重写。需要将ECID库更新至v4.3.0，以便检索此cookie的值。

此新 `s_ecid` cookie遵循与AMCV cookie相同的选择退出状态。如果从 `s_ecid` cookie读取ecid，则始终调用demdex检索该ID的最新退出状态并存储在AMCV cookie中。

此外，如果您的消费者通过此 [方法](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)退出Analytics跟踪，则此 `s_ecid` cookie将被删除。

使用TrackingServer或TrackingServerSecure初始化库时，应将跟踪服务器名称提供给VisitorJS库。这应与Analytics配置中的TrackingServer配置匹配。

如果您选择不利用此方法，请将以下配置添加到您的ECID库实施：discardTrackingServerECID。当此配置设置为true时，访客库不读取由第一方跟踪服务器设置的MID。

![](assets/itp-proposal-v1.png)

## 使用AppendVisitorIdsto方法进行跨域跟踪(在您自己的公司的多个域中)

通过此函数，当浏览器阻止第三方cookie时，您可以跨域共享访客的ECID。要使用此函数，您必须已实施 ID 服务，并且拥有源域和目标域。在VisitorAPI. js版本1.7.0或更高版本中可用(但不在版本1.10.0中)。

**设计**

* 当访客浏览到其他域时，访客. appendVisitorIDSTo(url)返回一个URL，并将ECID附加为查询参数。

   使用此URL可重定向到目标域的原始域。

* 目标域上的ID服务代码从URL提取ECID，而不是向Adobe发送请求的ID。

   此请求包含第三方 Cookie ID，而该 ID 在这种情况下不可用。

* 目标页面上的ID服务代码使用传入的ECID跟踪访客。

   >[!NOTE]
   >如果目标页面已经有来自以前访问的EID，则覆盖现有cookie的决定由此config OverwriteCrossDomaMIDDandan控制。有关此配置的详细信息，请参阅 [OverwriteCrossDomainMidCand帮助](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)。
   >
   >有关此方法的详细信息，请参阅 [AppendVisitorIdsto(跨域跟踪)](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) 参考页。
