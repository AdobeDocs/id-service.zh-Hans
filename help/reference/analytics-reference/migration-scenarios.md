---
description: 包含服务器示例配置和必需的迁移步骤。
keywords: ID 服务
title: Experience Cloud Identity 服务迁移方案
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 94%

---

# Experience Cloud Identity 服务迁移方案 {#experience-cloud-id-service-migration-scenarios}

包含服务器示例配置和必需的迁移步骤。

## 单个Web属性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客户**：Example Company Inc.
* **是否启用 Experience Cloud**：否
* **Web 属性**：example.com
* **数据收集服务器**：metrics.example.com、smetrics.example.com
* **Analytics JavaScript 文件**：所有网站页面只有一个文件

首先，该客户应该启用 Experience Cloud（请参阅[要求](../../reference/requirements.md)）。而且，由于它们只有一个 JavaScript 文件，因此该客户不需要设置宽限期。该客户还将设置访客迁移，然后从其数据收集 CNAME 迁移到别处（此操作没有必要）。

## 多个JavaScript文件、硬编码的图像标签 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客户**：Another Example Company Inc.
* **是否启用 Experience Cloud**：是
* **Web 属性**：anotherexample.com
* **数据收集服务器**：anotherexampleco.112.2o7.net
* **Analytics JavaScript 文件**：多个 JavaScript 文件。主网站有一个文件，在单独 CMS 中维护的支持部分有一个文件。
* **其他数据收集方法**：一个网站部分中的硬编码图像标签

首先，该客户应该查找他们的 Adobe Experience Cloud 组织 ID（请参阅[要求](../../reference/requirements.md)）。接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。此外，这位客户还应设置访客迁移，然后从 `*.2o7.net` 迁移到 `*.sc.omtrdc.net`。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也将更新所有硬编码的图像标签以改为使用 JavaScript。

## 多个Web资产、多个JavaScript文件和一个基于Flash的视频播放器 {#section-34647995ff3740b999fdee22d885e515}

* **客户**：A Good Customer LLC
* **是否启用 Experience Cloud**：是
* **Web 属性**：mymainsite.com、myothersiteA.com、myothersiteB.com
* **数据收集服务器**：metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript 文件**：多个 JavaScript 文件。每个 Web 属性有一个文件。
* **其他数据收集方法**：一个基于 Flash 的视频播放器

首先，该客户应该查找他们的 Adobe Experience Cloud 组织 ID（请参阅[要求](../../reference/requirements.md)）。接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。该客户会在其主域和子域之间跟踪访客，以便他们继续将其数据收集 CNAME 与访客 ID 服务配合使用。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也会将其基于 Flash 的视频播放器更新至最新的 AppMeasurement for Flash 版本。
