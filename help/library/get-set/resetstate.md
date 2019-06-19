---
description: 此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。
keywords: ID 服务
seo-description: 此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。
seo-title: resetState
title: resetState
uuid: ed7be76d7ee-4e51-b26 c-456ff85 fd096
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetState{#resetstate}

此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。

## 用例 {#section-840b88a5cdb042488b340cad5d7b22a5}

作为使用ID服务的A4T客户，您可能需要在需要时使用该 `visitor.resetState()` 函数：

* 通过重定向将补充数据 ID (SDID) 或任何其他 ID 从一个页面或屏幕传递到另一个页面或屏幕。通常情况下，如果没有此函数，ID 服务将不会传递此 ID。
* 使用可通过 Ajax 调用仅更新页面或应用程序特定部分的代码，并且您想要跟踪这些操作。例如，假设您有一个页面，单击其中的某个对象只会加载或更改特定部分。在这种情况下，ID 服务无法请求其他 ID，除非重新加载页面。但是，您 `visitor.resetState()`可以在这些条件下请求新ID。

请参阅下面的代码示例。

## 语法 {#section-9e63503e178f4be28ac850abf44d6d91}

**语法：**` visitor.resetState( *`state`*);`

## 代码范例 {#section-d75b211bb4ea473887eb284de2ad838b}

您的 ID 服务实施会影响您使用此函数的方式。有关示例，请参阅下表。

**服务器端实施**

服务器端实施是为A4T客户提供的混合服务器和客户端实现 [!DNL Target]以及 [!DNL Analytics]ID服务。如果使用此方法设置ID服务，您只需添加 `visitor.resetState()` 到页面中。对 ID 服务的调用将会自动返回新的 ID 和服务器状态。

**非标准实施(** 带有ID)

如果您已通过[非标准实施](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)设置 ID 服务，则您需要配置一个变量对象，以包含您要通过 `visitor.resetState()` () 传递的 SDID（或其他 ID）。如下所示，这将包含您的[组织 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) 以及您要传递的 ID。您的代码可能与以下示例类似。

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**非标准实施** (不传递ID)

在这种情况下， `visitor.resetState()` 可用于生成新ID。在单页应用程序中，如果当用户在未刷新页面的情况下导航到新屏幕时，您需要一个新的 ID，这可能会很有用。

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**动态标签管理器 (DTM)**

当前，`visitor.resetState()` () 没有 DTM 配置路径。