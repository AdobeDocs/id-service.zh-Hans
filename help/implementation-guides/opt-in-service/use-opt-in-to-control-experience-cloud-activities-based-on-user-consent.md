---
title: 在用户同意的基础上使用选择加入控制 Experience Cloud 活动
description: Adobe选择加入对象是Adobe Experience Platform Identity Service的扩展，旨在帮助您在最终用户同意的基础上，控制Experience Cloud解决方案是否可以在网页上创建Cookie或启动信标以及哪些Cookie解决方案可以执行此类操作。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# 在用户同意的基础上控制 Experience Cloud 活动

Adobe [!UICONTROL 选择加入] 对象是Adobe的扩展 [!UICONTROL Experience Platform标识服务]，旨在帮助您在最终用户同意的基础上，控制Experience Cloud解决方案是否可以在网页上创建cookie或启动信标以及哪些Cookie解决方案可以执行此类操作。

## [!UICONTROL 选择加入]的基础知识

针对个人数据的使用方式和使用者获取和传达用户同意，是隐私条例的一个重要方面。的最新版本 [!UICONTROL Identity Service] 包括根据最终用户是否同意，为Experience Cloud解决方案标记提供条件触发（例如，预先同意和后期同意）的功能。 此过程如下图所示：

![[!UICONTROL 选择加入]工作流程示意图](assets/opt-in.png)

[!UICONTROL 选择加入] 如下所示：

**如果在 Identity Service 中启用了[!UICONTROL 选择加入]（通过布尔变量），那么 Experience Cloud 解决方案库会延迟触发标记或设置 Cookie，直到获得对该解决方案的同意为止。**

[!UICONTROL 选择加入] 还允许您确定标记是否在用户同意前触发，然后存储此同意信息（以及最终用户提供的同意信息），以便在后续点击中使用。 同意信息可存储在[!UICONTROL 选择加入]选项中，也可以与 CMP 集成并使其存储同意选项。

## 启用并配置[!UICONTROL 选择加入]

[!UICONTROL 选择加入] 可以通过Adobe Experience Platform标记（以前称为Launch）轻松配置。 请查看以下简短视频，了解具体配置方法。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果不使用Experience Platform标记，则可以设置 [!UICONTROL 选择加入]初始化全局访客对象时的配置，如 [文档](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## 在页面上实施[!UICONTROL 选择加入]

所有这些设置和后端操作都只是准备工作，目的是为网站访客提供一个可以展示同意选项的界面。您可以自行构建此 UI，也可以与 CMP（同意管理平台）合作来创建此 UI。

在设置 UI 以使用[!UICONTROL 选择加入]来收集同意时，应该将其配置为调用一些 API，这些 API 会挂接到[!UICONTROL 选择加入]，并通知它针对部分或所有 Adobe Experience Cloud 解决方案给出同意选项。有关这些 API 的详细信息，请参阅[选择加入参考文档](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en)。周围的文档页面上还提供了有关选择加入的其他信息。

## [!UICONTROL 选择加入]演示

在以下视频中，观看 [!UICONTROL 选择加入] 处理页面，以及它对Experience Cloud解决方案是否可以设置cookie、启动信标等将产生何种影响。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** 必须指出，在编写本条时， [!UICONTROL 选择加入] 尚未内置到所有Experience Cloud应用程序的库中。 当前支持[!UICONTROL 选择加入]的库包括：

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
