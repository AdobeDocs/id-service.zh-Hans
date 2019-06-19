---
description: 选择服务允许您为访客设置协议，以确定您是否可以在访问站点时在用户的设备或浏览器上设置Cookie。
seo-description: 选择服务允许您为访客设置协议，以确定您是否可以在访问站点时在用户的设备或浏览器上设置Cookie。
seo-title: 选择服务
title: 选择服务
uuid: aabd72ad-4118-471b-9755-d08 a72 ca0 fd
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# 选择服务{#opt-in-service}

选择服务允许您为访客设置协议，以确定您是否可以在访问站点时在用户的设备或浏览器上设置Cookie。

选择服务是Experience Cloud ID(ECID)的扩展，设计用于控制用户在用户同意之前是否可以在网页上为访客创建cookies。通过选择加入服务，您还可以将协议设置为与同意管理平台(CMP)和现有系统集成，作为更大设计的一部分。

使用参与服务，您可以指定一个访客是否可以同时参与Adobe解决方案，或按顺序提供解决方案以进行权限。批准流程完成并由客户记录后，即可从所有 Adobe 解决方案中检索 CMP 访客批准。

使用可选择扩展的 [Adobe Launch](https://docs.adobelaunch.com/) 轻松实施和配置 [参与服务](../../implementation-guides/opt-in-service/launch.md)。它还可以使用 [DTM实现和配置](../../implementation-guides/opt-in-service/optin-dtm.md)。

请参阅 [设置参与服务](../../implementation-guides/opt-in-service/getting-started.md) 以开始。

>[!NOTE]
>
>选择服务允许您设置一个系统，以仅批准或拒绝下载Adobe cookies。它不支持收集用户同意首选项，也不是首选项存储库。

>[!IMPORTANT]
>
>本文档内容不是法律建议，旨在代替法律建议。在设置选择加入实施时，请咨询贵公司的法律部门，获取有关同意和做法的建议。

## 跨多个 Experience Cloud 解决方案的选择加入 {#section-053e6224505542cf961896f0ca869e52}

选择服务是一种根据您自己的需求在工作流程中构建同意的工具，允许您设计一个工作流，以便在用户或您同意的管理者提供同意之前和之后设计出响应(触发标记)。

通过选择加入服务，您可以为Adobe解决方案设置同意管理实践：

* 指出同意收集要求是否普遍适用于用户。
* 指定允许哪些解决方案生成 Cookie。
* 对属于用户未明确同意或拒绝类别的任何解决方案应用默认首选项。
* 根据对用户同意设置的更改触发自定义响应，允许您保留或更新用户的设置。

使用参与服务，您可以配置网站，以允许某些cookie在用户选择之前加载预先同意。您可以为新客户设置选择加入服务，以允许在用户同意后或在提供选择后加载cookie。您还可以从现有的“同意管理平台”存储和检索选择加入同意，或只在 Cookie 中存储选择加入权限。

![](assets/Opt-in-approval.png)

然后，Adobe 解决方案可以检查标签是否已获批准，订阅更改，然后检索所有选择加入的客户。选择服务允许您直接通过解决方案JavaScript库或ECID获得权限(如果已执行)。
