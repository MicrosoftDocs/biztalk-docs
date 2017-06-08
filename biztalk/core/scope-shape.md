---
title: "Scope Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.scope"
ms.assetid: ff3a3a49-526b-4e54-8071-ba82c801a281
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scope Shape
The **Scope** shape provides a contextual framework for its contents. The first block of a Scope shape is the context block, or body, in which the basic actions of the scope take place; it is analogous to the try block in a try/catch statement. Following the body, the Scope shape may also include one or more exception-handler blocks and a compensation block.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Batch** property|This property is not used in BizTalk Server and it will be deprecated in the future release.|  
|**Compensation** property|From the drop-down list, select **Default** or **Custom** to specify what type of compensation to perform on the scope.|  
|**Isolation Level** property|From the drop-down list, select the degree to which data is accessible among concurrent transactions:<br /><br /> -   Read Committed—Prevent the selected transaction from accessing data modifications in concurrent transactions until they are committed. This option is the Microsoft SQL Server default setting.<br />-   Repeatable Read—Require read locks until the selected transaction is complete.<br />-   Serializable—Prevent concurrent transactions from making data modifications until the selected transaction is complete. This option is the most restrictive isolation level.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
|**Retry** property|From the drop-down list, select **True** or **False** to specify whether to retry the transaction if it fails.|  
|**Synchronized** property|From the drop-down list, select **True** or **False** to specify whether the scope is synchronized, which guarantees that shared data accessed within the scope will not be written to by a parallel action until the current scope has completed.|  
|**Timeout** property|Enter an expression to specify the time in seconds until the transaction fails due to inactivity. If you do not want to use a time-out, set the value of this property to 0.|  
|**Transaction Identifier** property|If this scope is transactional, specify an identifier for the transaction.|  
|**Transaction Type** property|Specify whether this scope is an atomic transaction, a long-running transaction, or not a transaction. Different properties are available to you depending on the type.|  
  
## See Also  
 [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md)