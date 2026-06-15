---
description: 儿童在线隐私保护法(COPPA)禁止在未征得父母同意的情况下，在线收集13岁以下儿童的个人信息。 关注 COPPA 的客户可以在其 Experience Cloud 身份标识服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。
keywords: ID 服务
title: Experience Cloud 身份标识服务中的 COPPA 支持
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 86%

---

# Experience Cloud 身份标识服务中的 COPPA 支持 {#coppa-support-in-the-experience-cloud-id-service}

儿童在线隐私保护法(COPPA)禁止在未征得父母同意的情况下，在线收集13岁以下儿童的个人信息。 关注 COPPA 的客户可以在其 Experience Cloud 身份标识服务代码中添加一个可选变量，以阻止在浏览器的第三方域中设置 Cookie。

>[!NOTE]
>
>适用于版本 3.0.0 或更高版本。

**Cookie 与跟踪**

加载网页时，[!DNL Experience Cloud] ID 服务会调用 [!DNL Adobe] 数据收集服务器 (DCS)。 DCS 响应包含 Experience Cloud Cookie 和 demdex.net Cookie。

* Experience Cloud Cookie 在第一方域中设置。 它不能用于跨不同域跟踪访客，除非这些域协同工作来允许访问。
* demdex.net Cookie 在第三方域中设置。 它包含可用于跨不同域跟踪访客的唯一标识符。

**Cookie 和 COPPA 合规性**

在面向（或主要适用于）儿童的网站上跨不同域跟踪访客的第三方 Cookie，触发 COPPA 对征得家长同意的相关要求。 为了更易于符合 COPPA 对内部网站分析的规定，请将变量 `disableThirdPartyCookies:true` 添加到 `Visitor.getInstance` 函数中，如下所示。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

当设置为 `true` 时，`disableThirdPartyCookies` 对象会阻止 DCS 返回第三方 demdex.net Cookie。 如果网站访客的浏览器中已经具有此 Cookie，则 ID 服务不会使用它来创建新的 [!DNL Experience Cloud] ID 或返回现有的 ID。 [!DNL Experience Cloud] ID 服务而是会在第一方 Cookie 中创建一个新的随机 ID。 启用 ID 服务后，您可以通过该服务来收集数据，并在不同的 [!DNL Experience Cloud] 解决方案（包括 COPPA 允许的其他内部操作）之间共享该数据。

>[!MORELIKETHIS]
>
>* [Adobe 隐私权中心](http://www.adobe.com/cn/privacy.html)
>* [什么是 COPPA？](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

