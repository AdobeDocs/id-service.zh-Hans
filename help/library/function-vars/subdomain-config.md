---
description: 通过这些配置，可将 Experience Cloud Identity 服务调用所使用的默认域名更改为您自己的子域名。
keywords: ID 服务
title: audienceManagerServer 和 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 100%

---

# audienceManagerServer 和 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

通过这些配置，可将 Experience Cloud Identity 服务调用所使用的默认域名更改为您自己的子域名。

**语法：**

* ` audienceManagerServer: " *`your subdomain name`*.demdex.net"`
* ` audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**用途**

通常情况下，[!DNL Experience Cloud] ID 服务会调用 `dpm.demdex.net` 中的 [!DNL Adobe]。有时，您可能不希望调用此目标，因为它看起来太宽泛或者太像“第三方”目标。要让 ID 服务调用看起来更像第一方调用，请使用这些配置将您的 [!DNL Audience Manager] 子域名添加到 `demdex.net`，如下所示。有关 `dpm.demdex.net` 调用的更多信息，请参阅[了解 Demdex 域调用](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans)。

**要求**

这些配置要求您使用：

* 您的公司记录的 [!DNL Audience Manager] 子域名。可向您的顾问确认或获取此域名。
* 与您的[!UICONTROL 组织 ID] 关联的子域名。
* 具有相同子域名的&#x200B;*两个*&#x200B;配置参数。

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
