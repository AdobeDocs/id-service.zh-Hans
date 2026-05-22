---
title: 经用户同意使用选择加入控制 Experience Cloud 活动
description: Adobe 选择加入对象是 Adobe Experience Platform 身份标识服务的扩展，旨在帮助您在最终用户同意的基础上，控制 Experience Cloud 解决方案是否可以在网页上创建 Cookie 或启动信标以及哪些 Experience Cloud 解决方案可以执行此类操作。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 517
ht-degree: 39%

---

# 经用户同意控制 Experience Cloud 活动

Adobe [!UICONTROL Opt-in]对象是Adobe [!UICONTROL Experience Platform Identity Service]的扩展，旨在帮助您根据最终用户同意，控制哪些Experience Cloud解决方案能否在网页上创建Cookie或启动信标。

## [!UICONTROL Opt-In]的基础知识

针对个人数据的使用方式和使用者获取和传达用户同意，是隐私条例的一个重要方面。 最新版本的[!UICONTROL Identity Service]包括可根据是否获得最终用户同意提供Experience Cloud解决方案标记的有条件触发（例如同意前和同意后）的功能。 下图说明了此流程：

![&#x200B; [!UICONTROL Opt-in]的工作原理图](assets/opt-in.png)

[!UICONTROL Opt-in]的工作方式如下：

**如果在Identity Service中启用了[!UICONTROL Opt-in]（通过布尔变量），它会延迟Experience Cloud解决方案库触发标记或设置Cookie，直到获得对该解决方案的同意为止。**

[!UICONTROL Opt-in]还允许您确定是否在用户同意之前触发标记，然后存储此同意信息（以及最终用户提供的同意信息），以便在后续的点击中可以使用。 同意信息可存储在[!UICONTROL Opt-in]选项中，也可以与CMP集成并使其存储同意选项。

## 启用和配置[!UICONTROL Opt-In]

使用Adobe Experience Platform标记（以前称为Launch）配置[!UICONTROL Opt-in]最为轻松。 请观看以下简短视频，了解具体配置方法。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您未使用Experience Platform标记，则可以在全局访客对象的初始化中设置[!UICONTROL Opt-in]的配置，如[文档](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lank=zh-Hans)中所示。

## 在页面上实施[!UICONTROL Opt-In]

所有这些设置和后端操作都只是准备工作，目的是为网站访客提供一个可以展示同意选项的界面。 您可以自行构建此 UI，也可以与 CMP（同意管理平台）合作来创建此 UI。

在设置UI以使用[!UICONTROL Opt-in]来收集同意时，应该将其配置为调用将挂接到[!UICONTROL Opt-in]的API，并通知其同意部分或所有Adobe Experience Cloud解决方案。 有关这些 API 的详细信息，请参阅[选择加入参考文档](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lank=zh-Hans)。 周围的文档页面上还提供了有关选择加入的其他信息。

## [!UICONTROL Opt-In]演示

请在以下视频中，观看[!UICONTROL Opt-in]在页面上的快速演示，以及它对Experience Cloud解决方案是否可以设置Cookie、启动信标等将会产生何种影响。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：**&#x200B;请务必注意，在撰写本文时，[!UICONTROL Opt-in]尚未内置到所有Experience Cloud应用程序的库中。 当前支持[!UICONTROL Opt-in]的库包括：

* 身份标识服务
* Analytics
* Audience Manager
* [!DNL Target]

