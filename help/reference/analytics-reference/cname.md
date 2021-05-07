---
description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
keywords: 操作顺序;ID 服务
seo-description: 如果您有一个主要的登录网站，可以在客户访问其他域之前识别客户，那么 CNAME 就可以在不接受第三方 Cookie 的浏览器（如 Safari）中启用跨域跟踪。
seo-title: CNAME实施概述
title: CNAME实施概述
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# CNAME实现概述{#cname-implementation-overview}

CNAME实施允许您自定义Adobe使用的集合域，以便它们与您自己的域匹配。 这允许Adobe使用JavaScript在服务器端而不是客户端设置第一方Cookie。 过去，这些服务器端第一方Cookie不受Apple的Intelligent Tracking Prevention(ITP)策略下施加的限制。 但是，在2020年11月，[!DNL Apple]更新了其策略，以便这些限制也适用于通过CNAME设置的Cookie。 目前，通过CNAME在服务器端设置的Cookie和通过Javascript在客户端设置的Cookie在ITP下均限于7天或24小时的到期时间。 有关ITP策略的详细信息，请参阅此[!DNL Apple]文档[关于跟踪预防](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)。

虽然CNAME实施在Cookie生命周期方面不提供任何好处，但可能还有一些其他好处，如广告拦截器和不太常见的浏览器阻止数据发送到它们归类为跟踪器的域。 在这些情况下，使用CNAME可能会防止使用这些工具的用户中断您的数据收集。