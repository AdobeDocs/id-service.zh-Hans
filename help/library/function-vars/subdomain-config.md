---
description: 使用这些配置将对Experience Cloud Identity Service调用使用的默认域名更改为您自己的子域名。
keywords: ID 服务
seo-description: 使用这些配置将对Experience Cloud Identity Service调用使用的默认域名更改为您自己的子域名。
seo-title: audienceManagerServer 和 audienceManagerServerSecure
title: audienceManagerServer 和 audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# audienceManagerServer 和 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用这些配置将对Experience Cloud Identity Service调用使用的默认域名更改为您自己的子域名。

**语法：**

* ` audienceManagerServer: " *`your subdomain name`*.demdex.net"`
* ` audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**用途**

通常情况下，[!DNL Experience Cloud] ID 服务会调用 `dpm.demdex.net` 中的 [!DNL Adobe]。有时，您可能不希望调用此目标，因为它看起来太宽泛或者太像“第三方”目标。要让 ID 服务调用看起来更像第一方调用，请使用这些配置将您的 [!DNL Audience Manager] 子域名添加到 `demdex.net`，如下所示。有关 `dpm.demdex.net` 调用的更多信息，请参阅[了解 Demdex 域调用](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)。

**要求**

这些配置要求您使用以下各项：

* 您的公司记录的 [!DNL Audience Manager] 子域名。可向您的顾问确认或获取此域名。
* 与您的 [!DNL Organization ID] 关联的子域名。
* 包含相同子域名的&#x200B;*两个*&#x200B;配置参数。

**代码示例**

在此示例中，假设有一家娱乐传媒公司表示担心对 `dpm.demdex.net` 的调用存在法律问题。在 [!DNL Audience Manager] 中，该公司登记的子域名为 Music1。以下代码示例演示了如何使用这个特定于客户的子域名来对 ID 服务数据调用进行品牌标识。

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

