---
title: Google Chrome SameSite标签更改
seo-title: Google Chrome SameSite标签更改
description: 适用于 Adobe ECID（ID 服务）库的文档。
seo-description: 适用于 Adobe ECID（ID 服务）库的文档。
translation-type: tm+mt
source-git-commit: f74a028532e95ab17f5d2e64697d69eb64e03391
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Google Chrome SameSite标签更改 {#google-chrome-samesite-labelling-changes}

SameSite属性告诉浏览者在第一方和第三方场景中何时以及如何触发cookie。 SameSite属性可以具有以下三个值之一： `strict`、 `lax`或 `none`。 自2017年11月推出以来，Chrome、Firefox、Edge、 `strict` Safari和 `lax` Opera均得到支持 `none` ，并于2018年推出。 但是，某些旧版浏览器不支持此设置。

2020年2月，Google发布了Chrome 80，并将默认设置从 `none` 更 `lax` 改为当cookie没有指定的SameSite属性值时。 此设置可防止在第三方上下文（也称为“跨站点”）中使用Cookie。 随后发生的任何第三方Cookie都必须设置为 `SameSite=none` 并标记为安全。

没有指定SameSite属性值的Cookie将默认为 `lax`。

有关SameSite属 [性的更多信息](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) ，请访问Cookie标准文档。

## SameSite属性值

| SameSite属性值 | 描述 |
| ------ | ------------ |
| `strict` | 仅当引用页面和登陆页与cookie属于同一域时，才会发送具有此设置的cookie。 |
| `lax` | 仅当浏览器URL中显示的域与cookie的域匹配时，才会发送具有此设置的cookie。 这是Chrome中Cookie的新默认设置。 |
| `none` | 具有此设置的Cookie可用于外部或第三方访问，如“跨站点”。 在进行此更改之前， `none` 是cookie的默认SameSite设置，因此使用此设置可使cookie的行为与其传统工作方式最相似。 但是，Google要求具有此设置的任何Cookie现在都指定安全标志，这意味着Cookie将仅通过HTTPS创建和发送请求。 所有没有安全标志的跨站点Cookie将被Google拒绝。 |

## 作为Adobe Experience Cloud客户，您需要了解的

**无需JavaScript更新**

Adobe产品已发布服务器端更新，以设置具有相应属性的第三方cookie。 我们的客户不需要JavaScript库更新。

**确保第三方端点使用HTTPS**

所有客户应确认其JavaScript配置正在使用HTTPS来调用Adobe服务。 目标、Audience Manager和Experience Cloud标识服务(ECID)正在将第三方HTTP调用重定向到其各自的HTTPS端点，这会增加延迟。 这意味着您无需更改配置。 Analytics客户应更新其实施以专门使用HTTPS，因为特定于Analytics的重定向可能会导致数据丢失。

**正确标记的cookies应按预期收集数据**

只要cookies的标签正确，浏览器就不会采取任何措施来阻止它们。 消费者可以选择阻止某些类型的Cookie，但目前，这似乎只是一个选择加入设置。

**将忽略未更新标签的现有第三方Cookie**

在Chrome 80开始强制SameSite=之前创建的第三方Cookie`none` ，如果这些标志不存在，则Chrome 80将忽略安全标志设置。

许多现有的Adobe第三方Cookie没有这些标志，需要由边缘服务器更新，然后用户才能升级到Chrome 80，否则这些Cookie将丢失。 当用户访问使用Cookie的任何网站时，边缘服务器会自动更新。

大多数Adobe产品已经为cookie分配了相应的标记。 Analytics实施中使用第三方数据收集且不使用ECID的情况除外。 客户可能会遇到新访客的暂时性小幅增加，否则，新访客会返回。

**目标和市场合作伙伴的Cookie匹配可能会降低(仅限Audience Manager)**

虽然Adobe可以控制更新其cookie，但Adobe无法强制合作伙伴进行必要的更改。 对于使用未进行这些更新的目标合作伙伴或市场合作伙伴的Audience Manager客户，Cookie匹配可能会降低。

**Analytics友好型第三方Cookie(仅限`s_vi`Analytics Cookie)**

某些Analytics实施使用Analytics CNAME别名，以启用在 `s_vi` 该CNAME的域中创建Cookie。 如果CNAME与您的网站位于同一域中，则此CNAME将指定为第一方Cookie。 但是，如果您拥有多个域，并且在所有域中使用相同的CNAME进行数据收集，那么在这些其他域上它将指定为第三方cookie。

在 `lax` Chrome中成为新的默认SameSite设置后，CNAME在其他域上不再可见。

为了适应此更改，Analytics现在将cookie的SameSite值显 `s_vi` 式设置为 `lax`。 要在友好的第三方上下文中使用此Cookie，请将SameSite值设 `none`置为，这也意味着您必须始终使用HTTPS。 请联系客户服务部门，更改您的安全CNAME的SameSite值。

> [!IMPORTANT] 使用ECID的Analytics客户、对其每个域使用单独CNAME的客户或仅使用第三方Analytics数据收集的客户不需要执行此操作。

## Adobe标准访客Cookie

下表仅列出通用访客标准Cookie。 有关其他Cookie配置，请参阅产品特定文档或与Adobe代表联系。

### ECID

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | 客户端第一方 | 无增值*Chrome默认设置为 `lax` 设置 | 可配置 |
| AMCVS_###@AdobeOrg | 客户端第一方 | 无增值*Chrome默认设置为 `lax` 设置 | 可配置 |
| s_ecid | 服务器端第一方 | SameSite==`lax` | 未设置 |

### Audience Manager

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | 第三方 | `none` | 设置为安全 |
| Dextp | 第三方 | `none` | 设置为安全 |

### Analytics

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> 服务器端第一方(如果使用 `CNAME` </li> <li>第三方（如果使用2o7.net或omtrdc.net）</li></ul> | <ul><li>`lax` if第一方</li> <li>`none` 如果是第三方</li></ul> *客户可以通过第一方域的客户关怀票证编辑设置* | 设置(如果使用和 `none` HTTPS请求) |
| s_fid | 客户端第一方 | 没有添加值*Chrome默认值为设 `lax` 置 | 未设置 |

### Target

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | 第一方 | 无增值*Chrome默认设置为 `lax` 设置 | 未设置 |

### Ad Cloud

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | 第三方 | `none` *仅在基于Google Chrome和Chromium的浏览器上* | 设置(如果使用和 `none` HTTPS请求) |
| data_adcloud | 第一方 | 无增值*Chrome默认设置为 `lax` 设置 | 未设置 |
| ev_tm | 第三方 | `none` *仅在基于Google Chrome和Chromium的浏览器上* | 设置(如果使用和 `none` HTTPS请求) |

### Bizible

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | 第三方 | `none` | Secure |

### 马克托·蒙奇金

| Cookie | 类型 | SameSite属性 | 安全属性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | 客户端第一方 | 无增值*Chrome默认设置为 `lax` 设置 | 可针对外部页面进行配置 |

> !![IMPORTANT] Adobe第三方Cookie是在服务器端

有关详细信息，请参阅有关文档 [的Google Chrome SameSite策略的目标](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)。