---
title: "How to Configure Transactional Properties on an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "atomic transactions"
  - "orchestrations, transactions"
  - "transactions, long-running"
  - "orchestrations, configuring"
  - "transactions, atomic"
ms.assetid: 8eec6019-4d96-4ed6-8a90-9403738d8af4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Transactional Properties on an Orchestration
An orchestration can be treated as an atomic transaction, a long-running transaction, or neither.  
  
### To make your orchestration an atomic transaction  
  
1.  In the Orchestration View window, select **Orchestration Properties**.  
  
2.  In the Properties window, select **Atomic** in the drop-down for the **Transaction Type** property.  
  
     **Batch**, **Compensation**, **Isolation Level**, **Retry**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window, just as they do for any scope. For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).  
  
### To make your orchestration a long-running transaction  
  
1.  In the Orchestration View window, select **Orchestration Properties**.  
  
2.  In the Properties window, select **Long Running** in the drop-down for the **Transaction Type** property.  
  
     **Compensation**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window. For more information on these properties, just as they do for any scope. For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).  
  
## See Also  
 [Making Orchestrations Transactional](../core/making-orchestrations-transactional.md)