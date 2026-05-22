---
description: 通过这些配置，可将 Experience Cloud 身份标识服务调用所使用的默认域名更改为您自己的子域名。
keywords: ID 服务
title: audienceManagerServer 和 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 222
ht-degree: 100%

---

# audienceManagerServer 和 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

通过这些配置，可将 Experience Cloud 身份标识服务调用所使用的默认域名更改为您自己的子域名。

**语法：**

* `audienceManagerServer: " *`your subdomain name`*.demdex.net"`
* `audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**用途**

通常情况下，[!DNL Experience Cloud] ID 服务会调用 `dpm.demdex.net` 中的 [!DNL Adobe]。 有时，您可能不希望调用此目标，因为它看起来太宽泛或者太像“第三方”目标。 要让 ID 服务调用看起来更像第一方调用，请使用这些配置将您的 [!DNL Audience Manager] 子域名添加到 `demdex.net`，如下所示。 有关 `dpm.demdex.net` 调用的更多信息，请参阅[了解 Demdex 域调用](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans)。

**要求**

这些配置要求您使用：

* 您的公司记录的 [!DNL Audience Manager] 子域名。 可向您的顾问确认或获取此域名。
* 与您的 [!UICONTROL Organization ID] 关联的子域名。
* 具有相同子域名的&#x200B;*两个*&#x200B;配置参数。

**代码示例**

在此示例中，假设有一家娱乐传媒公司表示担心对 `dpm.demdex.net` 的调用存在法律问题。 在 [!DNL Audience Manager] 中，该公司登记的子域名为 Music1。 以下代码示例演示了如何使用这个特定于客户的子域名来对 ID 服务数据调用进行品牌标识。

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

