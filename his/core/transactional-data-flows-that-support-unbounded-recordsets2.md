---
title: "Transactional Data Flows That Support Unbounded Recordsets2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2668085d-517a-4a65-8e30-450e023e33ca
caps.latest.revision: 3
---
# Transactional Data Flows That Support Unbounded Recordsets
This model supports one or more consecutive sends followed by one or more consecutive receives. Therefore, the last input parameter and/or the return value of the method invocation can be an unbounded recordset (that is, a recordset with no set number of rows).  
  
 The CICS Link programming model cannot be used, so this data flow model supports only these two server models:  
  
-   CICS LU6.2 User Data  
  
-   IMS LU6.2  
  
## See Also  
 [Supported Data Flow Models](../core/supported-data-flow-models2.md)