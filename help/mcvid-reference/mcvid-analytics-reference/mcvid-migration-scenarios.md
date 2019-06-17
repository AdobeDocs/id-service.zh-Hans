---
description: 包含服务器示例配置和必需的迁移步骤。
keywords: ID 服务
seo-description: 包含服务器示例配置和必需的迁移步骤。
seo-title: Experience Cloud ID 服务迁移方案
title: Experience Cloud ID 服务迁移方案
uuid: e229045-6508-48c4ae39-9537b4941853
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID 服务迁移方案 {#experience-cloud-id-service-migration-scenarios}

包含服务器示例配置和必需的迁移步骤。

## 单个 Web 属性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客户**：Example Company Inc.
* **启用 Experience Cloud**：否
* **Web 属性**：example.com
* **数据收集服务器**：metrics.example.com、smetrics.example.com
* **Analytics JavaScript 文件**：所有网站页面使用一个文件

首先，这位客户应当启用 Experience Cloud（请参阅[要求](../../mcvid-reference/mcvid-requirements.md)）。另外，由于它们具有单个 JavaScript 文件，因此该客户不需要宽限期。这位客户还应设置访客迁移，然后从其使用 CNAME 的数据收集中迁移出来（因为不再需要 CNAME）。

## 多个 JavaScript 文件、硬编码的图像标签 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客户**：Another Example Company Inc.
* **启用 Experience Cloud**：是
* **Web 属性**：anotherexample.com
* **数据收集服务器**：anotherexampleco.112.2o7.net
* **Analytics JavaScript 文件**：多个 JavaScript 文件。一个文件用于其主网站，另一个文件用于其在单独 CMS 中维护的支持部分。
* **其他数据收集方法**：在某个网站部分中使用了硬编码的图像标签

首先，这位客户应当查找其 Adobe Experience Cloud 组织 ID（请参阅[要求](../../mcvid-reference/mcvid-requirements.md)）。接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。此客户还将设置访客迁移，然后从 `*.2o7.net` 迁移到 `*.sc.omtrdc.net`迁移。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也将更新所有硬编码的图像标签以改为使用 JavaScript。

## 多个 Web 属性、多个 JavaScript 文件和一个基于 Flash 的视频播放器 {#section-34647995ff3740b999fdee22d885e515}

* **客户**：A Good Customer LLC
* **启用 Experience Cloud**：是
* **Web 属性**：mymainsite.com、myothersiteA.com、myothersiteB.com
* **数据收集服务器**：metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript 文件**：多个 JavaScript 文件。每个文件对应于一个 Web 属性。
* **其他数据收集方法**：基于 Flash 的视频播放器

首先，这位客户应当查找其 Adobe Experience Cloud 组织 ID（请参阅[要求](../../mcvid-reference/mcvid-requirements.md)）。接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。这位客户跟踪主域和子域之间的访客，因此他们将继续在访客 ID 服务中使用数据收集 CNAME。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也会将其基于 Flash 的视频播放器更新至最新的 AppMeasurement for Flash 版本。
