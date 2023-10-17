---
description: "Learn more about: Reassert"
title: "Reassert | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert function [Business Rules Engine]"
ms.assetid: 9cd640a2-bfeb-4c7a-b737-1c92cc122a9c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reassert
To *reassert* means to call the **Assert** function on an object that is already in the engine's working memory. A reassert command is equivalent to issuing a retract command for the object, followed by an assert command.  
  
## .NET Objects  
 The object is first retracted and any actions on the agenda for rules that use the object (in a predicate or action) are removed. The object is then asserted back into working memory and evaluated as any object that is newly asserted. This means that any rules that use the object in a predicate are re-evaluated and their actions are added to the agenda as appropriate. Any rules that previously evaluated to **true** and only use the object in their actions will have their actions re-added to the agenda.  
  
## TypedXmlDocument  
 When a top level **TypedXmlDocument** (**TXD**) is reasserted, the child **TXD**s that are created when the top level **TXD** is initially asserted have different behaviors depending on the state of the child **TXD**s. In the case of a new child node or a child node that is dirty, meaning that at least one of its fields has been changed in the policy by using a rule action, an assert, or reassert action is performed on the child node. Any existing child node that is not dirty remains in the working memory. The following example is a simplified scenario that describes the behaviors of the child nodes when their parent node is reasserted.  
  
 Assume there are three **TXD**s currently in the working memory: **P**, **C**1, **C**2, and **C**3. **P** is the top level **TXD**, the parent node; each child node contains a field **x**.  
  
 **P**  
  
 **C**1 (**C**1.**x** = 1)  
  
 **C**2 (**C**2.**x** = 1)  
  
 **C**3 (**C**3.**x** = 1)  
  
 Next, assume the following operations have been performed as a result of rule action:  
  
-   The field (**x**) value for **C**2 is updated.  
  
-   **C**3 is deleted by using user code.  
  
-   An additional child node, **D**, is added to **P** by using user code.  
  
> [!NOTE]
>  A node will not be marked dirty by the Business Rule Engine from operations, of which the engine is not aware. For example, adding, deleting, or modifying a node programmatically in an external application.  
  
 The new representation of the objects in working memory is as follows.  
  
 **P**  
  
 **C**1 (**C**1.**x** = 1)  
  
 **C**2 (**C**2.**x** = *0*)  
  
 **D**  
  
 Now, reassert **P**. The following points summarize the behaviors of the child nodes:  
  
-   Node **C**2 is reasserted, because it has become dirty after its field being updated.  
  
-   Node **C**3 is retracted from the working memory.  
  
-   Node **D** is asserted into the working memory.  
  
-   Node **C**1 remains unchanged in the working memory, because it was not updated before **P** was reasserted.  
  
## TypedDataTable  
 If **Reassert** is issued on a **TypedDataRow**, that row is retracted and then asserted into working memory. If **Reassert** is issued on the **TypedDataTable**, all associated **TypedDataRow**s are retracted and then asserted.  
  
## DataConnection  
 All **TypedDataRow**s retrieved through the **DataConnection** are retracted. All predicates that use the **DataConnection** are then re-evaluated, causing the **DataConnection** to be requeried to create the relevant **TypedDataRow**s.  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)
