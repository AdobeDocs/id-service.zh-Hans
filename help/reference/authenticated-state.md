---
description: 除了 Experience Cloud 访客 ID 之外，您还可以将其他的客户 ID 和身份验证状态与每位访客关联。
keywords: ID 服务
seo-description: 除了 Experience Cloud 访客 ID 之外，您还可以将其他的客户 ID 和身份验证状态与每位访客关联。
seo-title: 客户 ID 和身份验证状态
title: 客户 ID 和身份验证状态
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: tm+mt
source-git-commit: ee07ec0fd83932ab5006dcdbece61608f4e4606e

---


# 客户 ID 和身份验证状态 {#customer-ids-and-authentication-states}

除了 Experience Cloud 访客 ID 之外，您还可以将其他的客户 ID 和身份验证状态与每位访客关联。

## 身份验证状态 {#section-68ad4065dfaa437d9070832d6e2bf85c}

`setCustomerIDs` 方法可以接受同一访客拥有多个客户 ID。这有助于您识别或定位跨不同设备的单独用户。例如，您可以将这些 ID 作为[客户属性](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)上传至 [!DNL Experience Cloud]，并在不同的解决方案中访问此数据。

>[!IMPORTANT]
>
>客户属性和核心服务功能要求使用 `setCustomerIDs`（客户 ID 同步）。同步客户 ID 是一种适用于 [!DNL Analytics] 的可选识别方法。[!DNL Target] 需要使用 `Visitor.AuthState.AUTHENTICATED` 才能使客户属性正常工作。请参阅[核心服务 - 如何启用您的解决方案](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)，以了解相关示例。

从 Experience Cloud Identity 服务版本 1.5 开始，`setCustomerIDs` 包含可选的 `AuthState` 对象。`AuthState` 可根据访客的身份验证状态（例如，已登录，已注销）来识别他们。您可通过表中列出的状态值来设置身份验证状态。身份验证状态将以整数的形式返回。

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 身份验证状态 </th> 
   <th colname="col2" class="entry"> 状态整数 </th> 
   <th colname="col3" class="entry"> 用户状态 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>未知或从未验证。 </p> <p> 未对访客 ID 使用 <span class="codeph">AuthState</span>，或未在每个页面或应用程序上下文中显式设置此属性时，默认应用未知状态。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>已经过特定实例、页面或应用程序的验证。 </p> <p> <p>注意：要正常使用，<span class="keyword">Target</span> 的用户属性需要此状态。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>已注销。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 身份验证状态的用例 {#section-fe9560cc490943b29dac2c4fb6efd72c}

您可以根据用户对您的 Web 属性执行的操作以及是否进行身份验证来为他们分配身份验证状态。请参阅下表中的一些示例：

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 身份验证状态 </th> 
   <th colname="col2" class="entry"> 用例 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>此状态可用于以下情况： </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">阅读电子邮件（此操作可能意味着读者是预期的收件人，但也可能表示电子邮件已被转发）。 </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">从电子邮件点进到登录页面。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>用户目前通过了您网站或应用程序上活动会话的身份验证。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>用户已经过身份验证，但已主动注销。用户想要并打算与已经过身份验证状态断开连接。用户不想再被当为已经过身份验证处理。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 设置客户 ID 和身份验证状态 {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

客户 ID 可包含 ID 和身份验证状态的组合，如以下示例中所示。

>[!IMPORTANT]
>
>* ID 区分大小写。
>* 仅对您的ID使用未编码的值。
>* 客户 ID 和身份验证状态未存储在访客 ID Cookie 中。必须针对每个页面或应用程序上下文设置它们。
>* 您不应当在客户 ID 中包含任何个人身份信息 (PII)。如果您要使用 PII 来识别访客（例如电子邮件地址），我们建议您存储信息的哈希版本或加密版本。ECID 库支持对用户标识符进行哈希处理。请参阅[对 setCustomerIDs 的 SHA256 哈希处理支持](/help/reference/hashing-support.md)。
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## 返回客户 ID 和身份验证状态 {#section-71a610546188478fa9a3185a01d6e83b}

使用 `getCustomerIDs` 可返回客户 ID 和相关的身份验证状态。此方法可按照整数的形式返回访客的身份验证状态。

**语法**

`getCustomerIDs` 通过以下语法返回数据。

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**示例**

返回的客户 ID 和身份验证状态数据看起来应该类似于以下示例。

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK 支持 {#section-861c6b3b1ba645dda133dccb22ec7bb0}

[!DNL Experience Cloud] ID 服务支持在我们的 Android 和 iOS SDK 代码中使用客户 ID 和身份验证状态。请参阅以下代码库：

* [Android SDK 方法](https://docs.adobe.com/content/help/en/mobile-services/android/overview.html)
* [iOS SDK 方法](https://docs.adobe.com/content/help/en/mobile-services/ios/overview.html)

## 面向 Analytics 和 Audience Manager 客户的注意事项 {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

如果您将声明的 ID 传递至 [!DNL Audience Manager]，则 `userid` 对象需要匹配与数据源关联的集成代码。更多信息，请参阅[配置合并规则代码](https://docs.adobe.com/help/en/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html#configure-merge-rule-code)文档中的[!UICONTROL 访客 ID 服务]部分。
