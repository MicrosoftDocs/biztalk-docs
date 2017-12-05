---
title: "Non-transactional Data Flows That Support Unbounded Recordsets1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 872bc1bc-eb4a-4d79-8365-bea4a7055419
caps.latest.revision: 4
---
# Non-transactional Data Flows That Support Unbounded Recordsets
This model supports one or more consecutive sends followed by one or more consecutive receives. Therefore, the last input parameter of the method invocation can be an unbounded recordset (that is, a recordset with no set number of rows).  
  
 The input parameters are converted and sent, and then each row of the recordset is converted and sent to the mainframe transaction program (TP). The mainframe TP executes, receives the input data and each row of the recordset, processes the data (perhaps doing database accesses and/or updates), and then sends its response back to TI. TI receives any output parameters from the TP and converts them to return to the invoker. Then each row of an unbounded recordset is received, if appropriate. The mainframe TP has no notion of a recordset; it is just receiving or sending tabular data. TI handles all conversion to and from the recordset.  
  
 The following server models support this data flow model:  
  
-   CICS LU6.2 User Data  
  
-   IMS LU6.2  
  
-   TCP Transaction Request Message (TRM) User Data  
  
## See Also  
 [Supported Data Flow Models](../HIS2010/supported-data-flow-models2.md)