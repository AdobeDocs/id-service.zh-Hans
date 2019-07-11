---
description: 通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将补充数据 ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码将有 30 秒的时间从反向链接页面发送的 URL 中获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒内检索 SDID，它会请求一个新的 SDID。此功能主要适用于需要在页面间传递 SDID 并希望控制此超时间隔的 A4T 客户。
keywords: ID 服务
seo-description: 通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将补充数据 ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码将有 30 秒的时间从反向链接页面发送的 URL 中获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒内检索 SDID，它会请求一个新的 SDID。此功能主要适用于需要在页面间传递 SDID 并希望控制此超时间隔的 A4T 客户。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# sdidParamExpiry{#sdidparamexpiry}

通过此配置，您可以在使用 appendSupplementalDataIDTo 帮助程序函数将补充数据 ID (SDID) 从一个页面传递到另一个页面时，覆盖此 ID 的默认过期时间间隔。默认情况下，接收页面上的 ID 服务代码将有 30 秒的时间从反向链接页面发送的 URL 中获取 SDID。如果接收页面上的 ID 服务代码无法在 30 秒内检索 SDID，它会请求一个新的 SDID。此功能主要适用于需要在页面间传递 SDID 并希望控制此超时间隔的 A4T 客户。

**覆盖 SDID 超时**

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

配置完成后，您的 ID 服务代码可能与以下示例类似。此示例将 SDID 超时设置为 15 秒。此配置需与[appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 帮助程序方法结合使用。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

