---
description: "Learn more about: Non-transactional Data Flows That Support Bounded Recordsets"
title: "Non-transactional Data Flows That Support Bounded Recordsets2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
  
-   IBM i Distributed Program Calls  
  
## See Also  
 [Supported Data Flow Models](../core/supported-data-flow-models1.md)
