---
description: 通过这些配置，可将 Experience Cloud ID 服务调用所使用的默认域名更改为您自己的子域名。
keywords: ID 服务
seo-description: 通过这些配置，可将 Experience Cloud ID 服务调用所使用的默认域名更改为您自己的子域名。
seo-title: audienceManagerServer 和 audienceManagerServerSecure
title: audienceManagerServer 和 audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0 f0-9e90275 f4 c7 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer 和 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

通过这些配置，可将 Experience Cloud ID 服务调用所使用的默认域名更改为您自己的子域名。

**语法：**

* ` audienceManagerServer: " *`your subdomain name`*.demdex.net"`
* ` audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**用途**

通常， [!DNL Experience Cloud] ID服务发出调用 [!DNL Adobe]`dpm.demdex.net`调用。有时，您可能不希望调用此目标，因为它看起来太宽泛或者太像“第三方”目标。要让 ID 服务调用看起来更像第一方调用，请使用这些配置将您的 [!DNL Audience Manager] 子域名添加到 `demdex.net`，如下所示。有关 `dpm.demdex.net` 调用的更多信息，请参阅[了解 Demdex 域调用](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)。

**要求**

这些配置要求您使用以下各项：

* 公司的记录 [!DNL Audience Manager] 的子域名称。可向您的顾问确认或获取此域名。
* 与您的子域关联 [!DNL Organization ID]的子域名。
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

