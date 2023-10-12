---
description: "Learn more about: Non-transactional Data Flows That Support Unbounded Recordsets"
title: "Non-transactional Data Flows That Support Unbounded Recordsets2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Non-transactional Data Flows That Support Unbounded Recordsets
This model supports one or more consecutive sends followed by one or more consecutive receives. Therefore, the last input parameter of the method invocation can be an unbounded recordset (that is, a recordset with no set number of rows).  
  
 The input parameters are converted and sent, and then each row of the recordset is converted and sent to the mainframe transaction program (TP). The mainframe TP executes, receives the input data and each row of the recordset, processes the data (perhaps doing database accesses and/or updates), and then sends its response back to TI. TI receives any output parameters from the TP and converts them to return to the invoker. Then each row of an unbounded recordset is received, if appropriate. The mainframe TP has no notion of a recordset; it is just receiving or sending tabular data. TI handles all conversion to and from the recordset.  
  
 The following server models support this data flow model:  
  
-   CICS LU6.2 User Data  
  
-   IMS LU6.2  
  
-   TCP Transaction Request Message (TRM) User Data  
  
## See Also  
 [Supported Data Flow Models](../core/supported-data-flow-models1.md)
