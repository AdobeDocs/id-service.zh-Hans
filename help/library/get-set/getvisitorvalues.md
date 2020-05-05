---
description: 这是一个异步 API，在默认情况下可返回 Analytics 和 ID 服务中的标识符、选择禁用数据收集的用户标识符、以及地理位置和元数据“blob”内容中的标识符。此外，您还可以通过可选的 visitor.FIELDS 枚举来控制要返回哪些 ID。
keywords: ID Service
seo-description: 这是一个异步 API，在默认情况下可返回 Analytics 和 ID 服务中的标识符、选择禁用数据收集的用户标识符、以及地理位置和元数据“blob”内容中的标识符。此外，您还可以通过可选的 visitor.FIELDS 枚举来控制要返回哪些 ID。
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getVisitorValues{#getvisitorvalues}

这是一个异步 API，在默认情况下可返回 Analytics 和 ID 服务中的标识符、选择禁用数据收集的用户标识符、以及地理位置和元数据“blob”内容中的标识符。此外，您还可以通过可选的 visitor.FIELDS 枚举来控制要返回哪些 ID。

目录：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local">语法</a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> 用例 1：请求默认数据集 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> 用例 2：请求自定义数据集 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> 定义的响应参数 </a> </li> 
</ul>

## 语法{#section-5aebe3907b2b46e997f45a1d1ed35c09}

此函数使用以下语法（斜体表示变量的占位符）：` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

在此函数的参数中：

* ` *`callback`*` 表示您自己的用于接收所返回 ID 的回调代码。
* *（可选）*` visitor.FIELDS. *`ID type`*` 是一个枚举，用于指定您希望此函数返回的 [ID 值](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5)。

有关更多信息，请参阅以下用例和定义。

## 用例 1：请求默认数据集 {#section-36a31683558742a5915db3a391e09f7b}

此代码返回标准数据集。 您的请求和响应可能与以下示例类似。

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

在默认示例响应中，某些值已缩短以用于演示目的。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## 用例 2：请求自定义数据集 {#section-467b2f4e513344c89b7332b05f6f59f3}

此代码使用可选数组通过 `visitor.FIELDS` 枚举来返回一组特定的 ID。在这种情况下，我们只希望获得访客的Experience Cloud ID(MCID)和Analytics ID(MCAID)。 您的请求和响应可能与以下示例类似。

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

自定义示例响应只返回在请求中指定的ID。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## 定义的响应参数 {#section-4c4c300167694c6fbff1d6c612f372b5}

下表列出并定义了响应参数。这些参数也是 `visitor.FIELDS` 枚举中的所有值。请注意，如果某个特定变量没有值，则此方法将返回空字符串。

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 值 </th> 
   <th colname="col2" class="entry"> 描述 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>加密的 <span class="keyword">Audience Manager</span> 元数据，称为“blob”。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>数据收集区域ID。 这是特定ID服务数据中心的地理位置的数字标识符。 </p> <p>请参阅 <a href="https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external">DCS 区域 ID、位置和主机名</a>以及 <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local">getLocationHint</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>访客的 <span class="keyword">Analytics</span> ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>访客的Experience Cloud ID。 </p> <p>See <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookies and the Experience Cloud Identity Service </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>一个标志，指示访客是否已退出数据收集。 </p> <p>值包括： </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph">'isoptedout-true'</span>：访客已选择禁用数据收集。 </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph">'isoptedout-false'</span>：访客未选择禁用数据收集。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

