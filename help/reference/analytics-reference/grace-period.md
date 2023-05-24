---
description: 如果有多个 JavaScript 文件要将数据发送至同一报表包，或者您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。
keywords: ID 服务
title: ID 服务宽限期
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# ID 服务宽限期 {#the-id-service-grace-period}

如果有多个 JavaScript 文件要将数据发送至同一报表包，或者您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。

在您部署 [!DNL Experience Cloud] ID 服务后，新的访客将不再从您的数据收集服务器中接收 Analytics 访客 ID。如果您网站的某些部分尚未实施 [!DNL Experience Cloud] ID 服务，那么当访客浏览这些部分时，将无法识别 Experience Cloud ID，与此同时，分配给访客的会是一个旧版 Analytics 访客 ID。这可能会导致访客计数重复以及不正确的归因。

例如，如果网站的支持部分是在单独的 CMS 中管理的，则此部分可能有不同的 Analytics JavaScript 文件。如果您在将访客 ID 服务部署到支持网站之前，在主要网站上部署了访客 ID，则新访客在访问支持部分时会收到一个旧版 Analytics ID，而且跨两个网站区域的访问都将会报告为不同的访问。

在使用多个 JavaScript 文件或其他技术（例如 Flash）的网站上部署 [!DNL Experience Cloud] ID 服务时，可能会导致协调问题，因为您需要同时对网站的所有部分都启用 ID 服务。通过配置一个宽限期，新的访客可以继续从 [!DNL Experience Cloud] ID 服务中接收 Analytics 访客 ID，这样对于网站中没有升级为使用 ID 服务的部分而言，也可以始终如一地识别访客。

>[!NOTE]
>
>要实现宽限期支持，必须安装 [!DNL Experience Cloud] ID 服务版本 1.3 或更高版本。

## 我需要设置宽限期吗？ {#section-fd34c7ff697348a39f49258b7d39eb42}

如果您只有一个 Analytics JavaScript 文件并且未使用任何其他 AppMeasurement 库，则不需要设置宽限期。您可以在一个 JavaScript 文件中进行更新，系统会在访问期间使用 Marketing Cloud ID 以一致方式识别新访客。

如果有多个 JavaScript 文件要将数据发送至&#x200B;*同一报表包*，或者您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。

## 我该如何启用宽限期？ {#section-512d5cd8570e483cbdd8b04457a16ced}

联系[客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html)。
