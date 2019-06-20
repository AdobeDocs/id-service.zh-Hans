---
description: 使用这些配置将对Experience Cloud ID服务调用使用的默认域名更改为您自己的子域名。
keywords: ID 服务
seo-description: 使用这些配置将对Experience Cloud ID服务调用使用的默认域名更改为您自己的子域名。
seo-title: audienceManagerServer 和 audienceManagerServerSecure
title: audienceManagerServer 和 audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0 f0-9e90275 f4 c7 c
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# audienceManagerServer 和 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用这些配置将对Experience Cloud ID服务调用使用的默认域名更改为您自己的子域名。

**语法：**

* ` audienceManagerServer: " *`your subdomain name`*.demdex.net"`
* ` audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**用途**

Normally, the [!DNL Experience Cloud] ID service makes calls to [!DNL Adobe] at `dpm.demdex.net`. 有时，您可能不希望调用此目标，因为它看起来太宽泛或者太像“第三方”目标。要让 ID 服务调用看起来更像第一方调用，请使用这些配置将您的 [!DNL Audience Manager] 子域名添加到 `demdex.net`，如下所示。有关 `dpm.demdex.net` 调用的更多信息，请参阅[了解 Demdex 域调用](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)。

**要求**

这些配置要求您使用以下各项：

* The [!DNL Audience Manager] subdomain name of record for your company. 可向您的顾问确认或获取此域名。
* The subdomain name associated with your [!DNL Organization ID].
* 包含相同子域名的*两个*配置参数。

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

