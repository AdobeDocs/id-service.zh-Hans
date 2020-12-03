---
description: 通过此配置，当使用appendSupplementalDataIDTo帮助函数将该ID从一页传递到另一页时，可覆盖默认的补充数据ID(SDID)过期间隔。 默认情况下，接收页面上的ID服务代码有30秒钟从引用页面发送的URL获取SDID。 如果接收页上的ID服务代码在30秒内无法检索SDID，则它会请求新的SDID。 此功能主要针对需要将SDID从一个页面传递到另一个页面并希望控制此超时时间间隔的A4T客户。
keywords: ID Service
seo-description: 通过此配置，当使用appendSupplementalDataIDTo帮助函数将该ID从一页传递到另一页时，可覆盖默认的补充数据ID(SDID)过期间隔。 默认情况下，接收页面上的ID服务代码有30秒钟从引用页面发送的URL获取SDID。 如果接收页上的ID服务代码在30秒内无法检索SDID，则它会请求新的SDID。 此功能主要针对需要将SDID从一个页面传递到另一个页面并希望控制此超时时间间隔的A4T客户。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 7%

---


# sdidParamExpiry{#sdidparamexpiry}

通过此配置，当使用appendSupplementalDataIDTo帮助函数将该ID从一页传递到另一页时，可覆盖默认的补充数据ID(SDID)过期间隔。 默认情况下，接收页面上的ID服务代码有30秒钟从引用页面发送的URL获取SDID。 如果接收页上的ID服务代码在30秒内无法检索SDID，则它会请求新的SDID。 此功能主要针对需要将SDID从一个页面传递到另一个页面并希望控制此超时时间间隔的A4T客户。

**覆盖SDID超时**

如果您需要更改默认的 SDID 超时，请使用以下语法将 `sdidParamExpiry` 添加到 `Visitor.getInstance` 函数：

**语法：**` sdidParamExpiry: *` 时间（以秒为单位）`*`

**代码示例**

配置后，您的ID服务代码可能与此示例类似。 此示例将SDID超时设置为15秒。 此配置与appendSupplementalDataIDTo [帮助程序方](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 法配合使用。

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

