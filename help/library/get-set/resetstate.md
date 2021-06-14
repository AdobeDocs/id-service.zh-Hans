---
description: 此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。
keywords: ID 服务
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '374'
ht-degree: 100%

---

# resetState{#resetstate}

此函数主要用于 A4T 客户，旨在帮助解决与在单页站点/屏幕或应用程序上使用 ID 相关的问题。

## 用例 {#section-840b88a5cdb042488b340cad5d7b22a5}

作为使用 ID 服务的 A4T 客户，当您需要执行以下操作时，您可能要使用 `visitor.resetState()` 函数：

* 通过重定向将 Supplemental Data ID (SDID) 或任何其他 ID 从一个页面/屏幕传递到另一个页面/屏幕。通常，若不使用此函数，ID 服务便不会传递该 ID。
* 使用仅通过 Ajax 调用更新页面或应用程序的特定部分的代码，并且您想跟踪这些操作。例如，假设您有一个页面，当您在其中单击某个对象时，系统仅会加载或更改特殊部分。在这种情况下，除非重新加载该页面，否则 ID 服务无法请求不同的 ID。但是，通过 `visitor.resetState()`，您便可以在这种情况下请求新的 ID。

请参阅下面的代码示例。

## 语法{#section-9e63503e178f4be28ac850abf44d6d91}

**语法：**` visitor.resetState( *`状态`*);`

## 代码示例 {#section-d75b211bb4ea473887eb284de2ad838b}

您的 ID 服务实施会影响您使用此函数的方式。请参阅下表了解相关示例。

**服务器端实施**

服务器端实施适用于具有 [!DNL Target]、[!DNL Analytics] 和 ID 服务混合服务器端和客户端实施的 A4T 客户。如果您已通过此方法设置 ID 服务，则您只需将 `visitor.resetState()` 添加到页面中。对 ID 服务的调用将会自动返回新的 ID 和服务器状态。

**非标准实施**（包含 ID）

如果您已通过[非标准实施](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)设置 ID 服务，则需要配置一个变量对象，以包含您要通过 `visitor.resetState()` 传递的 SDID（或其他 ID）。如下所示，这将包含您的[组织 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) 以及您要传递的 ID。您的代码可能与以下示例类似。

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

**非标准实施**（不传递 ID）

在这种情况下，`visitor.resetState()` 可用于生成新的 ID。在以下情况下，这可能会很有用：用户在单页应用程序中转到一个新屏幕而不刷新页面，并且您需要一个新 ID。

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

**动态标记管理器 (DTM)**

当前，`visitor.resetState()` 没有 DTM 配置路径。
