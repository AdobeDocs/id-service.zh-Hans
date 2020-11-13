---
title: 根据用户同意使用选择加入控制Experience Cloud活动
description: Adobe选择加入对象是Adobe Experience Platform标识服务的扩展，旨在帮助您根据最终用户的同意，控制是否以及哪些Experience Cloud解决方案可以在网页上创建cookie或启动信标。
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# 基于用户同意控制Experience Cloud活动

Adobe [!UICONTROL 选择] -加入对象是Adobe Experience Platform标识服务的扩展，旨在帮助您根据最终用户的同意，控制是否以及哪些Experience Cloud解决方案可以在网页上创建cookie或启动信标。

## 选择加入 [!UICONTROL 的基础知识]

隐私法规的一个重要方面是获取和传达用户对个人数据的使用方式和使用者的同意。 最新版本的Identity Service [!UICONTROL 包含功能] ，该功能位于用户(UI)和Adobe解决方案之间，并根据最终用户是否同意提供对Adobe Experience Cloud解决方案标签的条件触发（例如，预先和后置同意）。 如下图所示：

![参与工 [!UICONTROL 作方式图]](assets/opt-in.png)

[!UICONTROL 选择加入] ，基本上就是看门人，还是主键？ 由你决定。

归根到底是：

**如 [!UICONTROL 果在Identity Service] （通过布尔变量）中启用了选择加入，则会延迟Experience Cloud解决方案库触发标签或设置cookie，直到获得该解决方案的同意。**

[!UICONTROL 选择加入] 还允许您在用户同意 *前* ，确定是否还有任何标记触发，然后存储此同意信息（连同最终用户的同意），以便在后续点击中使用它。 同意存储可在选择加入 [!UICONTROL 选项中] ，也可以与CMP集成并让其存储同意选择。

## 启用和配 [!UICONTROL 置选择加入]

[!UICONTROL 选择加入] ，也可以通过Adobe Experience Platform Launch轻松配置。 视图以下简短视频，了解具体方法。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您未使用Experience Platform Launch，则可 [!UICONTROL 以在全局]对象的初始化中设置访客的选择加入 [配置](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)。

## 在 [!UICONTROL 页面上实施] “选择加入”

所有这些设置和后端内容都只是为提供一个界面以向站点访客显示同意选项做准备。 此UI可以由您构建，也可以使用CMP（同意管理平台）合作伙伴创建UI。

在设置UI以使用 [!UICONTROL 加入] (Opt-in)收集同意时，应将其配置为调用将加入加入选择加入( [!UICONTROL Opt-in] )的API并通知它同意部分或所有Adobe Experience Cloud解决方案。 有关这些API的详细信息，请参 [阅参考文档](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)。 有关选择加入的其他信息也请参阅周围的文档页面。

## [!UICONTROL 选择加入演示] (Opt-In Demo)

在以下视频中，请观看页面 [!UICONTROL 上参与工作] 的快速演示，以及它如何影响Experience Cloud解决方案是否可以设置cookies、启动信标等。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** 必须指出，在本文撰写时，尚 [!UICONTROL 未将Opt] -in内置到所有Experience Cloud解决方案的库中。 当前支持加入 [!UICONTROL 的库] :

* 标识服务
* Analytics
* Audience Manager
* [!DNL Target]
