---
description: 如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。
keywords: ID 服务
seo-description: 如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。
seo-title: ID 服务宽限期
title: ID 服务宽限期
uuid: 10a7db7d-de32-4379-914f-edfear929 ea32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# ID 服务宽限期 {#the-id-service-grace-period}

如果有多个 JavaScript 文件要将数据发送至同一报表包，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。

在您部署 [!DNL Experience Cloud] ID 服务后，新的访客将不再从您的数据收集服务器中接收 Analytics 访客 ID。如果您网站的某些部分尚未实施 [!DNL Experience Cloud] ID 服务，那么当访客浏览这些部分时，将无法识别 Experience Cloud ID，与此同时，分配给访客的会是一个旧版 Analytics 访客 ID。这可能会导致访问次数被重复计数，从而产生错误的属性。

例如，如果您网站的支持部分是在单独的 CMS 中进行管理，则应有一个单独的 Analytics JavaScript 文件负责处理此部分。如果您在为该支持网站部署访客 ID 服务之前，在主网站上部署了访客 ID，那么当新的访客访问支持部分时，他们会收到一个旧版的 Analytics ID，而且跨越这两个网站部分的访问将被报告为不同的访问。

在使用多个 JavaScript 文件或其他技术（例如 Flash）的网站上部署 [!DNL Experience Cloud] ID 服务时，可能会导致协调问题，因为您需要同时对网站的所有部分都启用 ID 服务。通过配置一个宽限期，新的访客可以继续从 [!DNL Experience Cloud] ID 服务中接收 Analytics 访客 ID，这样对于网站中没有升级为使用 ID 服务的部分而言，也可以始终如一地识别访客。

>[!NOTE]
>
>宽限期支持需要 [!DNL Experience Cloud] ID服务的1.3版本或更高版本。

## 我是否需要宽限期？ {#section-fd34c7ff697348a39f49258b7d39eb42}

如果您有一个单独的 Analytics JavaScript 文件并且没有使用任何其他 AppMeasurement 库，则不需要设置宽限期。您可以在这个单独的 JavaScript 文件中执行更新，访问期间将使用 Marketing Cloud ID 来始终如一地识别新的访客。

如果有多个 JavaScript 文件要将数据发送至*同一报表包*，或者，如果您目前在自己的网站上使用 Flash 视频测量等其他技术，那么我们建议配置一个宽限期。

## 怎样才能启用宽限期？ {#section-512d5cd8570e483cbdd8b04457a16ced}

联系 [客户关怀](https://helpx.adobe.com/marketing-cloud/contact-support.html)。
