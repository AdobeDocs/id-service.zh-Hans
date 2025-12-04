---
description: 关于 Experience Cloud 身份标识服务的功能发布、更新或更改。
keywords: ID 服务
title: 2021 版发行说明
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Experience Cloud 身份标识服务发行说明 - 2021

关于 Experience Cloud 身份标识服务的功能发布、更新或更改。

## Visitor 5.3.0

Visitor 5.3.0 版本中包含以下更新：

* 更新了算法以生成本地 ECID。
* 最新的选择加入中具有隐私 Cookie 的 `Secure` 和 `SameSite` 标志。
* 为 Firefox 浏览器在子 iFrame 中加载页面发生的问题提供了修补程序。

## Visitor 5.2.0

Visitor 5.2.0 版本中包含以下更新：

* 此版本引入 `onReceiveEcid` 事件，当从身份标识服务收到 ECID 时调用该事件。例如：

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

