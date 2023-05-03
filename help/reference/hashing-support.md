---
description: Experience Cloud ID 服务 (ECID) 支持 SHA-256 哈希算法，该算法允许您传入客户 ID 或电子邮件地址，并传出经过哈希处理的 ID。这是一种可选的 Javascript 方法，用于将经过哈希处理的标识符发送到 Experience Cloud。在发送客户 ID 之前，您可以继续使用自己的哈希处理方法。
keywords: ID 服务
title: 对 setCustomerIDs 支持 SHA256 哈希
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: ht
source-wordcount: '602'
ht-degree: 100%

---

# 对 `setCustomerIDs` 支持 SHA256 哈希 {#hashing-support}

Experience Cloud ID 服务 (ECID) 支持 SHA-256 哈希算法，该算法允许您传入客户 ID 或电子邮件地址，并传出经过哈希处理的 ID。这是一种可选的 Javascript 方法，用于将经过哈希处理的标识符发送到 Experience Cloud。在发送客户 ID 之前，您可以继续使用自己的哈希处理方法。有两种方法可以对 setCustomerIDs 实施哈希处理支持，具体如以下部分所述：

* [在 ECID 中使用 setCustomerIDs 方法](/help/reference/hashing-support.md#use-setcustomerids-method)
* [在 Adobe Experience Platform Launch 中添加一项操作](/help/reference/hashing-support.md#add-action-launch)

## 在 ECID 中使用 `setCustomerIDs` 方法 {#use-setcustomerids-method}

第一种方法是使用 [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) 方法。

在进行哈希处理之前，ECID 库会对 customerIDs 执行数据标准化。此过程会去除 customerIDs 两端的空格，并将所有字符转换为小写。例如，电子邮件地址“ ecid@adobe.com ”会变为“ecid@adobe.com”

请参阅下面的代码示例，了解如何使用 SHA-256 哈希处理来设置单个客户 ID（上面提到的电子邮件地址）。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

除了 Experience Cloud 访客 ID 之外，您还可以将其他的客户 ID、身份验证状态以及哈希类型 (SHA-256) 与每位访客关联。如果您不提供任何哈希类型，则将被视为不进行哈希处理。

`setCustomerIDs` 方法可以接受同一访客拥有多个客户 ID。这有助于您识别或定位跨不同设备的单独用户。例如，您可以将这些 ID 作为[客户属性](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html)上传至 Experience Cloud，并在不同的解决方案中访问此数据。

客户 ID、身份验证状态以及哈希类型&#x200B;*不会*&#x200B;存储在 Cookie 中以供稍后使用，而是应存储在实例变量中，以便使用 [`getCustomerIDs`](/help/library/get-set/getcustomerids.md) 进行检索，如下所示：

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

使用 `setCustomerIDs` 方法会导致调用 Experience Cloud ID 服务、`dpm.demdex.net` 以及 `d_cid_ic` 查询参数，该参数包含经过哈希处理的客户 ID。调用示例可能与以下内容类似。为清楚起见，添加了换行符。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

请参阅下表，了解有关 `d_cid_ic` 参数和身份验证状态的描述。

| 参数 | 描述 |
|------------|----------|
| `d_cid_ic` | 将集成代码、唯一用户 ID (DPUUID) 和经过身份验证的状态 ID 传递到 ID 服务。使用不可打印的控制字符 %01</code> 将集成代码与 DPUUID 分隔开：<br>示例：d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>身份验证状态</b> <br>这是 d_cid_ic 参数中的一个可选 ID。此 ID 以整数形式表示，用于根据用户的身份验证状态来标识用户，如下所示：<br> <ul><li>0（未知或从未验证）</li><li>1（当前已经针对此实例/页面/应用程序上下文进行了身份验证）</li><li>2（已注销）</li></ul> <br>示例：<br> <ul><li>未知：...d_cid=123%01456%01<b>0</b></li><li>已通过身份验证：...d_cid=123%01456%01<b>1</b></li><li>已注销：...d_cid=123%01456%01<b>2</b></li></ul> |

## 在 Adobe Experience Platform Launch 中添加一项操作 {#add-action-launch}

Experience Platform Launch 是 Adobe 推出的新一代标记管理功能。有关 Platform Launch 的更多信息，请参阅 [Launch 产品文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)。

要在 Launch 中添加一项操作，请参阅 Adobe Launch 中的[规则文档](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html)并查看下面的屏幕截图：

![](/help/reference/assets/hashing-support.png)

<br> 

在确认您的配置后，Launch 会将数据打包到一个对象中，如下所示：

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

下面是一个代码示例：

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

与第一部分所述的 `setCustomerIDs` 方法类似，这会导致调用 Experience Cloud ID 服务以及 `d_cid_ic` 查询参数。
