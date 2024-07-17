---
description: ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
keywords: PlayStation;ID 服务
title: Cookie 和 Experience Cloud Identity 服务
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
source-git-commit: 33e467ade389144423abf14539aad8a5a5f69d21
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 100%

---

# Cookie 和 Experience Cloud Identity 服务{#cookies-and-the-experience-cloud-id-service}

ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。

## 了解 ID 服务 Cookie {#section-f438168beaec409ab8b2cc58bd021e26}

ID 服务依赖 AMCV、AMCVS 和 Demdex Cookie 来正常运行。这些 Cookie 只是用于存储 ID 服务所使用的数据的文件。这些 ID 服务 Cookie 没有危险、无恶意，而且与网站或服务在浏览器中存储的其他第一方或第三方 Cookie 没有什么不同，它们遵循的规则与管理其他第一方和第三方 Cookie 的规则相同。请参阅下面的各个部分，以了解有关 ID 服务所用 Cookie 的更多信息。

### ID 服务 Cookie 可以执行的操作

* 为网站访客设置和存储唯一 ID (MID)。
* 保留此唯一 ID，以便 ID 服务可以收集数据并与其他 Experience Cloud 解决方案共享数据。
* 跨域跟踪用户。但是，这要求您拥有其他域并在这些域上部署 ID 服务代码。

### ID 服务 Cookie 无法执行的操作

* 存储、传输或执行计算机病毒。
* 访问或存储个人身份信息 (PII)，如您的电子邮件地址。
* 控制计算机硬件或软件。
* 使计算机不稳定或导致性能问题。
* 在未使用 ID 服务的网站上跟踪用户。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

ID 服务设置 Cookie 的以下属性。

**名称**

AMCV Cookie 的名称应遵循语法 `AMCV_<variable name>@AdobeOrg`。在名称中，`<variable name>` 元素是 Experience Cloud 组织 ID 部分的占位符。此 ID 由 ID 服务代码中的 `Visitor.getInstance` 函数传递到 DCS。

一个具有完整形式的 Cookie 名称应该类似于下面的样子：

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCV Cookie 包含 Experience Cloud 访客 ID 或 MID。MID 存储在一个键值对中，它遵循以下语法：`MCMID|<Experience Cloud ID>`。

一个具有完整形式的键值对应该类似于下面的样子：

```
MCMID|20265673158980419722735089753036633573
```

此永久性标识符支持跨解决方案共享数据。

**域**

AMCV Cookie 是在浏览器的第一方域中设置的。这意味着它在用户当前访问的网站的域中设置。因此，ID 服务代码和其他 Experience Cloud 代码库可以读取 AMCV Cookie 中存储的 MID。

但是，由于 AMCV Cookie 是在第一方域中设置的，它不能用于跟踪和识别不同域中的用户。当网站访客导航到其他域时，ID 服务而是会依赖组织 ID 和 Demdex ID 来返回正确的 MID。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名称**

AMCVS Cookie 名称遵循语法 `AMCVS_####@AdobeOrg`。在名称中，#### 元素是 Experience Cloud 组织 ID 部分的占位符。此 ID 由 ID 服务代码中的 `theVisitor.getInstance` 函数传递到 DCS。

一个具有完整形式的 Cookie 名称应该类似于下面的样子：

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCVS Cookie 用作指示会话已初始化的标记。它的值始终为 `1`，并会在会话结束时失效。

**域**

AMCVS Cookie 是在浏览器的第一方域中设置的。这意味着它在用户当前访问的网站的域中设置。

![](assets/AMCVS-cookie.png)

## Demdex Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

下表列出并定义了 Demdex Cookie 的一些重要属性。

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 属性 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>名称</b> </p> </td> 
   <td colname="col2"> <p>Cookie 名称为“Demdex”。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>内容</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 包含由 DCS 生成的 Demdex ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>域</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 是在浏览器的第三方 demdex.net 域中设置的。该域不同于用户当前访问的网站。 </p> <p>与第一方 AMCV Cookie 不同，Demdex Cookie 和 ID 会跨不同域持续存在。Demdex ID 和您的组织 ID 是常用值，它们允许 ID 服务返回并识别具有正确访客 ID 的网站访客。 </p> </td> 
  </tr> 
 </tbody> 
</table>

有关 Demdex 的披露信息，请访问 [Audience Manager 设备存储披露](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json)。

有关相关信息，请阅读关于[了解 Demdex 域调用](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hans)的文档。

## 生成 Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID (MID) 是通过数学方法从您的组织 ID 和 Demdex ID 计算而来的。只要这些 ID 保持不变，为特定用户生成正确的 MID 就只是一个数学问题。使用相同的组织 ID 和 Demdex ID，您每次会获得相同的 MID 值。这允许 ID 服务跨由您控制并配置了 ID 服务代码的域来跟踪访客。

ID 服务在页面加载时开始创建 MID。在此过程中，由 `visitorAPI.js` 代码库提供的代码会在事件调用中将您的组织 ID 发送至 ID 服务。ID 服务会创建 MID 和 Demdex ID，并将其分别在 AMCV Cookie 和 Demdex Cookie 中返回。

## Cookie 标记

下表介绍了 Experience Cloud Cookie 标记：

| Cookie（设置方式） | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex（http 响应） | 否 | 是 | &quot;无&quot; |
| AMCV (Javascript) | 否 | 可配置 | 未设置（默认为“Lax”） |
| AMCVS (Javascript) | 否 | 可配置 | 未设置（默认为“Lax”） |

*注意：有关使用安全属性配置 AMCV 和 AMCVS Cookie 的信息，请参阅 [secureCookie](../library/function-vars/securecookie.md) 主题。*

## 后续步骤 {#section-8db1727a63bc4ff68b495f270315d453}

请参阅 [Experience Cloud Identity 服务如何请求和设置 ID...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)。
