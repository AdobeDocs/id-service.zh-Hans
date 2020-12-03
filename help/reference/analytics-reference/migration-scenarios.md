---
description: 包含服务器示例配置和必需的迁移步骤。
keywords: ID Service
seo-description: 包含服务器示例配置和必需的迁移步骤。
seo-title: Experience Cloud Identity 服务迁移方案
title: Experience Cloud Identity 服务迁移方案
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 46%

---


# Experience Cloud Identity 服务迁移方案{#experience-cloud-id-service-migration-scenarios}

包含服务器示例配置和必需的迁移步骤。

## 单个 Web 属性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客户**：Example Company Inc.
* **Experience Cloud已启用**:否
* **Web属性**:example.com
* **数据收集服务器**:metrics.example.com、smetrics.example.com
* **分析JavaScript文件**:适用于所有站点页面的单个文件

首先，应启用此Experience Cloud(请参阅 [要求](../../reference/requirements.md))。 而且，由于他们有一个JavaScript文件，因此此客户不需要宽限期。 此客户还将设置访客迁移，然后从其数据收集CNAME迁移，这是不必要的。

## 多个 JavaScript 文件、硬编码的图像标签 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客户**：Another Example Company Inc.
* **Experience Cloud已启用**:是
* **Web属性**:anotherexample.com
* **数据收集服务器**:anotherexampleco.112.2o7.net
* **分析JavaScript文件**:多个JavaScript文件。 一个用于其主站点的文件，另一个用于其支持部分的文件，在单独的CMS中进行维护。
* **其他数据收集方法**:一个站点部分上的硬编码图像标记

首先，此客户应找到其Adobe Experience Cloud组织ID(请参阅 [要求](../../reference/requirements.md))。 接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。此外，这位客户还应设置访客迁移，然后从 `*.2o7.net` 迁移到 `*.sc.omtrdc.net`。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也将更新所有硬编码的图像标签以改为使用 JavaScript。

## 多个 Web 属性、多个 JavaScript 文件和一个基于 Flash 的视频播放器 {#section-34647995ff3740b999fdee22d885e515}

* **客户**：A Good Customer LLC
* **Experience Cloud已启用**:是
* **Web属性**:mymainsite.com、myothersiteA.com、myothersiteB.com
* **数据收集服务器**:metrics.mymainsite.com、smetrics.mymainsite.com
* **分析JavaScript文件**:多个JavaScript文件。 每个Web属性一个文件。
* **其他数据收集方法**:基于Flash的视频播放器

首先，此客户应找到其Adobe Experience Cloud组织ID(请参阅 [要求](../../reference/requirements.md))。 接下来，他们应当配置一个迁移宽限期，因为他们当前使用了多个 JavaScript 文件。此客户跟踪其主域与子域之间的访客，因此他们将继续将其数据收集CNAME与访客ID服务一起使用。

当这位客户更新至最新的 Analytics JavaScript 代码以便为使用 [!DNL Experience Cloud] ID 服务做准备时，他同时也会将其基于 Flash 的视频播放器更新至最新的 AppMeasurement for Flash 版本。
