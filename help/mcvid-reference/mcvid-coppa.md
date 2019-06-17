---
description: 儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud ID 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。
keywords: ID 服务
seo-description: 儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud ID 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。
seo-title: Experience Cloud ID 服务中的 COPPA 支持
title: Experience Cloud ID 服务中的 COPPA 支持
uuid: 621b5ebbd-92e7-4635be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID 服务中的 COPPA 支持 {#coppa-support-in-the-experience-cloud-id-service}

儿童在线隐私保护法 (COPPA) 禁止在未征得父母同意的情况下，在线收集 13 岁以下儿童的个人信息。关注 COPPA 的客户可以在其 Experience Cloud ID 服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。

>[!NOTE]
>
>适用于版本 1.5.3 或更高版本。

**Cookie 与跟踪**

加载网页时，[!DNL Experience Cloud] ID 服务会调用 [!DNL Adobe] 数据收集服务器 (DCS)。DCS 响应包含 Experience Cloud Cookie 和 demdex.net Cookie。

* Experience Cloud Cookie 是在第一方域中设置的。它无法用来跟踪跨不同域的访客，除非这些域彼此之间允许相互访问。
* demdex.net Cookie 是在第三方域中设置的。它包含一个唯一的标识符，可用于跟踪跨不同域的访客。

**Cookie 与 COPPA 合规性**

可在面向（或部分面向）儿童的网站上跟踪跨不同域访客的第三方 Cookie 会触发 COPPA 父母同意要求。为了更易于符合 COPPA 对内部网站分析的规定，请将变量 `disableThirdPartyCookies:true` 添加到 `Visitor.getInstance` 函数中，如下所示。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

当设置为 `true` 时，`disableThirdPartyCookies` 对象会阻止 DCS 返回第三方 demdex.net Cookie。如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 [!DNL Experience Cloud] ID 或返回现有的 ID。[!DNL Experience Cloud] ID 服务而是会在第一方 Cookie 中创建一个新的随机 ID。启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 [!DNL Experience Cloud] 解决方案（包括 COPPA 允许的其他内部操作）之间共享该数据。

>[!MORE_ LIKE_ This]
>
>* [Adobe 隐私权中心](http://www.adobe.com/privacy.html)
>* [什么是 COPPA？](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

