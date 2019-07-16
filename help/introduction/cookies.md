---
description: ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
keywords: PlayStation;ID 服务
seo-description: ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。
seo-title: Cookie和体验平台标识服务
title: Cookie和体验平台标识服务
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Cookies and the Experience Platform Identity Service{#cookies-and-the-experience-cloud-id-service}

ID 服务使用您的组织 ID、Experience Cloud AMCV Cookie 和 Demdex Cookie，为您的网站访客创建并存储唯一的永久性标识符。这些 Cookie 允许 ID 服务跨不同的域跟踪访客，还允许在不同的 Experience Cloud 解决方案之间共享数据。

## 了解 ID 服务 Cookie {#section-f438168beaec409ab8b2cc58bd021e26}

ID 服务依赖于 AMCV、AMCVS 和 Demdex Cookie 来正常运行。这些 Cookie 就是存储 ID 服务所用数据的文件。这些 ID 服务 Cookie 没有危险或恶意，而且与通过网站或服务存储在浏览器中的其他第一方或第三方 Cookie 没有区别，它们遵循的规则与管理其他第一方和第三方 Cookie 的规则相同。请参阅下面的各个部分，以了解有关 ID 服务所用 Cookie 的更多信息。

**ID 服务 Cookie 可以执行的操作**

* 设置并存储网站访客的唯一 ID（即 MID）。
* 保留此唯一 ID，以便 ID 服务能够收集数据并与其他 Experience Cloud 解决方案共享该数据。
* 跨域跟踪用户。但是，这要求您拥有其他域，并在这些域上部署 ID 服务代码。

**ID 服务 Cookies 不能执行的操作**

* 存储、传输或执行计算机病毒。
* 访问或存储个人身份信息 (PII)，如电子邮件地址。
* 控制计算机硬件或软件。
* 使计算机不稳定或导致出现性能问题。
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

AMCV Cookie 包含 Experience Cloud 访客 ID 或 MID。MID 存储在一个键值对中，它遵循以下语法：`mid|<Experience Cloud ID>`。

一个具有完整形式的键值对应该类似于下面的样子：

```
mid|20265673158980419722735089753036633573
```

此永久性标识符允许进行跨解决方案数据共享。

**域名**

AMCV Cookie 是在浏览器的第一方域中设置的。这意味着它是在用户当前访问网站的域中设置的。因此，ID 服务代码和其他 Experience Cloud 代码库都可以读取 AMCV Cookie 中存储的 MID。

但是，由于 AMCV Cookie 是在第一方域中设置的，因此它无法用于跟踪和识别跨不同域的用户。作为替代，当网站访客导航到其他域时，ID 服务将依靠组织 ID 和 Demdex ID 来返回正确的 MID。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名称**

AMCVS Cookie 名称遵循语法 `AMCVS_####@AdobeOrg`。在名称中，#### 元素是 Experience Cloud 组织 ID 部分的占位符。此 ID 由 ID 服务代码中的 `theVisitor.getInstance` 函数传递到 DCS。

一个具有完整形式的 Cookie 名称应该类似于下面的样子：

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCVS Cookie 可作为指示会话已初始化的标志。它的值始终为 `1`，并会在会话结束时失效。

**域名**

AMCV Cookie 是在浏览器内的第一方域中设置的。这意味着它是在用户当前访问网站的域中设置的。

![](assets/AMCVS-cookie.png)

## Demdex Cookie{#section-7ff7d96d6e4141b08a84a75a63d7814c}

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
   <td colname="col2"> <p>该 Cookie 的名称为“Demdex”。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>内容</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 包含由 DCS 生成的 Demdex ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>域名</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 是在浏览器内的第三方 demdex.net 域中设置的。此域与用户当前访问的网站无关。 </p> <p>与第一方 AMCV Cookie 不同的是，Demdex Cookie 和 ID 可在不同的域之间持续存在。Demdex ID 和您的组织 ID 是通用值，可允许 ID 服务返回并识别具有正确访客 ID 的网站访客。 </p> </td> 
  </tr> 
 </tbody> 
</table>

For related information, see [Understanding Calls to the Demdex Domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## 生成 Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID (MID) 是通过数学方法从您的组织 ID 和 Demdex ID 计算而来的。只要这些 ID 保持不变，为特定用户生成正确的 MID 就仅仅是一个数学问题。通过相同的组织 ID 和 Demdex ID，您每次都能获得相同的 MID 值。这允许 ID 服务在您控制并为其配置了 ID 服务代码的各个域中跟踪访客。

ID 服务会在页面加载时开始创建 MID。在此过程中，由 `visitorAPI.js` 代码库提供的代码会在事件调用中将您的组织 ID 发送至 ID 服务。ID 服务会创建 MID 和 Demdex ID，并将其分别在 AMCV Cookie 和 Demdex Cookie 中返回。

## 后续步骤 {#section-8db1727a63bc4ff68b495f270315d453}

See [How the Experience Platform Identity Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
