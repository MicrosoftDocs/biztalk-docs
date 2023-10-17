---
description: "Learn more about: Non-transactional Data Flows That Support Bounded Recordsets"
title: "Non-transactional Data Flows That Support Bounded Recordsets2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c3ea011-7fe0-41f2-9e5e-bd9ac11e2a10
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
 [Supported Data Flow Models](../core/supported-data-flow-models1.md)
