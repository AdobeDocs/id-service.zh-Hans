---
description: Experience Cloud ID服务(EID)支持SHA-256哈希哈希算法，它允许您传递客户ID或电子邮件地址，并传递散列的ID。这是一种可选的Javascript方法，用于将哈希标识符发送到Experience Cloud。在发送客户ID之前，您可以继续使用自己的哈希散列方法。
keywords: ID 服务
seo-description: Experience Cloud ID服务(EID)支持SHA-256哈希哈希算法，它允许您传递客户ID或电子邮件地址，并传递散列的ID。这是一种可选的Javascript方法，用于将哈希标识符发送到Experience Cloud。在发送客户ID之前，您可以继续使用自己的哈希散列方法。
seo-title: SHA256散列支持setCustomerID
title: SHA256散列支持setCustomerID
translation-type: tm+mt
source-git-commit: c670939cbeaebf4530df0e7d12e992ca5f0963bd

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Experience Cloud ID服务(EID)支持SHA-256哈希哈希算法，它允许您传递客户ID或电子邮件地址，并传递散列的ID。这是一种可选的Javascript方法，用于将哈希标识符发送到Experience Cloud。在发送客户ID之前，您可以继续使用自己的哈希散列方法。
有两种方法可使用setCustomerID实现散列支持，如下面的部分所述：

* 使用EID中的setCustomerID方法
* 在Adobe Experience Platform Launch中添加操作

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

散列之前，ECID库在CustomerID上执行数据标准化。此过程修剪两端的CustomerID的空白，并将所有字符转换为小写字母。例如，如果电子邮件地址：“ecid@adobe.com”变为“ecid@adobe.com”

请参见下面的代码示例，了解如何设置单个客户ID(上面提到的电子邮件地址)，SHA-256哈希。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

除了Experience Cloud访客ID之外，您还可以与每个访客关联额外的客户ID、身份验证状态和哈希类型(SHA-256)。如果不提供任何哈希类型，它将被视为不哈希。

`setCustomerIDs` 方法可以接受同一访客拥有多个客户 ID。这有助于您识别或定位跨不同设备的单独用户。例如，您可以将这些 ID 作为[客户属性](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)上传至 Experience Cloud，并在不同的解决方案中访问此数据。

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. 示例调用可能类似于下面的一个调用。添加换行符以清楚起见。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| 参数 | 描述 |
|------------|----------|
| `d_cid_ic` | 将集成代码、唯一用户ID(DPUUID)和身份验证状态ID传递给ID服务。Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>身份验证状态</b> <br> 这是d_ cid_ ic参数中的可选ID。Expressed as an integer, it identifies users according to their authentication status as shown below: <br> <ul><li>0(未知或从未验证过)</li><li>1(当前为此实例/页面/应用程序上下文进行身份验证)</li><li>2（已注销）</li></ul> <br>示例：<br> <ul><li>未知：...d_cid=123%01456%01<b>0</b></li><li>已通过身份验证：...d_cid=123%01456%01<b>1</b></li><li>已注销：...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch是Adobe新一代标签管理功能。Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

确认配置后，Launch将数据打包到对象中，如下所示：

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

下面是代码示例：

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.