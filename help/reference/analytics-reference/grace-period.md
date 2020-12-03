---
description: 如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。
keywords: ID Service
seo-description: 如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。
seo-title: ID 服务宽限期
title: ID 服务宽限期
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 66%

---


# ID 服务宽限期 {#the-id-service-grace-period}

如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。

在您部署 [!DNL Experience Cloud] ID 服务后，新的访客将不再从您的数据收集服务器中接收 Analytics 访客 ID。如果您网站的某些部分尚未实施 [!DNL Experience Cloud] ID 服务，那么当访客浏览这些部分时，将无法识别 Experience Cloud ID，与此同时，分配给访客的会是一个旧版 Analytics 访客 ID。这会创建重复的访问计数和不正确的归因。

例如，如果网站的支持部分是在单独的 CMS 中管理的，则此部分可能有不同的 Analytics JavaScript 文件。如果您在将访客ID服务部署到支持站点之前在主站点上部署访客ID，新访客在访问支持部分时将收到旧版Analytics ID，并且跨两个站点部分的访问将报告为不同的访问。

在使用多个 JavaScript 文件或其他技术（例如 Flash）的网站上部署 [!DNL Experience Cloud] ID 服务时，可能会导致协调问题，因为您需要同时对网站的所有部分都启用 ID 服务。通过配置一个宽限期，新的访客可以继续从 [!DNL Experience Cloud] ID 服务中接收 Analytics 访客 ID，这样对于网站中没有升级为使用 ID 服务的部分而言，也可以始终如一地识别访客。

>[!NOTE]
>
>要实现宽限期支持，必须安装 [!DNL Experience Cloud] ID 服务版本 1.3 或更高版本。

## 我需要设置宽限期吗？{#section-fd34c7ff697348a39f49258b7d39eb42}

如果您有一个Analytics JavaScript文件，并且没有使用任何其他AppMeasurement库，则无需宽限期。 您可以在单个JavaScript文件中进行更新，并在访问过程中使用marketing cloud ID一致地识别新访客。

If you have multiple JavaScript files that are sending data to the *same report suite*, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.

## 如何启用宽限期？ {#section-512d5cd8570e483cbdd8b04457a16ced}

Contact [Customer Care](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html).
