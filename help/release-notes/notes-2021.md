---
description: 关于 Experience Cloud Identity 服务的功能发布、更新或更改。
keywords: ID 服务
title: 2021版发行说明
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 25%

---

# Experience CloudIdentity Service发行说明 — 2021版

关于 Experience Cloud Identity 服务的功能发布、更新或更改。

## 访客5.3.0

访客5.3.0版本中包含以下更新：

* 更新了生成本地ECID的算法。
* 最新选择加入功能 `Secure` 和 `SameSite` 隐私Cookie的标记。
* 修复了在子iFrame中加载页面时Firefox浏览器问题的修补程序。

## 访客5.2.0

访客5.2.0版本中包含以下更新：

* 此版本引入了事件 `onRecieveEcid`，在从Identity服务接收ECID时调用。 例如：

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
