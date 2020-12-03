---
title: 在用户同意的基础上使用选择加入控制 Experience Cloud 活动
description: Adobe 选择加入对象是 Adobe Experience Platform Identity Service 的扩展，旨在帮助您在最终用户同意的基础上，控制 Experience Cloud 解决方案是否可以在网页上创建 Cookie 或启动信标以及哪些 Experience Cloud 解决方案可以执行此类操作。
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---


# 在用户同意的基础上控制 Experience Cloud 活动

Adobe [!UICONTROL 选择加入]对象是 Adobe [!UICONTROL Experience Platform Identity Service] 的扩展，旨在帮助您在最终用户同意的基础上，控制 Experience Cloud 解决方案是否可以在网页上创建 Cookie 或启动信标以及哪些 Experience Cloud 解决方案可以执行此类操作。

## [!UICONTROL 选择加入]的基础知识

针对个人数据的使用方式和使用者获取和传达用户同意，是隐私条例的一个重要方面。最新版本的 [!UICONTROL Identity Service] 包含的功能着眼于用户 (UI) 和 Adobe 解决方案之间，并根据最终用户是否同意，为 Adobe Experience Cloud 解决方案标记提供条件触发（例如，预先同意和后期同意）。下图显示了该服务：

![[!UICONTROL 选择加入]工作流程示意图](assets/opt-in.png)

[!UICONTROL 选择加入]本质上是守门员...还是密钥管理员？由您决定。

总的来说即为：

**如果在 Identity Service 中启用了[!UICONTROL 选择加入]（通过布尔变量），那么 Experience Cloud 解决方案库会延迟触发标记或设置 Cookie，直到获得对该解决方案的同意为止。**

[!UICONTROL 选择加入]还允许您确定是否在用户同意&#x200B;*之前*&#x200B;触发任何标记，然后存储此同意信息（以及最终用户提供的同意信息），以便在后续的点击中可以使用。同意信息可存储在[!UICONTROL 选择加入]选项中，也可以与 CMP 集成并使其存储同意选项。

## 启用并配置[!UICONTROL 选择加入]

[!UICONTROL 选择加入]也可以通过 Adobe Experience Platform Launch 轻松配置。请查看以下简短视频，了解具体配置方法。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您未使用 Experience Platform Launch，则可以在全局访客对象的初始化中设置[!UICONTROL 选择加入]配置，如该[文档](https://marketing.adobe.com/resources/help/zh_CN/mcvid/getting-started.html)中所述。

## 在页面上实施[!UICONTROL 选择加入]

所有这些设置和后端操作都只是准备工作，目的是为网站访客提供一个可以展示同意选项的界面。您可以自行构建此 UI，也可以与 CMP（同意管理平台）合作来创建此 UI。

在设置 UI 以使用[!UICONTROL 选择加入]来收集同意时，应该将其配置为调用一些 API，这些 API 会挂接到[!UICONTROL 选择加入]，并通知它针对部分或所有 Adobe Experience Cloud 解决方案给出同意选项。有关这些 API 的详细信息，请参阅[选择加入参考文档](https://marketing.adobe.com/resources/help/zh_CN/mcvid/api.html)。周围的文档页面上还提供了有关选择加入的其他信息。

## [!UICONTROL 选择加入]演示

请在以下视频中，观看[!UICONTROL 选择加入]在页面上运作的快速演示，以及它对 Experience Cloud 解决方案是否可以设置 Cookies、启动信标等将会产生何种影响。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：**&#x200B;请务必注意，在撰写本文时，尚未将[!UICONTROL 选择加入]内置到所有 Experience Cloud 解决方案的库中。当前支持[!UICONTROL 选择加入]的库包括：

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
