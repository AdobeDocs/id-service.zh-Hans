---
description: 选择加入服务允许您为访客设置协议，以确定在用户访问网站时您是否可以在用户的设备或浏览器上设置 Cookie。
seo-description: 选择加入服务允许您为访客设置协议，以确定在用户访问网站时您是否可以在用户的设备或浏览器上设置 Cookie。
seo-title: 选择加入服务
title: 选择加入服务
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 73%

---


# 选择加入服务{#opt-in-service}

选择加入服务允许您为访客设置协议，以确定在用户访问网站时您是否可以在用户的设备或浏览器上设置 Cookie。

选择加入服务是 Experience Cloud ID (ECID) 的一项扩展，旨在让您控制 Experience Cloud 解决方案是否可以在用户同意前为访客在网页上创建 Cookie，如果是，具体是哪些解决方案。您还可以通过选择加入服务设置协议以与大型设计中同意管理平台 (CMP) 和现有系统集成。

使用选择加入服务，您可以指定让访客立即选择加入 Adobe 解决方案，还是按照顺序显示解决方案，让访客分别授予权限。批准流程完成并由客户记录后，即可从所有 Adobe 解决方案中检索 CMP 访客批准。

The Opt-in service is implemented and configured easily using [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) with the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md). 您还可以使用 [DTM](../../implementation-guides/opt-in-service/optin-dtm.md) 来实施和配置选择加入服务。

请参阅[设置选择加入服务](../../implementation-guides/opt-in-service/getting-started.md)以开始操作。

>[!NOTE]
>
>选择加入服务允许您设置系统以批准或拒绝仅下载 Adobe Cookie。它不支持收集用户同意首选项，也不是首选项存储库。

>[!IMPORTANT]
>
>本文档的内容不是法律建议，也不会代替法律建议。在设置实施时，请咨询公司的法务部门，获得有关同意和实践的选择加入建议。

## 跨Experience Cloud解决方案选择加入 {#section-053e6224505542cf961896f0ca869e52}

选择加入服务是一个根据您自己的需要创建同意选择加入工作流程的工具，允许您设计工作流程以在用户或同意控制方同意之前和之后做出相应的反应（触发标签）。

通过选择加入服务，您可以为 Adobe 解决方案设置同意管理实践，以便：

* 指示同意收集要求是否适用于用户。
* 指定允许生成Cookie的解决方案。
* 对用户未明确同意或拒绝类别的任何解决方案应用默认首选项。
* 根据用户同意设置的更改触发自定义响应，以便您保留或更新用户设置。

使用选择加入服务，您可以将您的网站配置为在用户做出选择之前，加载一些预先同意的 Cookie。您可以将新客户的选择加入服务设置为允许在用户同意或做出选择后加载 Cookie。您还可以存储并检索您选择加入现有的同意管理平台的同意，或者只将权选择加入限存储在cookie中。

![](assets/Opt-in-approval.png)

Adobe解决方案随后可以检查标记是否获得批准，订阅更改，然后检索所有选择加入客户。 选择加入服务允许您直接通过解决方案 JavaScript 库或通过 ECID（如果已实施）获取权限。
