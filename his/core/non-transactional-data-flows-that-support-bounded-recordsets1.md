---
title: "Non-transactional Data Flows That Support Bounded Recordsets1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fda15fec-0a31-499e-bff1-cfcb7fce2eed
caps.latest.revision: 4
---
# Non-transactional Data Flows That Support Bounded Recordsets
For each method invocation, TI converts and sends the input parameters to the transaction program (TP). The mainframe TP executes, processes the input data (for instance, accessing or updating the database), and sends its response back to TI. Then TI receives the output parameters from the TP and converts them to return to the invoker.  
  
 This data flow model does not support unbounded recordsets. (An unbounded recordset has no set number of rows.)  
  
 The following server models support this data flow model:  
  
-   CICS LU6.2 Link  
  
-   CICS LU6.2 User Data  
  
-   IMS LU6.2  
  
-   TCP Transaction Request Message (TRM) Link  
  
-   TCP Transaction Request Message (TRM) User Data  
  
-   IMS Connect  
  
-   OS/400 Distributed Program Calls  
  
## See Also  
 [Supported Data Flow Models](../core/supported-data-flow-models2.md)