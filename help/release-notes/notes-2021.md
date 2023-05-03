---
description: 关于 Experience Cloud 身份服务的功能发布、更新或更改。
keywords: ID 服务
title: 2021 版发行说明
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: ht
source-wordcount: '103'
ht-degree: 100%

---

# Experience Cloud 身份服务发行说明 - 2021

关于 Experience Cloud 身份服务的功能发布、更新或更改。

## Visitor 5.3.0

Visitor 5.3.0 版本中包含以下更新：

* 更新了算法以生成本地 ECID。
* 最新的选择加入中具有隐私 Cookie 的 `Secure` 和 `SameSite` 标志。
* 为 Firefox 浏览器在子 iFrame 中加载页面发生的问题提供了修补程序。

## Visitor 5.2.0

Visitor 5.2.0 版本中包含以下更新：

* 此版本引入 `onRecieveEcid` 事件，当从身份服务收到 ECID 时调用该事件。例如：

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
