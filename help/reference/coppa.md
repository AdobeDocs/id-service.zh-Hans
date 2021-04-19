---
description: 儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud Identity 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。
keywords: ID 服务
seo-description: 儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud Identity 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。
seo-title: Experience Cloud Identity 服务中的 COPPA 支持
title: Experience Cloud Identity 服务中的 COPPA 支持
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '403'
ht-degree: 100%

---

# Experience Cloud Identity 服务中的 COPPA 支持{#coppa-support-in-the-experience-cloud-id-service}

儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud Identity 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。

>[!NOTE]
>
>适用于版本 3.0.0 或更高版本。

**Cookie 与跟踪**

加载网页时，[!DNL Experience Cloud] ID 服务会调用 [!DNL Adobe] 数据收集服务器 (DCS)。DCS 响应包含 Experience Cloud Cookie 和 demdex.net Cookie。

* Experience Cloud Cookie 在第一方域中设置。它不能用于跨不同域跟踪访客，除非这些域协同工作来允许访问。
* demdex.net Cookie 在第三方域中设置。它包含可用于跨不同域跟踪访客的唯一标识符。

**Cookie 和 COPPA 合规性**

在面向（或主要适用于）儿童的网站上跨不同域跟踪访客的第三方 Cookie，触发 COPPA 对征得家长同意的相关要求。为了更易于符合 COPPA 对内部网站分析的规定，请将变量 `disableThirdPartyCookies:true` 添加到 `Visitor.getInstance` 函数中，如下所示。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

当设置为 `true` 时，`disableThirdPartyCookies` 对象会阻止 DCS 返回第三方 demdex.net Cookie。如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 [!DNL Experience Cloud] ID 或返回现有的 ID。[!DNL Experience Cloud] ID 服务而是会在第一方 Cookie 中创建一个新的随机 ID。启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 [!DNL Experience Cloud] 解决方案（包括 COPPA 允许的其他内部操作）之间共享该数据。

>[!MORELIKETHIS]
>
>* [Adobe 隐私权中心](http://www.adobe.com/cn/privacy.html)
>* [什么是 COPPA？](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

