---
title: Google Chrome SameSite 标签更改
description: 适用于 Adobe ECID（ID 服务）库的文档。
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: ee4b7f8df5766372034da2a76e7acb81ba2a65f0
workflow-type: ht
source-wordcount: '1064'
ht-degree: 100%

---

# Google Chrome SameSite 标签更改 {#google-chrome-samesite-labelling-changes}

SameSite 属性可告知浏览器何时以及如何在第一方和第三方环境中触发 Cookie。SameSite 属性可具有以下三个值之一：`strict`、`lax` 或 `none`。自 2017 年 11 月以来，Chrome、Firefox、Edge、Safari 和 Opera 均已支持 `strict` 和 `lax`；2018 年，又引入了 `none`。然而，某些旧版浏览器并不支持这种设置。

2020 年 2 月，Google 发布了 Chrome 80，在该版本中，如果 Cookie 不具备指定的 SameSite 属性值，那么默认设置将由 `none` 更改为 `lax`。该设置可防止在第三方环境（也称为“跨站点”）中使用 Cookie。任何后续的第三方 Cookie 都必须设置为 `SameSite=none` 并标记为安全。

对于未设置指定 SameSite 属性值的 Cookie，默认情况下将被设置为 `lax`。

有关 SameSite 属性的更多信息，请访问 [Cookie 标准文档](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1)。

## SameSite 属性值

| SameSite 属性值 | 描述 |
| ------ | ------------ |
| `strict` | 仅当引用页面和登陆页面都与 Cookie 处于相同的域时，才发送具有此设置的 Cookie。 |
| `lax` | 仅当浏览器的 URL 中显示的域与 Cookie 的域匹配时，才发送具有此设置的 Cookie。这是 Chrome 中新增的 Cookie 默认设置。 |
| `none` | 具有此设置的 Cookie 可用于外部或第三方访问，如“跨站点”访问。在进行此项更改之前，`none` 是 Cookie 的默认 SameSite 设置，因此使用该设置可以让 Cookie 的行为最接近其传统的工作方式。但是，Google 现在要求任何具有此设置的 Cookie 都应指定安全标志，这意味着此类 Cookie 将只能通过 HTTPS 创建和发送请求。Google 将会拒绝所有没有安全标志的跨站点 Cookie。 |

## Adobe Experience Cloud 客户须知

**无需执行 JavaScript 更新**

Adobe 产品已发布了服务器端更新，实现了用适当的属性来设置第三方 Cookie。我们的客户不需要更新 JavaScript 库。

**确保第三方端点使用 HTTPS**

客户应确认其 JavaScript 配置正在使用 HTTPS 来调用 Adobe 服务。Target、Audience Manager 和 Experience Cloud Identity 服务 (ECID) 正在将第三方 HTTP 调用重定向到各自的 HTTPS 端点，该项操作可能会增加延迟。这意味着您无需更改配置。由于特定于 Analytics 的重定向可能会导致数据丢失，因此 Analytics 客户应更新其实施，以便能够专门使用 HTTPS。

**正确标记的 Cookies 应按照预期收集数据**

只要 Cookies 的标签正确，浏览器就不会采取任何措施来阻止它们。消费者可以选择阻止某些类型的 Cookie，但目前似乎只有一个选择启用设置。

**将忽略现有的未更新标签的第三方 Cookie**

那些在 Chrome 80 开始强制实施 SameSite= `none` 和安全标志设置之前创建的第三方 Cookie，如果不具备这些安全标志，则会被 Chrome 80 忽略。

许多现有的 Adobe 第三方 Cookie 没有这些标志，因而需要在用户升级到 Chrome 80 之前通过边缘服务器进行更新，否则这些 Cookie 将会丢失。当用户访问任意使用相关 Cookie 的网站时，边缘服务器会自动对它们进行更新。

大多数 Adobe 产品已经为 Cookie 分配了相应的标志。使用第三方数据收集但不使用 ECID 的 Analytics 实施除外。这些客户可能会遇到新访客数量的小幅临时性增加，否则这些新访客将被标记为回访访客。

**目标合作伙伴和市场合作伙伴可能会导致匹配 Cookie 的数量有所减少（仅限 Audience Manager）**

尽管 Adobe 可以控制其 Cookie 的更新，但是 Adobe 不能强制要求合作伙伴执行必要的更改。对于使用未执行这些更新的目标合作伙伴或市场合作伙伴的 Audience Manager 客户而言，匹配的 Cookie 数量可能会有所减少。

**Analytics 的第三方友好 Cookie（仅限 Analytics `s_vi` Cookie）**

有些 Analytics 实施会使用 Analytics CNAME 别名来支持在该 CNAME 的域中创建 `s_vi` Cookie。如果该 CNAME 与您的网站位于同一个域，那么该 CNAME 将被指派为第一方 Cookie。但是，如果您拥有多个域，并且在所有域中均使用相同的 CNAME 来进行数据收集，那么对于其他域而言，该 CNAME 将被指派为第三方 Cookie。

随着 `lax` 在 Chrome 中成为新的默认 SameSite 设置，该 CNAME 在其他域中将不再可见。

为了适应这项更改，Analytics 现在明确地将 `s_vi` Cookie 的 SameSite 值设置为 `lax`。要在友好的第三方环境中使用此 Cookie，需将 SameSite 值设置为 `none`，这也意味着您必须始终使用 HTTPS。请联系客户关怀部门，以便为您安全的 CNAME 更改 SameSite 值。

>[!IMPORTANT]
>
>使用 ECID 的 Analytics 客户、对其每个域使用单独的 CNAME 的客户，或者仅使用第三方 Analytics 数据收集的客户，均不需要执行此操作。

## Adobe 标准访客 Cookie

下表仅列出了通用的访客标准 Cookie。有关其他 Cookie 配置，请参阅特定于产品的文档或与您的 Adobe 代表联系。

### ECID

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | 客户端第一方 | 无增值 *Chrome 默认设置为 `lax` | 可配置 |
| AMCVS_###@AdobeOrg | 客户端第一方 | 无增值 *Chrome 默认设置为 `lax` | 可配置 |
| s_ecid | 服务器端第一方 | SameSite==`lax` | 未设置 |

### Audience Manager

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | 第三方 | `none` | 设置为安全 |
| Dextp | 第三方 | `none` | 设置为安全 |

### Analytics

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> 使用 `CNAME` 的服务器端第一方 </li> <li>使用 2o7.net 或 omtrdc.net 的第三方</li></ul> | <ul><li>若为第一方，则属性为 `lax`</li> <li>若为第三方，则属性为 `none`</li></ul> *客户可通过客户关怀团队开具的票证，编辑第一方域的设置* | 已设置（如果使用 `none` 和 HTTPS 请求） |
| s_fid | 客户端第一方 | 无增值 *Chrome 默认设置为 `lax` | 未设置 |

### Target

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | 第一方 | 无增值 *Chrome 默认设置为 `lax` | 未设置 |

### Ad Cloud

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | 第三方 | `none` *仅设置 Google Chrome 和基于 Chromium 的浏览器上* | 已设置（如果使用 `none` 和 HTTPS 请求） |
| data_adcloud | 第一方 | 无增值 *Chrome 默认设置为 `lax` | 未设置 |
| ev_tm | 第三方 | `none` *仅设置 Google Chrome 和基于 Chromium 的浏览器上* | 已设置（如果使用 `none` 和 HTTPS 请求） |

### Bizible

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | 第三方 | `none` | 安全 |

### Marketo Munchkin

| Cookie | 类型 | SameSite 属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | 客户端第一方 | 无增值 *Chrome 默认设置为 `lax` | 可对外部页面进行配置 |

>  Adobe 第三方 Cookie 在服务器端设置。

有关详细信息，请参阅文档 [Target 的 Google Chrome SameSite 策略](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html)。
